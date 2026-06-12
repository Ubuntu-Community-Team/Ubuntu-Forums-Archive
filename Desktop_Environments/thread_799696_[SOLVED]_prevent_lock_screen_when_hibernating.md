---
title: "[SOLVED] prevent lock screen when hibernating"
date: 2008-05-19
forum: Desktop Environments
---

### Post by dresnu on 2008-05-19
Hello, I'm using uswsusp to hibernate my laptop running Kubuntu, but when it resumes the session is locked. 

Is there a way to resume directly to the desktop instead of having to input my password everytime? 

Thank you

---

### Post by phidia on 2008-05-19
You need to open up the screensaver settings and unselect (uncheck) the lock desktop option.
In KDE I think you'll find the screensaver settings in control center.

---

### Post by dresnu on 2008-05-19
Unfortunately it's not that. Screensaver is disabled already and all options are unchecked.
The problem lies somewhere in KDE guidance and the HAL scripts it invokes during hibernation.

If I hibernate from a terminal with the s2disk command I can resume regularly on my desktop. On the other hand if I hibernate through the Log out options in Kmenu I get a locked screen when resuming.

---

### Post by sdennie on 2008-05-19
I'm not sure how to do it within KDE but, one thing you could try would be to edit /etc/default/acpi-support.  Look for LOCK_SCREEN and change the value to false.  I'm not sure if that will work in Hardy anymore though.

---

### Post by dresnu on 2008-05-19
> **vor said:**
> one thing you could try would be to edit /etc/default/acpi-support.  Look for LOCK_SCREEN and change the value to false.

I'm still on Gutsy but what you suggested didn't work anyway. Indeed LOCK_SCREEN was true in acpi configuration but switching it didn't make any change.

From what I found out when I press the button to hibernate what gets called is this script /usr/lib/hal/scripts/hal-system-power-hibernate:```
#!/bin/sh

PRIVILEGE=hal-power-hibernate
if [ "$HAVE_POLKIT" = "1" ] ; then
    if [ "$HAL_METHOD_INVOKED_BY_UID" != "0" ] ; then
        RESULT=$(polkit-is-privileged --privilege $PRIVILEGE \
            --user $HAL_METHOD_INVOKED_BY_UID \
            --system-bus-unique-name $HAL_METHOD_INVOKED_BY_SYSTEMBUS_CONNECTION_NAME 2>&1)
        IS_PRIVILEGED=$?
        if [ "$IS_PRIVILEGED" != "0" ] ; then
            echo org.freedesktop.Hal.Device.PermissionDeniedByPolicy >&2
            echo $PRIVILEGE refused uid $HAL_METHOD_INVOKED_BY_UID >&2
            exit 1
        fi
    fi
fi

if [ -n "$HALD_UNAME_S" -a -x ./$HALD_UNAME_S/hal-system-power-hibernate-$HALD_UNAME_S ]; then
    exec ./$HALD_UNAME_S/hal-system-power-hibernate-$HALD_UNAME_S $@
else
    echo "org.freedesktop.Hal.Device.UnknownError" >&2
    echo "No back-end for your operating system" >&2
    exit 1
fi

```

that then calls this one /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux:```
#!/bin/sh

POWERSAVED_SUSPEND2DISK="dbus-send --system --dest=com.novell.powersave \
                         --print-reply /com/novell/powersave \
                         com.novell.powersave.action.SuspendToDisk"

unsupported() {
        echo org.freedesktop.Hal.Device.SystemPowerManagement.NotSupported >&2
        echo No hibernate script found >&2
        exit 1
}

# Make a suitable command line argument so that the tools can do the correct
# quirks for video resume.
# Passing the quirks to the tool allows the tool to not depend on HAL for data.
QUIRKS=""
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-bios"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-mode"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-suspend"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-on"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbestate-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbemode-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3" = "true" ] && QUIRKS="$QUIRKS --quirk-vga-mode3"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST" = "true" ] && QUIRKS="$QUIRKS --quirk-vbe-post"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RADEON_OFF" = "true" ] && QUIRKS="$QUIRKS --quirk-radeon-off"

#ALTLinux only supports powersave
if [ -f /etc/altlinux-release ] ; then
        if [ -x /usr/bin/powersave ] ; then
                $POWERSAVED_SUSPEND2DISK
                RET=$?
        else
                unsupported
        fi

#Mandriva support suspend-scripts
elif [ -f /etc/mandriva-release ] ; then
    if [ -x /usr/sbin/pmsuspend ] ; then
        /usr/sbin/pmsuspend disk
        RET=$?
    else
        unsupported
    fi

#RedHat/Fedora and SUSE support support pm-utils
elif [ -f /etc/redhat-release ] || [ -f /etc/fedora-release ] \
                 || [ -f "/etc/SuSE-release" ] ; then
        if [ -x /usr/sbin/pm-hibernate ] ; then
                /usr/sbin/pm-hibernate $QUIRKS
                RET=$?
        else
                unsupported
        fi

#Other distros just need to have *any* tools installed
else
        if [ -x "/sbin/s2disk" ] ; then
                /sbin/s2disk $QUIRKS
                RET=$?
        #elif [ -x "/usr/bin/powersave" ] ; then
        #        $POWERSAVED_SUSPEND2DISK
        #       RET=$?
        #elif [ -x "/etc/acpi/hibernate.sh" ] ; then
        #       # acpi-support installed
        #       /etc/acpi/hibernate.sh force
        #       RET=$?
        #elif [ -x "/usr/sbin/pm-hibernate" ] ; then
        #       # uswsusp tools installed
        #       /usr/sbin/pm-hibernate
        #       RET=$?
        #elif [ -x "/usr/sbin/pmi" ] ; then
        #       /usr/sbin/pmi action hibernate force
        #       RET=$?
        #elif [ -x "/usr/sbin/hibernate" ] ; then
        #       # Suspend2 tools installed
        #       /usr/sbin/hibernate --force
        #       RET=$?
        #elif [ -w "/sys/power/state" ] ; then
        #       # Use the raw kernel sysfs interface
        #       echo "disk" > /sys/power/state
        #       RET=$?
        else
                unsupported
        fi
fi

#Refresh devices as a resume can do funny things
for type in button battery ac_adapter
do
        devices=`hal-find-by-capability --capability $type`
        for device in $devices
        do
                dbus-send --system --print-reply --dest=org.freedesktop.Hal \
                          $device org.freedesktop.Hal.Device.Rescan
        done
done

exit $RET

```

But in this code there doesn't seem to be any reference to screen/session locking.

---

### Post by dresnu on 2008-05-20
Ok, solved it.
I found there is an option in Power Manager that says "Lock screen on resume". Disabling it did the trick... easier than I thought.

Thanks for the replies

---


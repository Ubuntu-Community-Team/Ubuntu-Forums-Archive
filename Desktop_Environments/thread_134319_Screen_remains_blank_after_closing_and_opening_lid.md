---
title: "Screen remains blank after closing and opening lid"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jchau on 2006-02-21
My screen remains blank after close the lid and reopen it.  The display only failed to turn back on occasionally in the past.  However, after I disabled the GDM service, everytime I close the lid (in the command prompt & often in X), and open the lid again, the display would not turn back on.  (BTW, i'm using a laptop; Dell Latitude D410).  I know that the system did not freeze/crash because I can Ctrl+Alt+F2, login, and run "sudo shutdown -r now"; the system would restart normally after I type in my passwd for sudo (but the screen remains blank until the system restarts).  I checked my acpi scripts and they have not changed since I installed Ubuntu & like I said, the screen worked well before I unselected GDM from services.  

In an attempt to debug, I ran:
```
sleep 30 && xset dpms force on
``` in one xterm, and 
```
xset dpms force off
``` in another xterm.

The display would turn off, but would not turn back on after 30 seconds. (but when I wiggle my mouse, the display returns). Does this mean that there is a bug with the "xset dpms force on" command? 

Can someone help me fix this problem? Maybe some modifications to /etc/acpi/lid.sh to wakeup the screen?


Thanks everyone!
-Jimmy

In case you are curious why I disabled GDM, I did so for security.  I set up an account for my friends to sftp files to and from me.  I was able to successfully restrict that account to sftp only using rssh except for the fact that GDM bypassed all of rssh's security (chrooted access & sftp only) & GDM did not have the option of restricting that account from logging in (when the user logs in using GDM, they can access the real root directory & run commands).  Since we live in dorms in the same university, they can easily access my laptop, which I leave on on my desk.  To fix that, I disabled GDM from System->Administration->Services.  Now, everyone has to login to their shells before they can startx. I get bash & my friend's account gets rssh (which tells them that they are only allowed to run sftp & exits; hence, security problem solved).  If someone can tell me how to do the same thing another way without causing the dead screen problem, I'd appreciate it too.

---

### Post by jchau on 2006-02-21
BTW, here are all the files that I think are relevant:

/etc/acpi/events/lidbtn
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

/etc/acpi/lid.sh
```
#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            . /usr/share/acpi-support/screenblank
        fi
    done
else
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            grep -q off-line /proc/acpi/ac_adapter/*/state
            if [ $? = 1 ]
                then
                su $user -c "xscreensaver-command -unthrottle"

            fi
            if [ x$RADEON_LIGHT = xtrue ]; then
                [ -x /usr/sbin/radeontool ] && radeontool light on
            fi
            su $user -c "xscreensaver-command -deactivate"
            su $user -c "xset dpms force on"
        fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```


/usr/share/acpi-support/power-funcs
```
# a micro library of helper functions for the power scripts

PATH="$PATH:/usr/bin/X11"
POWERSTATE="/var/lib/acpi-support/powerstate"

getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}

getXconsole() {
        console=`fgconsole`;
        displaynum=`ps ax | grep -e 'X .* vt'$console | grep -v grep | sed -re 's!.*/X .*:([0-9]+).*!\1!'`
        if [ x"$displaynum" != x"" ]; then
                export DISPLAY=":$displaynum"
                getXuser
        fi
}

getState() {
        /usr/bin/on_ac_power;
        if [ "$?" -eq 0 ]; then
                STATE="AC";
        elif [ "$?" -eq 1 ]; then
                STATE="BATTERY";
        fi
}

#check our state has actually changed
checkStateChanged() {
# do we have our state stashed?
        if [ -f "$POWERSTATE" ]; then
                OLDSTATE=$(<$POWERSTATE)
                if [ "$STATE" = "$OLDSTATE" ]; then
                       exit 0
                else
#stash the new state
                        echo "$STATE" > $POWERSTATE
                fi
        else
#we need to stash the new state
                echo "$STATE" > $POWERSTATE
        fi
}

LAPTOP_MODE='/usr/sbin/laptop-mode'
HDPARM='/sbin/hdparm -q'

LIDSTATE='/var/lib/acpi-support/lidstate'
```

/etc/default/acpi-support
```

# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
```


/usr/share/acpi-support/screenblank
```
su $user -c "(xscreensaver-command -throttle; xscreensaver-command -lock)"
xset dpms force off
if [ x$RADEON_LIGHT = xtrue ]; then
    [ -x /usr/sbin/radeontool ] && radeontool light off
fi
```

I hope I didn't miss anything. Please help!:confused:

---

### Post by jchau on 2006-02-21
Umm... Thanks for all the help guys:-k ? I fixed it. Credits to the following:
[https://lists.ubuntu.com/archives/ubuntu-users/2005-January/018208.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-January/018208.html)
[https://lists.ubuntu.com/archives/ubuntu-users/2005-January/018235.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-January/018235.html)

Wow that was tough.  I scanned almost a hundred pages to find the solution.  

Here is my new lid.sh:
```
#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        sudo /usr/sbin/vbetool dpms off
else
        sudo /usr/sbin/vbetool dpms on
fi
```

This shuts off my screen when the lid closes & turns it back on when the lid opens (almost instantly w/o any virtual terminal (vt) switching dances ;) )

In addition, it does not depend on xset (which requires X running & requires the current vt to be X).  It works with X and without X.  It doesn't lock X automatically, but I can do that manually before I close the lid.

This simplifies the code too.  I wonder why this code isn't the default lid.sh.  The default lid.sh assumes too much (that I'm running X).  

\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by jchau on 2006-02-24
I revised the code.  It does not need to run with sudo.  It is already running under root. 

```
#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        /usr/sbin/vbetool dpms off
else
        /usr/sbin/vbetool dpms on
fi
```

---

### Post by ninocass on 2006-04-05
you sir are a legend!!!!!!!!

i was this close *holds up fingers* to doing a full format!!!!!!!

one this on is there a way to enable the screen saver when the lid is opened, i like the laptop to be locked if im away from it

cheers again :D

Nino

---

### Post by jchau on 2006-04-05
Thanks for the compliment! :KS Happy to inadvertently help!

---

### Post by jchau on 2006-04-05
If you're asking if there is a way to enable the screensaver while the lid is open, you can go to System->Lock Screen in in Gnome. Or you can set your screen saver to do so automatically after some time in System->Preference->Screen Saver.

---

### Post by ninocass on 2006-04-05
[QUOTE=jchau]If you're asking if there is a way to enable the screensaver while the lid is open, you can go to System->Lock Screen in in Gnome. Or you can set your screen saver to do so automatically after some time in System->Preference->Screen Saver.[/QUOTE]

no no  i was after a way to get it to lock when the screen was closed and then opened managed to get it working with:

```

#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
	**su $user -c "(xscreensaver-command -activate; xscreensaver-command -lock)"**
        sudo /usr/sbin/vbetool dpms off
else
        sudo /usr/sbin/vbetool dpms on
fi

```

your right about your code being a lot simplier than the defualt one :)

---

### Post by Gomek on 2006-08-12
tag for future reference

---


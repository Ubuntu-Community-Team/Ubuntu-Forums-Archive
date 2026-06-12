---
title: "Insprion 1420 unable to resume from standby"
date: 2008-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jimmer72 on 2008-11-23
Here is what I'm running:

Ubuntu Hardy 8.04 (x86) dual boot with Vista (32 bit) partition
Kernel Drivers: 2.6.24-21-generic
Gnome desktop interface

The problem:

When I try to resume from standby, the disk, fan, and display function normally, while the keyboard and touchpad are non-responsive. This prevents me from returning to the desktop and forces me to hard reboot (hold down power button). The strange thing is that this only happens about 50% of the time.

I have tried the following:

1. Running /etc/acpi/sleep.sh before suspending
2. Editing /etc/default/acpi-support
   changed the following:
       ACPI_SLEEP_MODE=mem
   to
       ACPI_SLEEP_MODE=standby
3. Standby with and without a/c power connected

I cannot deduce any pattern from my experiments and obviously my attempts at fixing the problem have not worked.  My closest guess is that it has to do with one of the various config scripts in /etc/acpi/standby.d/ which most likely run whenever standby is called.  I have looked around in the scripts, but since I am no linux expert, I have to do a lot of googling just to figure out what some of the commands are that are being called. If there is anyone that has a suggestion, I would be more than greatful for the help.

Thanks

Jim

---

### Post by Denny Johnson on 2008-11-23
[http://ubuntuforums.org/showthread.php?t=437596&highlight=keyboard+suspend](http://ubuntuforums.org/showthread.php?t=437596&highlight=keyboard+suspend)
This worked for my 1420n / 8.04

---

### Post by jimmer72 on 2008-11-23
Thanks for the reply.  This thread was full of people having my same problem. I edited /etc/default/acpi-support in the following manner:

Change the line:
   MODULES_WHITELIST=""
to
   MODULES_WHITELIST="hid usbhid"

FYI for anyone having this same problem hid and usbhid are the modules for the touchpad and keyboard according to the thread I found following the above link.

I hope it works.

---

### Post by jimmer72 on 2008-11-24
Well, it did not seem to help the issue.  Does anyone know if I have to specify the full path to the module?

ie

MODULES_WHITELIST="/lib/modules/2.6.24-21-generic/kernel/drivers/hid/hid.ko"

or will

MODULES_WHITELIST="hid"

work?

--Jim

---

### Post by Denny Johnson on 2008-11-24
When I posted above, I didn't bother to read the thread that I linked, I just pulled it out of my solutions folder.
Just re read it now, almost positive it was the #19 post that worked for me.
Good luck.

---

### Post by jimmer72 on 2008-11-27
Yup! It worked. For any having same problem, just run the following command:

sudo vim /etc/pm/sleep.d/25i8042

then copy and paste the following in the file and save it (make it executable):

#!/bin/bash

case "$1" in
        hibernate|suspend)
                # Unbind the AT keyboard interface.
                if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
                        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
                fi
                ;;
        thaw|resume) 
                # Rebind the AT keyboard interface.
                if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
                        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
                fi
                ;;
        *)
                ;;
esac

exit $?

---

### Post by ShamoIdol on 2009-11-07
Just to report. 
I've an old IBM Thinkpad X40 and got the same problem after upgrade to karmic. Fixed by adding 
MODULES_WHITELIST="hid usbhid"

---


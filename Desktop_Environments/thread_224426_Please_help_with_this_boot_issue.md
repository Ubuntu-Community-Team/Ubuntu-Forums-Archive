---
title: "Please help with this boot issue"
date: 2006-07-27
forum: Desktop Environments
---

### Post by inspired on 2006-07-27
Hi there,
I am running Ubuntu 6.06 on a PIII PC.
Was running no probs on 5.x and upgrading to 6.x also went fine.

In the last week, however, I've started getting a problem during boot-up.
I'd like to know one or both of the following:
1) Is there a way to simply "repair" the existing installation and get rid of this issue
2) Is there a way to identify what is causing this issue and to then fix that directly.

THE DATA:
During the boot process everything goes ok until it gets to "Checking all file systems"...

At this point it hungs, exits the graphic boot screen and reverts to the text based screen. On here it has the following:

```

Starting Enterprise Volume Management System
udevd-event[3248]: wait_for_sysfs: waiting for '/sys/devices/platform/i82365.0/bus' failed
```

It will sit here until I hit "CTRL-C"... and which point the boot process continues.

I notice that after I hit CTRL-C there is another line that appears which says something about not being able to find "/sbin/ifrename"

I would like to get this sorted out, and would greatly appreciate some assistance.
I've not managed to find any info on the forums or Google relating to this data.

With thanks,

Jonathan

---

### Post by grimmson on 2006-07-27
Not sure if this will help but see this post [http://www.ubuntuforums.org/showthread.php?t=198073&highlight=i82365.0](http://www.ubuntuforums.org/showthread.php?t=198073&highlight=i82365.0) best of luck

---

### Post by inspired on 2006-07-28
> **grimmson said:**
> Not sure if this will help but see this post [http://www.ubuntuforums.org/showthread.php?t=198073&highlight=i82365.0](http://www.ubuntuforums.org/showthread.php?t=198073&highlight=i82365.0) best of luck

Thanks, I shall try doing what that person did (i.e. reinstalling the kernal). Sounds a bit drastic though.

---

### Post by inspired on 2006-07-28
Some additional info regarding this issue:

When the boot-up reverts to the text based progress display right after the failed "Starting EVMS" issue (once I have hit CTRL-C to get it moving to the next step, it then reports that there is a problem with /etc/rcs.d/s40ifrename referring to a file that does not exist. That file is /sbin/ifrename

Does anyone have any idea what that might be about?

The script S40ifrename is as follows:
```
#!/bin/sh

NAME=ifrename
IFRENAME=/sbin/ifrename
IFTAB=/etc/iftab

test -f $DAEMON || exit 0
test -f $IFTAB || exit 0

case "$1" in
	start|reload|force-reload|restart)
		$IFRENAME -d -p -t
	;;
	stop)
	;;
	*)
		echo "Usage: invoke-rc.d $NAME {start|stop|reload|force-reload|restart}"
	;;
esac

exit 0
```

Perhaps this attitional info will help narrow this down?

Thanks,

Jonathan

---

### Post by inspired on 2006-07-29
I managed to fix the /sbin/ifrename error following instructions here [http://www.ubuntuforums.org/showthread.php?t=89491&highlight=ifrename](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=ifrename) to stop this service (and various other unnecessary ones) from loading.

Somehow the services I stopped also got rid of the error with "Starting Enterprise Volume Management System" because that now completes.

The graphical boot process still drops out at "Checking all file systems". On the text screen it shows that /boot, /home, /local, and /usr are all "clean". It finishes that process as ",...done"
It then moves to *Reading files needed to boot" and hangs here.
There is no error message.
I hit CTRL-C and it finishes that process and moves on with no further errors.

I'd really like to sort this out so the computer can boot without having to sit there and wait to push CTRL-C.

Any ideas?

Thanks,

Jonathan

---

### Post by inspired on 2006-07-29
I've fixed the issue.
It would appear CAPTIVE-NTFS was playing up.
I removed it and installed NTFS-3g which is working.

---


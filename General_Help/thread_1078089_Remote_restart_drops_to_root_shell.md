---
title: "Remote restart drops to root shell?"
date: 2009-02-23
forum: General Help
---

### Post by squarebracket on 2009-02-23
I have a mythbuntu box that I basically only access through SSH. But when I try to restart/shutdown via SSH, it ends up just closing everything and dropping to a root shell (no SSH or anything).

Any help would be appreciated!!

-Chuck

---

### Post by DagMan on 2009-02-23
Does the machine shutdown when you do it from the machine itself?
If not, perhaps there's hardware that isn't being released properly.  I've had two machines that had a problem like that, and with one the solution was to remove the sound module just before shutdown.
You can't really log anything when your filesystems are all unmounted, but perhaps if you remove "splash" as an option at boot time, and thus at shutdown as well, you can temporarily put the lsmod command in right before shutdown and see if anything is still loaded by looking at the output during shutdown... which is what caused one of my machines to hang.

I'd go about this by editing /etc/init.d/halt and inserting **lsmod**, along with some echo commands to see if things are indeed getting this far in the shutdown process, between these 2 lines ```
do_stop () {
	if [ "$INIT_HALT" = "" ]

```
so it looks like this at the beginning of the script (the following is not the whole script)
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () { 
echo "modules still loaded..."
lsmod
echo "end of lit..."
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

```
These are the three lines I inserted in the above:```
echo "modules still loaded..."
lsmod
echo "end of lit..."

```

If there are still modules loaded at that stage, then in that same spot, put **rmmod <name of module/s listed>**, and see if that helps.



Hopefully your problem is something this simple.  Another thing to consider is that if your box ever goes into a suspend mode, and it happens only after a session in which its suspended and resumed, it may have been a buggy suspend/resume process that needs troubleshooting.

---

### Post by DagMan on 2009-02-23
Just noticed the restart issue in this thread [http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

It could be your problem.

---


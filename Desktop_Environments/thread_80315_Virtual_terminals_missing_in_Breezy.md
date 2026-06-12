---
title: "Virtual terminals missing in Breezy"
date: 2005-10-21
forum: Desktop Environments
---

### Post by 23meg on 2005-10-21
I've done a clean install of Breezy and i get a blank screen when I hit ctrl + alt + f(x). The relevant portion of my /etc/inittab looks like this:

[PHP]1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
[/PHP]

I've been hinted that this might be a usplash issue. How can I temporarily disable it to see if that's the case? What else might be causing this? Before you ask: I don't have a vga=xxxx entry in my grub menu config.

---

### Post by 23meg on 2005-10-24
tried chmod -x'ing usplash to disable it but that didn't work. any other ideas for disabling it temporarily?

"ps a | grep getty" gives the following output:
```

 8199 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 8200 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 8201 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 8202 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 8203 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 8204 tty6     Ss+    0:00 /sbin/getty 38400 tty6

```

which i interpret as the terminals are actually running, but are obscured due to a display problem.

---

### Post by Joe_lurker on 2005-10-24
To temporarily disable splash edit the boot parameters at the GRUB boot screen.  When you see the GRUB boot menu press the 'e' key on the line you are going to boot.  This will drop you into the boot detail.  Hightlight the kernel line and press the 'e' key.  You can now edit the line.  Remove the words 'quiet' and 'splash'.  When you have made your changes press the [esc] key then the 'b' key to boot.

-Joe

---

### Post by 23meg on 2005-10-24
thanks; with usplash disabled virtual terminals are back, so it's a usplash problem. i think it "steals" the framebuffer device and does not release it after it's done with it, right?

---

### Post by SilentCacophony on 2005-10-24
Hi. The info you posted looks fine compared to mine. I have usplash running, with no problems, though. I have removed usplash with no problems on my other Breezy install, using the package manager, but I don't know if it reinstalls well.

Anyway, the only other files I know of related to usplash are /etc/rc**#**.d/K01usplash (where **#** = 0 through 6,) though there may be others I don't know of. I'll post what mine looks like if you want to compare.

```
#! /bin/sh
# 
# The usplash script makes sure that usplash exits at the end of 
# the boot sequence and re-run the console-screen.sh script to make
# sure that the console fonts are actually set
#
#		Written by Miquel van Smoorenburg <miquels@cistron.nl>.
#		Modified for Debian 
#		by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
# Version:	@(#)skeleton  1.9  26-Feb-2001  miquels@cistron.nl
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/sbin/usplash
NAME=usplash
DESC="Userspace bootsplash utility"

test -x $DAEMON || exit 0

set -e

usplash_quit() {
	# first some sanity checks if we actually have usplash on the system
	# 
	# check if usplash is runing and if it does, exit it
	# then re-run console-screen.sh because it can't set console-fonts
	# properly while the screen is in graphics mode
	# 
	# also check if we are ended up in console 8. This means that 
	# no gdm/kdm/xdm was started (otherwise we would be on vt7).
	# It happens when e.g. usplash timed out
	CONSOLE_SCREEN=/etc/init.d/console-screen.sh
	if [ -x $CONSOLE_SCREEN ] && type usplash >/dev/null 2>&1 && 
           grep -q splash /proc/cmdline &&
           ( pidof usplash > /dev/null || [ "$(fgconsole 2>/dev/null)" = "8" ] ); then
		# disable the cursor, for a nice black screen to sit on to avoid
		# text flicker on the user's screen while we're killing usplash
		clear > /dev/tty1
		#echo "[?25l" > /dev/tty1
	        chvt 1

		# ask usplash to go away
		usplash_write QUIT

		# wait until it is really gone or kill it if it dosn't exit
		i=0
		while pidof usplash > /dev/null; do
			i=$(($i + 1))
			if [ $i -gt 10 ]; then
				kill -9 `pidof usplash`
				break
			fi
			sleep 1
		done

		# and, finally, reset all our virtual consoles, yay!
		$CONSOLE_SCREEN
		# re-enable that cursor, s'il vous plait
		clear > /dev/tty1
		#echo "[?25h" > /dev/tty1
		chvt 1
	fi
}

case "$1" in
  start)
	usplash_quit
	;;
  stop)
	usplash_quit
	;;
  *)
	N=/etc/init.d/$NAME
	# echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $N {start|stop}" >&2
	exit 1
	;;
esac

exit 0

```

---

### Post by blazoner on 2007-06-15
I had the same problem with Virtual Terminals in Feisty 7.04, they were there, but illegible due to flickering of the screen, but even uninstalling usplash didn't solve it for me.  Eventually, I started playing around with [SUM]("http://web.telia.com/~u88005282/sum/index.html"), chose a compatible resolution for my usplash, and VOILA!  VT's working again, and now with smaller, more legible text.

Hope this helps someone else! :D

---


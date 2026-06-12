---
title: "CTRL+ALT+F[1-6] problem"
date: 2006-11-22
forum: Desktop Environments
---

### Post by Mis_Uszatek on 2006-11-22
Hello everyone

I have a problem with a text terminal.
There is no problem with standard graphical user interface, but in case CTRL+ALT+F[1-6], when I am trying to switch to a text terminal/console, I have got only black screen.

I have got NVIDIA graphic card, my drivers were installed by method 1 from this post : 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Did/Does anybody have got this problem? Does anybody know any solution?

Best regards

---

### Post by tomcheng76 on 2006-11-22
do you have these line in /etc/inittab ?
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

---

### Post by Zamboniman on 2006-11-22
Also check that your getty program is installed and working correctly.

---

### Post by Mis_Uszatek on 2006-11-23
I have these lines

At the bottom is full /etc/inittab

getty is working

I have done a little experiment

I checked are there any mc processes. There were not any.
Next I tap ctlr+alt+f1, screen went black, I type my login, enter, type my password, enter, type mc,enter. came back to X(ctrl+alt+f7), I typed ps -A, and there were two processes mc on tty1
12043 tty1     00:00:00 bash
12066 tty1     00:00:00 mc

So text consoles are working, but they are not displayed on my screen. 

Any suggestions?


Here is my full inittab

```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

```

---

### Post by Mis_Uszatek on 2006-11-23
And one more thing

When I change in xorg from nvidia to nv(so nvidia driver is not loaded) everything is ok. 
In that case text console is displaying correctly(I can see what I type). 
But when driver is loaded, text console is not working correctly(I cannot see what I type).

---

### Post by ampop on 2007-01-17
I have the same problem! How to solve this matter. Please.
Thank you.

---

### Post by Mis_Uszatek on 2007-01-19
So I am not the only one.
Unfortunately, I still didn't find out any solution.

---

### Post by kingmonkey on 2007-01-19
I have this  problem.

I dont have a /etc/inittab

---

### Post by yota on 2007-01-19
Hi,

I had this problem and solved it by removing the 'vga=XXX' parameter, passed to the kernel at boot time, in /boot/grub/menu.lst
Please pay attention to the '# defoptions' directive too.
This obviously imply that the virtual terminal will revert to the quite ugly default text mode... but it's still better than the black screen!

Hope this helps.

---

### Post by ampop on 2007-01-19
> **yota said:**
> Hi,

I had this problem and solved it by removing the 'vga=XXX' parameter, passed to the kernel at boot time, in /boot/grub/menu.lst
Please pay attention to the '# defoptions' directive too.
This obviously imply that the virtual terminal will revert to the quite ugly default text mode... but it's still better than the black screen!

Hope this helps.

Where did you did this change? /boot/grub/menu.lst?

---

### Post by scrooge_74 on 2007-01-19
did you check the info in this site ?  [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)


My Nvidia is working ok following this info

---

### Post by ampop on 2007-01-19
> **scrooge_74 said:**
> did you check the info in this site ?  [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)


My Nvidia is working ok following this info

Yes, I already did that. Thanh you any way.

---

### Post by Mis_Uszatek on 2007-01-25
> I had this problem and solved it by removing the 'vga=XXX' parameter, passed to the kernel at boot time, in /boot/grub/menu.lst
Please pay attention to the '# defoptions' directive too.
This obviously imply that the virtual terminal will revert to the quite ugly default text mode... but it's still better than the black screen!

Hm...
I don't have this parameter in menu.lst

My options for boot are :

```
title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot
```

and I don't have any defoptions(only with #, but as I understand it means comment).

---

### Post by ampop on 2007-02-13
See: [http://ubuntuforums.org/showthread.php?p=2147979#post2147979](http://ubuntuforums.org/showthread.php?p=2147979#post2147979)

> I got this to work easily by changing the bit of /boot/grub/menu.lst (making a backup first) that says:

title Ubuntu, kernel 2.6.12-10-k7
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-k7
savedefault
boot

to make it say:

title Ubuntu, kernel 2.6.12-10-k7
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 **vga=792** ro quiet splash
initrd /boot/initrd.img-2.6.12-10-k7
savedefault
boot

It works with me. Thanks to [Huffers]("http://ubuntuforums.org/member.php?u=54583").

---


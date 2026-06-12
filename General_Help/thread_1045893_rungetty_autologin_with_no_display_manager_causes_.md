---
title: "rungetty autologin with no display manager causes broken mouse"
date: 2009-01-20
forum: General Help
---

### Post by librano on 2009-01-20
Hi all!

I am trying to set up a light single user system so I removed gdm and tried to use rungetty to handle the autologin and starting of X. I am using Fluxbox but this problem is present with XFCE as well. I am using Xubuntu Intrepid.

I have setup the system following this post:
[http://ubuntuforums.org/showpost.php?p=4552480&postcount=3](http://ubuntuforums.org/showpost.php?p=4552480&postcount=3)

This is the contents of /etc/event.d/tty1
> # tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
#exec /sbin/getty 38400 tty1
exec /sbin/rungetty tty1 --autologin librano

My ~/.bash_profile is:
> startx

And my ~/.xinitrc is:
> startfluxbox

**_The Problem_**

When I boot the system X starts ok and then Fluxbox starts up as well. But the mouse does not work. The cursor is present but I cannot move it and I cannot use the buttons. The keyboard works fine.

However, if I restart X by Ctrl+Alt+Backspace or Ctrl+Alt+F*, then kill Fluxbox and restart X, the mouse works fine!

I have tried different combinations of the .bash_profile and .xinitrc files... but I end up with either plain X with nothing or Fluxbox failing to connect to X. Note that the mouse doesnt work even when it is only plain X (no WM, no terminal, nothing).

What am I doing wrong? How can I fix this? 

Thanks for your help in advance!

---

### Post by librano on 2009-02-02
bump!

---

### Post by cong06 on 2009-11-26
Did you ever figure this out?

I have the same configurations as you posted, but when I turn the computer on, tty1 pauses/hangs.
It auto-logs in when I switch to tty2, and log into a terminal, but I can't get it to log in on it's own.

---


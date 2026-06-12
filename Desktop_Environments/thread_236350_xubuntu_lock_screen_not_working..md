---
title: "xubuntu lock screen not working."
date: 2006-08-14
forum: Desktop Environments
---

### Post by eylisian on 2006-08-14
xubuntu/ubuntu 6.06 works really well with one exception, the lock screen option isn't locking the desktop. this is an issue as I have to log out to secure the workstation... click on the "lock screen" icon and... crickets.
 Xorg.0.log(s) yeilds nothing, nor does acpid or messages... even pointers to where I should be looking to troubleshoot this would be welcome.

thanks,
Bob

---

### Post by Goofy666 on 2006-11-07
Are you sure that the xscreensaver daemon is running? I had the same problem after necessarily updating my video card driver, after which I started XFCE through the startx command. I didn't came to it that this was the problem (the daemon does not start automatically using startx) until I tried to open the 'Screensaver options' window in the 'Settings manager'; trying that I got a warning that the daemon was not running.

In short (I apologize for the whole story...); make sure that the xscreensaver daemon is running in the background, otherwise the lock screen function won't work.

[SIZE="1"]Again I apologize (this time for the bump); I posted this for the sake of all the other lurkers and Googlers out there. Hopefully eylisian will get it to read as well.[/SIZE]

---

### Post by fortran01 on 2006-11-07
If you are using the gnome-screensaver instead of the xscreensaver, you need a quick hack to point the lock screen feature to gnome-screensaver.

---

### Post by dare2dreamer on 2007-01-30
would you care to elaborate on what that "quick hack" is?

---

### Post by fortran01 on 2007-01-30
Source: [http://www.linuxquestions.org/questions/showthread.php?t=458516](http://www.linuxquestions.org/questions/showthread.php?t=458516)

By default, xfce screensaver requires xscreensaver. You have the *option* to remove xscreensaver using the following command (as privileged):

```
apt-get remove xscreensaver
```


To install gnome-screensaver use the following command (as privileged):

```
apt-get install gnome-screensaver
```


To auto-start gnome-screensaver, add it as an Autostarted Application:

Xfce menu > Settings > Autostarted Applications

The command for starting the gnome-screensaver daemon is:

```
gnome-screensaver
```


To be able to use the action button "Lock screen" to start gnome-screensaver immediately and lock your screen, modify the file /usr/bin/xflock4:

```
#xscreensaver-command -lock || xlock $*
gnome-screensaver-command --lock exit 0
```


Note that the original xscreensaver command is now commented. Backup the original copy of xflock4 (as privileged):

```
cp /usr/bin/xflock4 /usr/bin/xflock4.orig
```


Hope that helps.

---

### Post by dare2dreamer on 2007-01-31
works like a charm. Thanks ever so much.

---

### Post by evilhomer on 2007-12-31
Just in case anyone else comes across this thread, a more elegant solution is to simply install xlockmore :)

---

### Post by chewearn on 2008-01-20
> **evilhomer said:**
> Just in case anyone else comes across this thread, a more elegant solution is to simply install xlockmore :)

Well, just installed xubuntu over the weekend, the screen won't lock after "blank screen" screensaver comes on.

Installed xlockmore, no difference, still won't lock.  Any idea?  Thanks.

---

### Post by chewearn on 2008-01-20
Ok, nevermind, after somemore googling, I came across this:
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251)

Looks like gnome-screensaver is not launched automatically due to bug; so manually add a start-up entry solves the problem.

---

### Post by rykel on 2008-01-24
Hi pals,

Like the rest of you, my xscreensaver is NOT coming on when I click on the Lock Screen icon on the Xubuntu panel...

However, mine is xscreensaver-gl rather than xscreensaver... is that the reason why Lock Screen cannot find the screensaver? If so, how do I set it to use xscreensaver-gl instead of xscreensaver?

Thanks for advising.

---

### Post by xybre on 2008-02-08
Modify the file /usr/bin/xflock4 change the xscreensaver to xscreensaver-gl or whatever.

---

### Post by Belak on 2008-02-16
> **xybre said:**
> Modify the file /usr/bin/xflock4 change the xscreensaver to xscreensaver-gl or whatever.

Or install the xscreensaver package along with the extra xscreensaver-gl 'hacks'

---

### Post by rykel on 2008-02-18
Hi all,

I ran gnome-screensaver in a terminal and then Lock Screen - it worked.

Now, I added gnome-screensaver to the Autostarted Applications and believe that it should work.

No, I did NOT have to hack any config files...

I am doing this on eeeXubuntu 7.10 btw!!   :lolflag:

---

### Post by teohhanhui on 2008-04-30
This works, but I wonder why it is not autostarted by default.

---


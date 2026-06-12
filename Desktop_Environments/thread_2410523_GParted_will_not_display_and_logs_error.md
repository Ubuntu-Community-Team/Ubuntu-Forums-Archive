---
title: "GParted will not display and logs error"
date: 2019-01-16
forum: Desktop Environments
---

### Post by blown2bytes on 2019-01-16
I am trying to use GParted and I have installed it using APT. When I run the software however, it prompts for my sudo password but fails to actually open. I see it in the activity bar for a few seconds and then it goes away.

If I run it from the terminal, I see the following error (sometimes the number changes).
(gpartedbin:3651): Gtk-WARNING **: 11:27:23.390: cannot open display: :0

I've tried opening using sudo -H and pkexec (since gksudo is not an option any more).

I'm using ubuntu 18.04.

Any ideas on what might be the problem?
Thanks

---

### Post by tea for one on 2019-01-16
Are you running a Wayland session?

There is a workaround for Wayland sessions such as [http://gparted-forum.surf4.info/viewtopic.php?id=17446](http://gparted-forum.surf4.info/viewtopic.php?id=17446) but I always log in as an X session to avoid this type of dilemma.

---

### Post by ajgreeny on 2019-01-17
See if this thread helps you; it sounds like the same problem to me.
[https://ubuntuforums.org/showthread.php?t=2409234](https://ubuntuforums.org/showthread.php?t=2409234)

---

### Post by blown2bytes on 2019-02-11
> **tea for one said:**
> Are you running a Wayland session?

There is a workaround for Wayland sessions such as [http://gparted-forum.surf4.info/viewtopic.php?id=17446](http://gparted-forum.surf4.info/viewtopic.php?id=17446) but I always log in as an X session to avoid this type of dilemma.

Yep, that seemed to work. I was using Ubuntu on Wayland as my login session, but when I switched to just the "Ubuntu" session (I assume this is on Xorg) it worked.

---


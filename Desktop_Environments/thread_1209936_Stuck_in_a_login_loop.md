---
title: "Stuck in a login loop"
date: 2009-07-10
forum: Desktop Environments
---

### Post by NathanaelCulver on 2009-07-10
(This is a duplicate of thread [http://ubuntuforums.org/showthread.php?t=1047692](http://ubuntuforums.org/showthread.php?t=1047692) but as I can't get any response over there, I'm trying here.)

I'm running Ubuntu Jaunty on an Asus laptop. Several days ago I experienced a power outage. Now when I attempt to log in, I can't get past the login screen -- I just get a black screen, a quick flicker, and then I'm back at the login screen. I don't get "Failed login", and I can log into any of my user accounts from a terminal (Ctrl-Alt-F2), so it's not a credentials problem.

In my Sessions Type menu I have the following: Default, GNOME, GNOME/Openbox, KDE, KDE/Openbox, Openbox Session, Secure Remote Connection, Window maker, and Failsafe. I get the same result no matter which one I try (except SRC, which gives me "Login failed"), so it's not Gnome- or KDE-specific.

I suspect it's just a matter of some corrupted config file, but I'm not sure where to look.

Anyone?

Nathanael Culver

---

### Post by rainwalker on 2009-07-10
It's probably not likely, but how much space do you have free on your hard drive? The only time I ever had that problem was when my hard drive was full.

---

### Post by Clorow on 2009-07-11
Try editing your ~/.profile. I tried editing mine a while back, but I was a n00b back then, so I forgot to send a process to the background, causing it to hang on a black screen after login. If you edited your .profile, then undo your changes by pressing Ctrl+Alt+F1 and logging in as root, followed by vim /home/your_name/.profile.

---

### Post by NathanaelCulver on 2009-07-11
> **rainwalker said:**
> how much space do you have free on your hard drive?

In fact, the power outage occurred as I was trying to clean out a full /home partition, but I've since freed up some space. Currently, df -H shows 9.2gb free on my root (/) partition, and 4.9gb on my /home partition. I've also cleaned out /tmp (though there wasn't much there to begin with), and I'd like to clean out .Trash, if only I could find it.

> **Clorow said:**
> Try editing your ~/.profile.

I don't have one. In any case, I have several user accounts on my system, and they all exhibit the same behavior. Since both a) all users, and b) all session types have the same problem, I suspect it's an Xserver problem. I tried dpkg-reconfigure Xserver-xorg to rewrite my xorg.conf, but that didn't help, either.

NathanaelCulver

---

### Post by Nathanael Culver on 2009-07-12
OK, so I fixed it the hard way -- I reinstalled. It gave me the chance to upgrade to 64-bit.

NathanaelCulver

---


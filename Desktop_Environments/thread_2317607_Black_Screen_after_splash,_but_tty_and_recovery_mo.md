---
title: "Black Screen after splash, but tty and recovery mode work"
date: 2016-03-18
forum: Desktop Environments
---

### Post by jonathan81 on 2016-03-18
My Lubuntu 15.04 machine has a problem when booting.

When booting normally, it goes to a black screen after the LUbuntu splash screen. But if I press ALT+CTRL+F3 I get to tty and can log in (to a terminal!)

If I select a recovery mode, I can boot fine.

What steps can I take to fix this?

I tried running these from tty to fix it, but they have not worked:

 [COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall lubuntu-desktop, but it has not helped.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade[/FONT][/COLOR]

---

### Post by v3.xx on 2016-03-18
Have you tried nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jonathan81 on 2016-03-18
Thanks. That worked.

The link is a bit complicated. To summarise what I did:

```
gksudo gedit /etc/default/grub
```

Modify the line that looks like this to

```
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

[/B]
```run```
sudo update-grub
```

Strangely, when booting, I get a black screen with funny circle in the middle. But it works, and that's what counts.

---

### Post by v3.xx on 2016-03-18
You got it, nice job :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


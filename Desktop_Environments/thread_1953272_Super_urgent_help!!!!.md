---
title: "Super urgent help!!!!"
date: 2012-04-05
forum: Desktop Environments
---

### Post by The_Autonomist on 2012-04-05
SO, i upgraded from 11.10 to 12.04. No issues except that my window decorations wouldn't work. So, i Googled it, and saw that someone said to install kde (kwin) so that's what i did...

Now i don't know what HAPPENED. But now, i can't log into Ubuntu. My pretty lightdm Ubuntu 12.04 log in screen is gone and has been replaced with this: 

[IMG]http://lightbox-photos.s3.amazonaws.com/photos/e681469f2a84ce11af1438a5fe3f415f_348303_lrg.jpg[/IMG]

I keep typing in my Ubuntu username and password...but it isn't working. I'm terrified because I use UBuntu 98% of the time and only log onto Win7 (which i'm on now) for iTunes.

Can someone please help me reverse this or fix this???? How do i get my regular Ubuntu back???

---

### Post by LinuxFan999 on 2012-04-06
Ubuntu 12.04 is currently beta quality software, and is not yet recommended for daily use.

Go to the terminal (by pressing ctrl-alt-f1), then try logging in there. After doing that,type this in the terminal:
```
sudo apt-get purge kdm
```
Then type these two commands:
```
sudo apt-get update
sudo apt-get install lightdm
```
Reboot when the process is complete.
```
sudo reboot
```

---

### Post by nothingspecial on 2012-04-06
Duplicate thread.

Closed.

---


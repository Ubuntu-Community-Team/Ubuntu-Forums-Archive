---
title: "[SOLVED] KDE install makes login fail"
date: 2007-09-17
forum: Desktop Environments
---

### Post by becominglumberg on 2007-09-17
This past weekend, I installed KDE (addingkubuntu-desktop to Feisty). When it asked me what I wanted to default as, I chose kdm.

Now, when i am brought to the login screen, I put in my logname and password, hit enter...

The computer will thing for three seconds, the screen will blink like it is taking me to a desktop, and then it will bring up the login again, as if I hadn't done anything.

This happens whether I choose a KDE or GNOME session. The only thing that lets me log in right now is CLI mode.

Any advice to get me up and running again would be appreciated.

Thanks,
Guy

---

### Post by bydlo23 on 2007-09-17
I experienced the exact same symptoms the other day.

My situation was a little different, I did a fresh install of kubuntu and was messing around with mounting /home on a separate partition.

When I tried startx from the command line it spit out some errors which eventually led me to find out it was a problem with /home.

I'm a total noob so I don't know much about this stuff, but this might at least provide you with a place to start.

---

### Post by becominglumberg on 2007-09-19
Failing this being able to be fixed, does anyone know the best way to get some of the recent docs put on the hard drive onto another computer using the live CD? I assume I can just read them from the filesystem and write them to a hard drive?

---

### Post by Wolki on 2007-09-19
> **becominglumberg said:**
> Failing this being able to be fixed, does anyone know the best way to get some of the recent docs put on the hard drive onto another computer using the live CD? I assume I can just read them from the filesystem and write them to a hard drive?

That should work. Just mount the partition ("mkdir temp", then "sudo mount /dev/<yourpartition> temp" and you should be able to access the data. Now the question is how to ge them onto another computer, easiest is via an external harddrive, but it should be possible via the network.

But I'm quite sure your problem can be fixed. Try starting X manually as bydlo23 suggested and see if you get any errors. Log into a console (ctrl-alt-f1 and login), then doing "sudo invoke-rc.d kdm stop" should probably work for stopping X, then startx to start it manually and read the output.

Another thing you could do is logging in normally (and have it fail), then take a look at the file ~/.xsession-errors which may contain relevant error messages.

Did you try going back to gdm? "sudo dpkg-reconfigure gdm" will offer you the selection again if I'm not mistaken, you could also just remove kdm.

---

### Post by cknight on 2007-09-19
Wow, I may actually be able to help here.  The same exact thing happened to me.  The problem may be related to you being out of disk space.  kubuntu-desktop is a pretty large install, so maybe this filled your drive?  Try this (after logging in via CLI) to see what space you have left:

```
df -h
```

Anyway, check out my thread:  [http://ubuntuforums.org/showthread.php?t=491769](http://ubuntuforums.org/showthread.php?t=491769)

Good luck!

---

### Post by becominglumberg on 2007-09-19
Wow, I owe you a beer. df - h showed that i have a full file system.

Let this serve to show that I am very impressed with the deluge program.

I am back to using gdm as well. Thanks everyone for helping out.

---


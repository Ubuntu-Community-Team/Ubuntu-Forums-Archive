---
title: "Advanced process control"
date: 2007-08-05
forum: Desktop Environments
---

### Post by 11touche on 2007-08-05
Okay I have a hard question here. How can I transfer an already running process to another display and/or shell? Don't say to me by 'screen' beacause I already tried and that's not what I'm looking for.
I'll explain a little bit more here:
I have a destop box and a laptop, and my laptop is connected through ssh -X to my desktop. The laptop is an old P2 333mhz with 16mo of ram, so I just use it to run X apps on the desktop over ssh.
I'm already on a dual-screen setup on my desktop, but if I could, I would have 10203 screens because I work on Gimp and I chat at the same time, and if you ever tried to do this, you'd notice it's more convenient to have a maximum desktop place to work around. Anyways, my real problem is that: When Gimp isn't started, I can keep aMsn and xChat on my second screen on my desktop, but when I want to work on Gimp, I need to send these two (or more) windows on my laptop, through ssh (with DISPLAY=:10.0 command). BUT I need to close the apps, and then to restart them (and obviously reconnect on both) which is quite annoying. So I wondered if I could switch a process's display variable or bring it back to a shell (ie. my ssh shell) with somewhat SIG or process control command. I already tried to start aMSN in screen, bg it, change the display variable, and then fg it back but it still displays on my desktop computer.
Lots of people told me it wasn't possible to achieve this, but I'm certain there's a way, since Linux is flexible.
An another possibility would be to add my laptop as an extension to my current desktop, but I don't know either how to achieve this. 
Hope there's someone here to help me out with my questions !!!

---

### Post by ruibernardo on 2007-08-05
I have never used it, but I was curious about this some time ago:

usr@ubuntu-desktop:~$ apt-cache search xmove
xmove - allows you to move programs between X Window System displays

One link that I found was this one: [http://help.lockergnome.com/linux/Keeping-programs-running-server-ftopict381486.html](http://help.lockergnome.com/linux/Keeping-programs-running-server-ftopict381486.html)

I didn't want to open my X to the outside, so be careful. Don't even know if it really works.

---


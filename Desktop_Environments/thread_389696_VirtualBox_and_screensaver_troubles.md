---
title: "VirtualBox and screensaver troubles"
date: 2007-03-21
forum: Desktop Environments
---

### Post by futz on 2007-03-21
I just installed VirtualBox and installed Windows XP in it. Works GREAT, and so easy to install & configure! Had some strangeness with getting USB stuff working properly, but a quick forum search and I found this thread, [http://ubuntuforums.org/showthread.php?t=341740&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=341740&highlight=virtualbox), which, after lots of confusion and experimentation and a bunch of restarts, helped me get everything working correctly.

But I've run into a strange problem that I don't know what to do with. I have a screensaver (DPMS turns the monitor off to save energy) that runs after a few minutes of inactivity. When VirtualBox has the mouse & keyboard captured and the screensaver starts at the same time, there's no way out. You're trapped, and the only way I can find to get out is to hit the reset button and reboot.

You'd think that hitting the right CTRL key would let you out of VirtualBox, giving the mouse/keyboard back to Ubuntu so you could hit any key or move the mouse and shut off the screensaver? Well it should, but it doesn't. 

Anyone have any ideas besides disabling the screensaver?

EDIT: If it makes any difference, all this is running in Beryl. Yup, wobbly WindowsXP :mrgreen:

---

### Post by futz on 2007-03-26
bump

---

### Post by hikaricore on 2007-03-26
You could set it that Virtual Box doesn't capture your keyboard and mouse.

I've never had any trouble using it this way.

Also I don't specifically understand why you'd need a screensaver on your virtual windows box.  
If this is a 3d screensaver you may be pushing it /w beryl running.  I've managed to run various
opengl screensavers on my win2k vbox with no trouble, but never while running beryl or with
device capture (keyboard/mouse) enabled.

---

### Post by futz on 2007-03-26
> **hikaricore said:**
> You could set it that Virtual Box doesn't capture your keyboard and mouse.

I've never had any trouble using it this way.

Also I don't specifically understand why you'd need a screensaver on your virtual windows box.  
If this is a 3d screensaver you may be pushing it /w beryl running.  I've managed to run various
opengl screensavers on my win2k vbox with no trouble, but never while running beryl or with
device capture (keyboard/mouse) enabled.
It's the Ubuntu screensaver that's doing it. There is none on the XP install. That would be silly.

I didn't know you could use vb without mouse/keyboard capture. Guess I should take some time and really read that boring manual.

---

### Post by TabletUbuntu on 2007-03-26
I just had the same problem.  I tried to kill the screen saver after hitting ctrl-alt-F1 and logging in to a shell, but it did not help.  I havn't installed the XP guest additions yet, maybe that will help.

As an aside, virtualbox works so much better than qemu, of which up until today I was a big fan.

---

### Post by joco2 on 2007-04-07
I had a similar problem in that my mouse was captured into the XP virtual machine and then the only I could get out was to shut the machine down but after installing the guest additions this solved my problems.

I tried installing other virtual machines like VMplayer etc but could never get them to work. VirtualBox was very simple to install and use. I'd recommend it to anyone who wants to run XP as a virtual machine thereby avoiding dual boot

---


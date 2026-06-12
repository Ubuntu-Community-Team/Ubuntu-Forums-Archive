---
title: "can't minimize to tray"
date: 2010-06-29
forum: Desktop Environments
---

### Post by chicoharv on 2010-06-29
when I try to minimize to tray , any app disconnects or is hidden and I cannot bring it back up. If I leave app alone and just bring another app up it is still there behind new app. using lucid do not remember if this started at upgrade or later.

---

### Post by flick on 2010-06-29
So if you click on the app's button in the taskbar, the taskbar button and the window with the app in it both vanish?

---

### Post by chicoharv on 2010-06-29
No. If I try to min. an app, it does not go to the tray, it just quits and leaves me hanging.I have to bring up the app again, depending on the app I may have to restart. ?is taskbar and tray the same thing in Ubuntu now? I added alltray in package manager ,no difference. app still quits rather than go to a tray,same as hitting X. I used to hit minus and app would move to tray (taskbar?)now when I hit the minus it is the same as "X".

---

### Post by s_raiguel on 2010-07-05
I've started getting this in the last few days, as well! If I try to minimize an app, it disappears from the desktop but does NOT appear on the taskbar, but ps -A or system monitor shows an instance of the program still running in the background. Changing desktop themes has no effect and there doesn't seem to be any setting in System Configuration relating to showing/hiding minimized applications, so I can't figure out what's going on.

Are you also using 64-bit Lucid?

---

### Post by chicoharv on 2010-07-05
No I am using 32 bit Lucid and it is only happening on my Acer laptop not my HP PC. Both computers are dual OS's The HP has Windows XP Pro and the Acer has Vista.

---

### Post by s_raiguel on 2010-07-05
I also have a dual boot, but I don't think that has anything to do with it. I think that conpletely reinstalling the Gnome desktop would most likely cure our problem. I did this about a year ago, when I messed things up by trying to remove all the parts of Evolution. Unfortunately, I can no longer remember, nor find, the exact apt-get install command for completely reinstalling all the parts and dependencies of the desktop. Seems like maybe the fix-missing option was used as well. Sorry I don't have any better advice to offer, but like you, I'm mystified.

---

### Post by s_raiguel on 2010-07-05
Try this...it worked for me, and it's one of those simple, D'Oh! kinds of things: Right-click on the lower task bar, then select "add to panel". From the list of items, select "Window Selector" (near bottom of list) and push "Add" button. I think I remember going "what the hell is this?" a few days ago and removing it to see what it was, then, when it wasn't immediately apparent what it did, I forgot about it.

---

### Post by chicoharv on 2010-07-05
That did it, I must have deleted it by accident. Problem solved. Thank you

---


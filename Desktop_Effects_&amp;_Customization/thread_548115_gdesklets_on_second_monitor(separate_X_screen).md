---
title: "gdesklets on second monitor(separate X screen)?"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by gschoppe on 2007-09-10
So, I've got two monitors, running as separate X screens via the options in sysinfo.  I want gdesklets to run at boot on the second monitor.  Currently, everything works great until I reboot.  Then, gdesklets opens on the primary display, not the secondary.

How can I change this behavior?

---

### Post by gschoppe on 2007-09-11
Fixed one issue... it will start on the secondary display with the command 

DISPLAY=:0.1 gdesklets start

however, I'm unable to make it run on startup... now I'm truly confused...

any help?

---

### Post by gschoppe on 2007-09-11
Got it!

the startup command is:
var DISPLAY=:0.1 gdesklets start

---

### Post by graabein on 2008-05-15
I have a similar setup where my TV (screen1) is just for watching fullscreen tv-out movies. I'd like to get rid of the GNOME panels on that screen. Any idea how I do that?

---

### Post by AcidHawk on 2008-05-15
gschoppe: I can't thank you for some reason, but this post was really helpful.  Thanks Mate

---

### Post by gschoppe on 2008-05-15
graabein, as long as they are separate x screens, you should be able to just right click on each panel, and close it...  if I recall correctly

---

### Post by graabein on 2008-05-16
But they're separate, they're not twinview. I can't get the mouse cursor onto screen1 (as intended). I want to work on my monitor (screen0) and just send [fullscreen video]("http://ubuntuforums.org/showthread.php?p=4940762#post4940762") content to television (screen1) from VLC.

---

### Post by gschoppe on 2008-05-16
i understand that they're separate x-screens, but why can't you move your mouse between them?

---

### Post by graabein on 2008-05-18
Because they're *separate* not *twinview*! :)

---

### Post by CronoDekar on 2008-05-23
I've got a similar issue to graabein if anyone can help, I'm not in twinview either, but I can move my mouse between them.  Similarly, I would like the gnome-panels gone since the TV is mainly used for fullscreen programs.  Deleting the panels works for the session, but when I reboot it all goes back to default.

Is there any way I can get it to "remember" the settings for the second display?

---

### Post by Garyu on 2008-06-14
> **CronoDekar said:**
> I've got a similar issue to graabein if anyone can help, I'm not in twinview either, but I can move my mouse between them.  

Where is the setting for moving the mouse between separate X screens or not? And if you can't move your mouse between the X screens, how do you switch? Seems like simple questions, but I've googled every word combination I can think of and no one has an answer for it...

Yes, I have the same issue. Tried twinview, but my second monitor is my TV and I want to watch movies on it, which doesn't work very well with half the movie on the TV and the other half on the monitor. Apparently, there is a way to configure twinview to handle monitors as separate X screens, but I would rather get the actual separate X screens to work.

I tried looking at man pages, but that didn't give much info about this issue as far as I could see.


**EDIT:**Hey... I found it! :)

What you need to do (at least for Hardy Heron 8.04.1) is enable Xinerama (small checkbox in nvidiasettings). That will remove the panels in the second screen, but that works fine for me. You can drag windows into your other separate X screen and maximize them making them maximized only on that screen. Perfect.

---


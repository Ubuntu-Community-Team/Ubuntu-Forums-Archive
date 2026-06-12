---
title: "nautilus crash after last upgrade :("
date: 2005-05-28
forum: Desktop Environments
---

### Post by vishna on 2005-05-28
i have no icons, no wallpaper on my desktop -  only gdesklets work fine. i can login to gnome but i can't logout and i can't browse my files with nautilus. nautilus simply doesn't start and there is no way to make it start unless i run as root - but this does not recover my desktop.  ](*,) 

for a while it seems to me i'll have to switch to KDE but what will I do when KDE fails after another upgrade? - anyway thanks in advance for your help.

---

### Post by sebest on 2005-05-28
you could try starting it from a terminal to have some debug message maybe?

---

### Post by JohnC86 on 2005-06-07
I'm having the same problem, very annoying, only for me it's from boot up, I can't work out what i've done/installed to mess it up, but when I turn the PC on nautilus just doesn't bother to come on.

Nautilus isn't actually dead though, it's still running, and when i kill it and restart it it's fixed, no problems!
any ideas?

---

### Post by puddleglum on 2005-06-07
For me it dies when the mouse cursor is over an mp3 file long enough to where it tries to play it.  When I turned off playing sound files things stabilized.

---

### Post by xbill on 2005-06-07
I have the same probleme sometime after the last upgrade. I kill nautilus and that OK. Annoying :/

---

### Post by oritpro on 2005-06-08
[QUOTE=vishna]i have no icons, no wallpaper on my desktop -  only gdesklets work fine. i can login to gnome but i can't logout and i can't browse my files with nautilus. nautilus simply doesn't start and there is no way to make it start unless i run as root - but this does not recover my desktop.  ](*,) 

for a while it seems to me i'll have to switch to KDE but what will I do when KDE fails after another upgrade? - anyway thanks in advance for your help.[/QUOTE]

I had this problem when I installed Ubuntu on a system that had an old IBM USB webcam plugged into it.  The driver was hanging things up, unplugging the camera solved it. I didn't need the thing on there anyway. 

Whether related or not, you should be able to get to the console by pressing Ctrl+Alt+F1, login to the system and check the logs i.e. less /var/log/messages or to monitor them live: tail -f /var/log/messages can very useful.

You'll find X messages in a different log file, /var/log/Xorg.0.log.

---

### Post by dtfinch on 2005-06-28
I've been having a similar problem for about a month. It probably started around the same time this thread started, and after an upgrade. What happens (in my case) is nautilus freezes on startup with 100% cpu usage, so no desktop is displayed, additional instances won't start, etc. If I kill the existing nautilus process, it'll reload with no problems, I'll get a desktop with icons, and everything is fine until my next reboot. It freezes only about 2/3 of the time.

---

### Post by modaniel on 2007-04-23
cc

---

### Post by rockin_goliath on 2007-04-27
This solved it for me. I don't know if you guys had the exact same problem I had, but I had very similar symptoms.

One day nautilus just pooped on me. When I logged in, there were no icons on the desktop, no wallpaper, and I couldn't open the file browser. Even pushing the "power button" on the panel didn't do anything; I had to log out by restarting X (ctrl+alt+backspace). However, when I logged into the root account, everything worked fine.

Fortunately, I have a rule that I don't change ANY settings in my root account. NONE. That way, if something works in root that doesn't work in my normal user account, I know it's a user specific problem. 

In my normal account, I killed the nautilus process in the system monitor. Then, I opened a panel and typed "nautilus" to try and start it again. It gave me an error message that said something to the effect of "CRITICAL: your font settings are smaller than what nautilus is capable of drawing." That made me realize that setting my font settings to values smaller than the minimum (size 7) may be the cause of the problem. I went into font settings, changed all the values to 8, and my wallpaper came back, my icons came back, and I was able to open the file browser again.

This might have something to do with the fact that I use different font rendering packages, outlined in this post:
[http://ubuntuforums.org/showthread.php?t=343670]("http://ubuntuforums.org/showthread.php?t=343670")

Hope this helps someone!

---


---
title: "Coolbits problem..."
date: 2007-03-21
forum: Gaming &amp; Leisure
---

### Post by steevz on 2007-03-21
I've searched everywhere for this with no success.

Okay, I'm having an issue using Coolbits. I have it install properly and everything. I open
Applications>System Tools>NVIDIA X Server Settings, goto Clock Frequencies.
Enable Overclocking. Goto 3D.
Move the sliders to desired position, in my case it's 480/369.
Click Apply.

Both the sliders go back down to 350/350. Every time I do this it happens. How can I make the card stay overclocked?

Thanks in advance.

---

### Post by hikaricore on 2007-03-22
I've seen this issue in my setup, i found the trick is typing the number you want in the box, then hit enter.
Repeat for the 2nd box.

Then click apply.

It drove me nuts for awhile.

Once you get OC to a setting you like you'll need to make script to run at your session
startup to avoid them resetting after you restart X or reboot.  In this instance it's a feature
not a bug, this keeps the system from repeatidly locking up if you enter bad values.

Search the forums for additional info on nvidia overlocking scripts.  :)

--Aaron

---

### Post by hardyn on 2007-03-22
what about running nvidia-config with gksudo?

---

### Post by hikaricore on 2007-03-22
> **hardyn said:**
> what about running nvidia-config with gksudo?

why in the hell would you do that?  the drivers are working properly, they're just
trying to increase framerates in a non-native game and overclock...

---

### Post by steevz on 2007-03-22
Even if I type it in and hit enter it doesn't work. Once I click apply it resets then back to default. ARRRG!

---

### Post by Eazy© on 2007-03-22
You could try to rename nvidia-settings.rc to nvidia-settings.rc.bak and then reboot. You find the file in /home.

---

### Post by steevz on 2007-03-22
Renaming the file and rebooting didn't work. Well, I didn't reboot, I hit Ctrl+Alt+Backspace. Imagine that is the same. Still no success.. anyone else?

---

### Post by Eazy© on 2007-03-22
check this out:
[http://www.ubuntuforums.org/showthread.php?t=387019](http://www.ubuntuforums.org/showthread.php?t=387019)

---


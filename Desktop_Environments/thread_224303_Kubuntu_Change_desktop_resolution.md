---
title: "Kubuntu: Change desktop resolution"
date: 2006-07-27
forum: Desktop Environments
---

### Post by MWAAAHAAA on 2006-07-27
Hi all,

I've recently upgraded to dapper and found myself unable to change the resolution of my desktop. Where can I change the desktop resolution?

---

### Post by Jhongy on 2006-07-27
If you haven't customised your xorg.conf, then you can type:

```
sudo dpkg-reconfigure xserver-xorg
```

You will be presented with lots of questions - just accepting the defaults for most of them should be fine.

When you get to the question about graphics drivers, select yours from the list.

When you get to the question about resolutions, you can scroll down the list and select the one(s) you want to be available with the spacebar.

Answer all the rest of the questions, and when it prompts you if you want to write out a new xorg.conf, choose yes. When you're done, restart the computer. The resolutions you selected should then be selectable.


If there are any problems, the configuration tool should have automatically created a backup of your old xorg.conf in the /etc/X11 directory.

You may still need to install your graphics driver.

---

### Post by MWAAAHAAA on 2006-07-28
Hey thanks for the answer but that's not what I meant. I can set up any resolution I want in my xorg.conf, and then change using ctrl+ or ctrl-, but that means my screen resolution changes, not my desktop resolution. So when working under kubuntu I would just right click the desktop, then click "Configure desktop..." and I would be presented with an option to change my screen resolution. But now this option is completely gone, which leads me to wonder "where did it go?". So, where can I find it in kubuntu?

Just in case you're wondering, I need this because my TV doesn't display output correctly in 1280x1024 desktop mode, which I need for my LCD. So I have to switch every now and again.

---

### Post by der_joachim on 2006-07-29
[Quote=man:xorg.conf]
Option "DontZoom"  "boolean"
              This disallows the use of the Ctrl+Alt+Keypad-Plus and Ctrl+Alt+Keypad-Minus sequences.  These sequences allows you to switch
              between  video  modes.   When  this option is enabled, those key sequences have no special meaning and are passed to clients.
              Default: off.
[/Quote]

Note that it only works for your keypad. I made the same mistake once. :)

---

### Post by MWAAAHAAA on 2006-07-29
> **der_joachim said:**
> Note that it only works for your keypad. I made the same mistake once. :)

Yes I know that it only works for the keypad, but I'm looking for a KDE dialog where I can change the resolution.

---


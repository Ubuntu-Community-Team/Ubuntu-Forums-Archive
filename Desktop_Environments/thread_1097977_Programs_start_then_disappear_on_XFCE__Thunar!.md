---
title: "Programs start then disappear on XFCE / Thunar!"
date: 2009-03-16
forum: Desktop Environments
---

### Post by Cyanaether22 on 2009-03-16
Hey, I'm not sure what is causing this problem, the xfdesktop or thunar, but in any case I was following this [topic]("http://ubuntuforums.org/showthread.php?t=977120") and so I ended up rebuilding Thunar... that seemed to solve the thunar issue but xfdesktop is a mystery. 

Now that I've rebuilt thunar, or for some other reason, xfdesktop now doesn't even show the wallpaper or the things on the desktop when I log in. It did at one point, however.

When I log into a failsafe Xterm, I can type thunar, and it'll start fine, and if I type xfdesktop it works as well. Neither give any error messages (xfdesktop gives me about 8 messages such as ** Message: Querying XINPUT extension, then ** Message: XINPUT extension found. none of these fail).

So I'm at a loss at the problem. Are there any logs I can look at? Thanks for any help. :)

---

### Post by Cyanaether22 on 2009-03-16
A little more puzzling info:

When in Xterm, I type xfdesktop, everything loads just fine and I can open windows, and most programs (audacity wasn't opening for some reason).

When in xterm if I type sudo xfdesktop, the desktop logs in as root, and the same problem as when I log into the full desktop environment: whatever windows I open just disappear right after a millisecond of being there.

I'm still getting no error messages from these commands.... I'll keep experimenting.

---

### Post by Cyanaether22 on 2009-03-16
Bad news! When running xfdesktop from xterm (no sudo), I thought everything was opening fine, but it turns out when I tried to open a .wav file, whatever program it tried to open appeared then disappeared.

What could be causing this?


also, when I just run "thunar" and try to open the wav file, same problem. appear and disappear.

---

### Post by Cyanaether22 on 2009-03-16
even worse news..... I downloaded PCManFM and ran that from the terminal, tried opening the .wav file and a .aup file too. audacity never even appeared, and the .wav player opened but then disappeared.

Please help, I'd really like to get my desktop/filemanager/whatever working.

---


---
title: "Weird color on videos"
date: 2006-02-21
forum: Desktop Environments
---

### Post by kybishop on 2006-02-21
Hi, i'm using xubuntu (xfce), and i've been having some weird issues with color inversion or something.

At first, everything will work fine; my videos off the net or whatnot will play perfectly with totem or mplayer. Then, randomly, I'll open a video, or try to play a file from the web, and the colors will be extrememly bright and almost all yellow tints.

I have no idea why it does this, and it's not like im doing anything different when it happens.

The only way I've been able to fix the problem is by ctrl + alt + backspacing and restarting X.
(Okay scratch that, it worked one time but now the colors or still weird after doing it agian. Going to restart my computer and make an edit under it to see if it works)

Any ideas of why this happens, or a quicker fix then restarting X when it does happen?

---

### Post by kybishop on 2006-02-21
Okay so i Just tried reboot, didn't work.

My colors on videos seem permenatally messed up.

Please don't tell me I have to re package x or something like that

---

### Post by kybishop on 2006-02-22
yep . . . still can't watch videos . . . threads on like page 5 . . . =9

---

### Post by ekravche on 2006-04-17
[QUOTE=kybishop]Hi, i'm using xubuntu (xfce), and i've been having some weird issues with color inversion or something.

At first, everything will work fine; my videos off the net or whatnot will play perfectly with totem or mplayer. Then, randomly, I'll open a video, or try to play a file from the web, and the colors will be extrememly bright and almost all yellow tints.

I have no idea why it does this, and it's not like im doing anything different when it happens.

The only way I've been able to fix the problem is by ctrl + alt + backspacing and restarting X.
(Okay scratch that, it worked one time but now the colors or still weird after doing it agian. Going to restart my computer and make an edit under it to see if it works)

Any ideas of why this happens, or a quicker fix then restarting X when it does happen?[/QUOTE]

I have the same problem. After having the OS running for a while and openning a few videos, eventually the video color get's messed up in Totem. Does anyone have a fix for this?

---

### Post by ekravche on 2006-04-17
[QUOTE=ekravche]I have the same problem. After having the OS running for a while and openning a few videos, eventually the video color get's messed up in Totem. Does anyone have a fix for this?[/QUOTE]

Found a fix that seems to work. Just add the following lines to /etc/X11/xorg.conf
> 
Section "Device"
    Identifier  "Radeon 9800 XT"
    BusID      "PCI:1:0:0"
    Driver      "fglrx"
[B] Option "VideoOverlay" "on"
 Option "XaaNoOffscreenPixmaps"
 Option "RenderAccel"[/B]
EndSection


That seems to work. I could be wrong though, what could have fixed this problem temporarily was doing a secondary logon and then switching from user1 to user2. Hopefully adding the Option lines will fix it. The original link with a similar problem can be found here [http://ubuntuforums.org/showthread.php?t=20601&highlight=totem+color]("http://ubuntuforums.org/showthread.php?t=20601&highlight=totem+color")

---

### Post by juicybananahead on 2006-04-29
Hi, I'm having exactly the same problem (saturated brightness in videos after I've played a few) but I'm not sure I want to add those lines to my xorg.conf because I'm not using an ATI card - my display "card" is part of the Mobile Intel 915GM Express Chipset. Any ideas? I don't want to break X or start something smoking...

// Dave

---


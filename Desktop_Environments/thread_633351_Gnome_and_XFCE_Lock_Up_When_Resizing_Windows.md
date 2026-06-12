---
title: "Gnome and XFCE Lock Up When Resizing Windows"
date: 2007-12-06
forum: Desktop Environments
---

### Post by CornChowder on 2007-12-06
While using the Xubuntu (Gutsy) liveCD, I found that when I tried to resize any window, the whole system would lock up. Ctrl-Alt-F2 wouldn't get me to another terminal, Ctrl-Alt-Del would not respond; the system was truly frozen. Assuming that this was just a livecd issue, I attempted the install anyway (w/o resizing a single window throughout the entire process), but found that the problem persisted even after the install.  From there I decided to try and see if I had better luck with the Gnome-based Ubuntu (Gutsy) livecd, and found that it still crashes just when resizing a window.

I have been using Kubuntu (Dapper) on my other hard drive for quite some time and don't encounter this problem -- does this experience sound familiar to anyone?

---

### Post by ajgreeny on 2007-12-06
Sounds like a compiz problem to me so go to System->Preferences->Appearance and in the Visual Effects tab chose None and see if that helps.  Your graphics card may be good enough in theory but perhaps not really good enough in practice to use the desktop effects of compiz-fusion, which are switched on by default if the card can do so, but may cause problems in some cases.

---

### Post by CornChowder on 2007-12-06
> **ajgreeny said:**
> Sounds like a compiz problem to me so go to System->Preferences->Appearance and in the Visual Effects tab chose None and see if that helps.  Your graphics card may be good enough in theory but perhaps not really good enough in practice to use the desktop effects of compiz-fusion, which are switched on by default if the card can do so, but may cause problems in some cases.

Yeah, I was kind of hoping that's what the problem was, only when I actually do click on the Visual Effects tab, I find that "None" is chosen as the default.  My graphics card is only an on-the-motherboard SiS card; the motivation for trying to run Xubuntu first was to try to get away from any of the high-end graphics.

---

### Post by tomanytoremember on 2007-12-06
I used Feisty for a couple weeks, and then about a week ago did a fresh install of Gutsy.  I have been resizing windows like mad up till this point.  I'm trying to make the switch to Linux from XP and really have fallen in love with the ability to alt-click move and alt-right/left click to resize windows. xD

Within the last 30minutes I have encountered 2 hard lock ups and 1 reboot from resizing a shell terminal.  I was using alt-left/right click all 3 times, haven't tried any other method yet.

I can't remember anything that I have changed recently.  I do remember earlier today I updated through the update manager and there was a listing "compiz" under the label of "backports".  Doesn't make sense that this would cause a problem on an iso image however =\

Not sure what to do about it...  If anybody has any suggestions or anything they'd like me to try just let me know what I can do!

---

### Post by tomanytoremember on 2007-12-07
I'm begining to believe that it has more to do with my terminal than windows in general...  Just happened to me 2 more times but I was simply typing in a shell.  And again when I just tried to launch a Terminal just now...  :'(  WTC?  Might try another shell for now?  Don't really understand what the difference's are between the lot however...

---


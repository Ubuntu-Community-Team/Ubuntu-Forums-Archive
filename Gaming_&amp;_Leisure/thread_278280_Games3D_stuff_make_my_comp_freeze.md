---
title: "Games/3D stuff make my comp freeze"
date: 2006-10-16
forum: Gaming &amp; Leisure
---

### Post by voided3 on 2006-10-16
Hello all. I have had some problems with playing 3D games and my comp. I am running Ubuntu 6.06 with an AMD Athlon XP @ 1.36ghz, 1.0 gig of ram, and an ATI Radeon 9250 w/256 of RAM (an HIS Excalibur build). Whenever I play the games TORCS or Trigger, they work beautifully... for ten seconds, then the computer becomes completely unresponsive, forcing me to reboot. I noticed when I was looking at the screensavers, too, that the 3D ones had a similar effect if i left the preview window open for more than 10-20 seconds, except my mouse cursor would still move (not that it could do anything anyway). I seem to be having difficulty with 3D rendering, and I tried installing the ATI drivers, but they made the games unbearably slow and warped the colors. I also have Win XP Pro on here and I can play games like Flat Out 2 or use visualizers like R4 on or near full settings perfectly fine for hours. Any possible solutions? Thank you!

---

### Post by pay on 2006-10-16
I don't think that Ati support the 9200 series anymore. Have you tried the radeon drivers?

---

### Post by kelmer on 2006-10-16
double check if you've really got the driver to work. It happens very often that you think you do but you don't.

type "fglrxinfo" on the terminal.

check that you have ATI as a result. if something like "mesa..." appears, go here:

[http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue]("http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue")

---

### Post by voided3 on 2006-10-16
When i enter "fglrxinfo" I get a "bash: command not found", but i'll check out the link. Thanks!

---

### Post by voided3 on 2006-10-16
Alright, i tried the link, but i get the same results. Any other ideas? Thanks

---

### Post by jdunn on 2006-10-16
Never tried Compiz.  I tried the Kwin compositing manager and it also worked perfectly, except when playing opengl games.  I've read that because the compositing managers are new, it will be a little while before these bugs are fixed.  Personally, I will go with Compiz but, only with my next Kubuntu install, which will have xorg 7.1+ and the latest Nvidia drivers that support xorg 7.1.

---

### Post by handy on 2006-10-17
I was also wondering if **Compiz/XGL** was the culprit?  My machine was perfectly stable until I installed that combo'.  I very quickly removed them.

---

### Post by voided3 on 2006-10-17
Hello all. After a failed series of first experimental attempts, i finally got teh video card up to snuff. I used the Wiki guide (which i have bookmarked and backup the bookmark of..) with much success. In TORCS I get about 80 FPS, very nice. Thank you very much, forum geniuses!

---


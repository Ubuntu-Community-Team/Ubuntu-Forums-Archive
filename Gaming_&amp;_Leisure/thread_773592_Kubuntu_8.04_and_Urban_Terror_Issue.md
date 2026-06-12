---
title: "Kubuntu 8.04 and Urban Terror Issue"
date: 2008-04-29
forum: Gaming &amp; Leisure
---

### Post by astepintothedark on 2008-04-29
First off, I'm fairly noobish to linux. I've been able to lurk around the forums finding solutions to problems, but now I'm stumped.

I recently upgraded from kubuntu 7.10 to 8.04 and everything seems to be running smoothly (with the exception of kde 4 which seems too buggy for me). 

Well now I cannot run Urban Terror. I was able to run it quite nicely in 7.10 but not under 8.04. What happens is that I run the program and UT appears to run, then the screen gives me an image of the upper-left portion of my desktop that looks like it's been zoomed in on. The mouse is disabled in this instance and all I can do is use the keyboard. At this point I have to restart X.

I've tried reinstalling the video card drivers for my nvidia 7 series, but this hasn't helped. I've also tried running UT in a seperate X, but then I get error saying "Couldn't fin matching GLX visual".

Any suggestions?

---

### Post by asemblR on 2008-04-29
astepinthedark,
please post Your Xorg.o.log and then run "glxinfo" and copy the results and pot it here.
also Machine info, video card, sound crd, etc....

---

### Post by astepintothedark on 2008-04-30
> **asemblR said:**
> astepinthedark,
please post Your Xorg.o.log and then run "glxinfo" and copy the results and pot it here.
also Machine info, video card, sound crd, etc....

I was actually able to resolve the issue by doing a fresh install of hardy and through [here]("http://ubuntuforums.org/showthread.php?t=773122&page=3&highlight=nvidia+hardy").

Thanks though.

---


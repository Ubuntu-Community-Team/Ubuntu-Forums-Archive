---
title: "time for clean reinstall?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by hellfried on 2006-08-29
just wondering how often people in this forum have to do a clean reinstall of ubuntu and after how long? i have been using dapper for the past 1 month and i have installed a fair bit of software onto it eg amarok, compiz/xgl, ati drivers to enable 3d acceleration, gtkpod, kiba dock, various firefox plugins and multimedia codecs, flash player, vlc etc. 
lately i ahve noticed that dapper has been very flaky. random automatic logouts (to the login screen even when there are programs running), sudden closure of firefox while browsing, random loss of audio when playing video on youtube, loss of ability to transfer mp3s from hd to ipod in amarok (although gktpod still works), slowing down of compiz/xgl, loss of wireless connection with my ibook and the list goes on. 
time to reinstall?

---

### Post by Jussi Kukkonen on 2006-08-29
Four machines running, the first one dist-upgraded all the way from Hoary (could have been Warty, can't remember anymore). No reinstalls, no stability problems.

Files in /var/log/ will probably have some hints on what happens when X crashes, network connection is cut, etc. ...

EDIT: Yeah, my home desktop machine is originally Warty. Time flies.

---

### Post by matthew on 2006-08-29
> **hellfried said:**
> just wondering how often people in this forum have to do a clean reinstall of ubuntu and after how long?
Well, I can't comment on your specific situation, but I can say that I have one computer that I have upgraded from hoary to breezy to dapper without ever reinstalling from scratch and it is still running smoothly and with good speed. The only times I have ever done a complete reinstall of Ubuntu was because of
1) user error resulting in massive problems (don't do things you don't understand...I did learn a lot, though--that's for another thread)
2) hard drive failure

---

### Post by wagerrard on 2006-08-29
I've never had to do a 'clean reinstall' of any Linux distribution. Ubuntu should run fine for years.  That said, there's a reason a lot of software isn't in the offical repository. Unless you're having hardware issues, one or more of those program/libraries you've installed is probably the culprit.  Try removing some of them.

---

### Post by hellfried on 2006-08-29
> **Jussi Kukkonen said:**
> Four machines running, the first one dist-upgraded all the way from Hoary (could have been Warty, can't remember anymore). No reinstalls, no stability problems.

Files in /var/log/ will probably have some hints on what happens when X crashes, network connection is cut, etc. ...

EDIT: Yeah, my home desktop machine is originally Warty. Time flies.

which file am i supposed to be looking at? there are so many files in /var/log/.

---

### Post by PPAAUULL on 2006-08-29
I have been running Ubuntu for a year and I have reinstalled many times, however that is only because I play around with the settings and often mess it up so much that it is hard to fix. I know that when I do a clean install it can take me days because of all the stuff I need to get back on it and reconfigure. I would say that if you aren't up for that then just leave it.

Paul

---

### Post by Jussi Kukkonen on 2006-08-29
> which file am i supposed to be looking at? there are so many files in /var/log/.

Well, that depends on the case. *messages* is a good general guess. When you encounter a problem, you can also take a look at the timestamps of  files in /var/log/, and read the end of the files that were changed in the last couple of minutes.

---


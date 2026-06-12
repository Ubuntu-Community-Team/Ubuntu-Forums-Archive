---
title: "Need help dual booting with SuSE 9.3"
date: 2006-06-04
forum: Desktop Environments
---

### Post by greghill on 2006-06-04
Well I finally dumped Windows altogether on my main box, and replaced my main drive (hda) with Ubuntu 5.10 running Gnome. On the second drive (hdb) I have installed SuSE 9.3.
When I had Windows on hda and Ubuntu on hdb I had Ubuntu configured so that it could read Windows XP with no problem. Now I can't get Ubuntu to see SuSE on the second drive. Anyone have the exact code to chown hdb so I can read it from Ubuntu? Seems to be an ownership problem, and I can't seem to get the syntax right.....:( 
This forum never seems to let me down. Thanks!!!
Greg

---

### Post by jones_jj on 2006-06-04
I believe the syntax you may want is **sudo chown -R <username> /<directory>**.

Also something to take note, will Ubuntu be able to read the filesystem that you used for Suse?  Did you use ext3 for both Ubuntu and Suse?

---

### Post by greghill on 2006-06-04
Thanks for the code. Managed to change ownership OK, but you were right.... appears Ubuntu unable to read SuSE file system. Funny though, works the other way around. SuSE has no trouble reading Ubuntu !?
(SuSE user Reiser fs) though I have to admit, although I've been a Linux user for the past few years, I have a lot to learn about file systems (and Linux in general for that matter:???: )
I'm in "learn as you go mode" and at age 56, I still have a bit of time to learn. It's actually more fun than work! Again, thanks!

---


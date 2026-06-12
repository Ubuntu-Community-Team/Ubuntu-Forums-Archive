---
title: "trying to overwrite xyz which is also in package uvw"
date: 2006-07-11
forum: Desktop Environments
---

### Post by sup on 2006-07-11
I self compiled Rhythmbox 0.9.5 (I want tag editing) and installed it with checkinstall. Now I heard about graphical frontend to cron and wanted to try it out, so I
```
sudo apt-get install gnome-schedule
```
bit it gave me this:
dpkg: error processing /var/cache/apt/archives/gnome-schedule_1.0.0-1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/var/lib/scrollkeeper/es/scrollkeeper_cl.xml', which is also in package rhythmbox-0.9.5

So it would not install. Now, I can live without it, but this is not the first time something similar happened to me and I am not very clear what it means. Is the problem somewhere in the source code od rhythmbox, or with my packaging methods (rather straightforward ./configure --some options make sudo checkinstall) or is the problem elsewhere? And is there a way to solve this besides going back to Ubuntu's version of rhythmbox (now I do not expect that version to conflict with another ubuntu package)

---

### Post by sup on 2006-07-11
Hm, so i recompiled gnome-scheduler with --disable-scrollkeeper and now it works, but I would really like to know if it was rhythmbox's or my fault:-/.

---

### Post by sup on 2006-07-11
Hm, so i recompiled gnome-scheduler with --disable-scrollkeeper and now it works, but I would really like to know if it was rhythmbox's or my fault:-/.

---


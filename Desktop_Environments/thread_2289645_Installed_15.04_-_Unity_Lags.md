---
title: "Installed 15.04 - Unity Lags"
date: 2015-08-05
forum: Desktop Environments
---

### Post by gerowen on 2015-08-05
I was running Ubuntu 14.04 LTS and decided I wanted to upgrade my laptop to 15.04 so that I could take advantage of the newer software versions, newer kernel, systemd, etc.  In 14.04 Unity pretty much ran without a hitch.  I did a clean install of 15.04 after backing up my personal files, and although I'm generally pretty happy with it, I've noticed one thing that's particularly annoying.  Whenever the system is under any kind of load, such as installing software, extracting a large archive, etc., the entire Unity desktop comes to a grinding halt and/or becomes very jittery.  The mouse will freeze, the menu will take for EVER to open up, etc.  Games in Steam run great, and most things work as they should, but in 14.04 I could perform these tasks without the entire desktop interface locking up.  Even CTRL+ALT+F1 takes a good 30-45 seconds sometimes to shoot me to a background terminal to see what in the world is eating up all my cpu time.

I've generated a hardinfo report with all the relevant information which can be viewed here: [https://dl.dropboxusercontent.com/u/6017319/hardinfo_report.html](https://dl.dropboxusercontent.com/u/6017319/hardinfo_report.html)

Has anybody else noticed this?

---

### Post by gerowen on 2015-08-05
I THINK I've narrowed down the problem.  I've been recovering my personal files from backup over the past several hours.  I have 4 GB of RAM, and some of these tarballs are 10+ GB in size, I've got almost 30 GB of just music, so extracting a tarball several times the size of my available RAM could slow things down a little, :P

Thanks to badbodh for pointing out low RAM as a potential culprit in the IRC.

---


---
title: "nautilus cpu usage problem with autofs (Intrepid)"
date: 2009-01-17
forum: General Help
---

### Post by flar on 2009-01-17
After installing Ubuntu 8.10, nautilus cpu usage spikes to 99% every few seconds.  This happens 24/7 and has been going on for weeks (I haven't had time to look into it). Restarts don't help.

After some investigation this morning I found the cause but have no solution.

I use autofs to mount several remote directories. This computer has been running ubuntu for several years with the same setup, no problems.  

The cpu usage spikes stop if I stop the automounter

/etc/init.d/autofs stop

Nautilus, autofs and the mounted directories all work fine--no problems there.  I was just wondering if anyone else is experiencing these cpu usage spikes? I haven't figured out how to stop this.  Any ideas?

---

### Post by flar on 2009-01-18
Anyone using autofs on ubuntu 8.10?

It's like nautilus keeps polling for something when using autofs.  99% cpu every few seconds is pretty serious.

---

### Post by flar on 2009-01-18
I've had a chance to look into this now, apparently nautilus keeps checking the automounted directories.  They should only be mounted when someone tries to access them.  I had the timeout set low, so nautilus would check the directories, then unmount them a few seconds later.  Each unmount drove cpu usage up to 100%.  

My temporary solution is to increase the timeout to 3000 seconds.  I never had this problem with earlier versions of gnome and ubuntu.  Sadly, this and many other problems (eg: sound problems, window manager draw problems, crashing apps) in recent distros lead me to believe that quality control is on the decline in the linux world, I'm not sure that we can tout stability as an advantage anymore.

---

### Post by jrennell on 2009-01-28
I've been having a similar problem with a PVR computer I have since I upgraded to 8.10. People in the apartment use it to connect to network shares (all samba that I know of) and if we leave them connected, randomly nautilus starts using 100% of the cpu. I'm going to take a look into this autofs problem you've had. What kind of specific changes have you already made to reduce this problem? I normally let that computer run folding@home, so when nautilus starts stealing cycles it's time to find a remedy.

As a side note to your comment about stability, there's a difference between poor-behaving applications such as nautilus and the stability of the Linux kernel, which is what people like to tout. Distributions such as Ubuntu Desktop (especially the non-long-term-support versions) don't test things as thoroughly as some other distributions. They do this to try to get the latest and greatest "stable" versions of apps and other packages to end users. Those new versions are normally released without full QA that a commercial application would get because they're open source and probably don't have those kinds of resources available, and bugs creep in and out of each build. My favorite part about free software is if it doesn't work for you, you can always get your money back :D.

---

### Post by Glenhawk on 2009-02-23
I think I have had a similar/related problem.
With both 8.04 and 8.10 I encounter lockups of nautilus if the fileserver that I automount is turned off. 
It baffled me for ages, intermittently booting up to a usable window would take forever and then occasionally I would get lockups (lose control of the menus and file browsers) when trying to browse a CD or other attached disk (internal or external) and sometimes even when saving an email attachment. I thought it was related to using nvidia dual x screens but I have since upgraded to a single 23" LCD and still get the problems.
I realised on the weekend that it seems only to happen when my fileserver is powered down. As soon as the fileserver is running it seems my PC boots and behaved normally.
I specifically decided on using autofs because I would have the fileserver offline at times but now it seems that having the server off causes more problems. It is getting to the point where I will have to run with an always on server just to prevent mounting issues.

---

### Post by sej7278 on 2009-02-23
i have the same problem with fedora10 and centos 5.2 so its a nautilus/gnome/autofs/nfs bug, not anything ubuntu-specific.

i've disabled autofs for now as nautilus is unusable when the fileserver is offline.

someone in another thread said its because of bookmarked nfs shares which nautilus keeps polling, i might look into that.

i switched to nfs v4 which seems to be a bit more stable than v3, you don't get all those "server not responding" errors in dmesg at least and nautilus doesn't seem to grey out as much on large transfers.

i might drop nfs though as from some benchmarks i did its no faster than scp and about half as fast as ftp, so i might try benchmarking samba or moving to fuse-sshfs (with null encryption perhaps) instead.

---


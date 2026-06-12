---
title: "Clearing up space on harddrive."
date: 2008-12-30
forum: General Help
---

### Post by linuxlover15 on 2008-12-30
Since I am so used to Windows to where I can right click on HardDrive, and go to Properties and click Disk Cleanup or whatever, I am a little confused as to how I can free up space on my HDD on Ubuntu. I've typed in "sudo apt-get autoremove" in the Terminal, but it only helped a little bit, and I need to do some real "damage" (not really) when it comes to clearing space on my HDD. So can someone help a poor noob clear up space on his HDD?

---

### Post by exploder on 2008-12-30
A command I use often is, sudo apt-get clean.

This cleans things up a little.

---

### Post by xjcannonx on 2008-12-30
You could try sudo 'apt-get autoclean' but that probably wont help much to be honest, I would go to synaptic and remove any packages I know i don't need, like extra things here or there i.e. rhyme, cairo-dock, etc...Make sure you don't remove anything you need for system or functionality, You could also remove the preloaded games i guess

---

### Post by cdtech on 2008-12-30
Old downloaded files you would have to clean out yourself. If you need to clean out your /boot directory it's best to use the "Synaptic Package Manager" and remove unused kernel images.

You may want to look into "deborphan" and "localepurge" to help with cleaning your system.

---

### Post by exploder on 2008-12-30
I strongly advise using care with deborphan, it sometimes suggests removing packages that are needed.

---

### Post by xjcannonx on 2008-12-30
although you may not want to remove all the old kernels and leave maybe 1 around just in case something happens to the latest one you are using

---


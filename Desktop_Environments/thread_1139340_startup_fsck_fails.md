---
title: "startup fsck fails"
date: 2009-04-26
forum: Desktop Environments
---

### Post by pyroguysf on 2009-04-26
Just for some background info I did a clean install of Intrepid recently and upgraded to Jaunty. I then made a separate home partition on a 500GB drive all by itself, leaving my 150GB WD Raptor for my boot drive using [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) more or less as a guide, since I was using 2 drive and didn't have to edit partitions, just make a new one, and added "/dev/sdb1 /home ext3 nodev,nosuid 0 2" to the end of /etc/fstab.

However it appears that my system is trying to do the routine filesystem check at boot, but it brings me to a shell saying:

/dev/sdb1 is mounted. e2fsck: Cannot continue, aborting.

fsck died with exit status 8

And goes on to tell me it failed and created a log file and that I should fix it manually. From what I gather, it just seems that it can't scan sdb1 (my 500gb home drive) because it's already mounted, probably something having to do with the edit to /etc/fstab. What kind of workaround do I have so that the mounting of the home drive doesn't interfere with the filesystem check? Or am I completely off?

If I exit the maintenance shell it puts me in and try to login it tells me something about my home directory not existing and wanting to use root's home. Then it says something about $HOME/.dmrc being ignored. I changed the permissions like it said in the guide, but they don't stay put it seems.

---

### Post by pyroguysf on 2009-04-27
Well..umm, nevermind. I didn't add any new drives or partitions or anything of the like, but it decided to change my 500GB home drive to sdc instead of sdb. I just changed the line in fstab to the new value and it worked. Hopefully it doesnt change letters around on me anymore.

---


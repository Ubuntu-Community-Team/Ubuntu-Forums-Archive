---
title: "HFS+ External Drive...   R/W sharing?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by raintheory on 2006-09-13
Hey all, bear with me as I am fairly new to Ubuntu...

  Here's my issue:

  We have a 500Gb external drive that is formatted as HFS+ and was previously connected to my Toshiba laptop (WinXP using MacDrive) via firewire and shared on the network (although sometimes connected directly to our G5 for some applications).  

  I have since set up the laptop to dual-boot Ubuntu, and would like to have the same read/write access to the drive and be able to share it on the network.  Currently it mounts as read-only, but I am unable to write anything to the drive...

  Any suggestions on how I should do this?  I have done a little searching in the forums here but most of the HFS+ info I have found relates to PPC installs, or getting the drive to mount...  neither of which actually apply to my situation since I am not on a PPC and the drive actually mounts fine, I just need to be able to write to it locally and over the network.

  The drive has about 300 or so gigs of data on it so pulling the data off and reformatting isn't exactly an option at the moment.

  Thanks in advance!

---

### Post by nrwilk on 2006-09-13
I'm in the exact same situation.

My firewire drive has four partitions.  When I plug it in, the three HFS+ partitions are all mounted read-only, and the ext3 partition is mounted read/write.

It would be great to find a solution.

---

### Post by raintheory on 2006-09-16
Anyone have any ideas?

I have disabled Journaling on the drive but still mounts read-only..

Any help/suggestions greatly appreciated!  

Thanks

---

### Post by raintheory on 2006-09-17
Just an update,

I connected the drive to our G5 and it was showing that the drive was not journaled...   I actually enabled journaling and then disabled it.  When I connected it to Ubuntu again I set permissions and I can now write to the drive.

---

### Post by raintheory on 2006-09-27
Oddly enough, now the drive is read-only again...   It was writable yesterday, but now today its giving me errors saying it is read-only.

I haven't installed any updates or done anything today that I think could cause this...

Anyone have any ideas?  Any way I can get write access again on this drive?

---

### Post by raintheory on 2006-10-15
Okay guys here is an update and fix to my situation:

Turns out according to dmesg the drive at some point was not cleanly unmounted, and that seems to cause the drive to be mounted read-only from that point on. 

Anyway I followed this and solved the problem: [http://www.debian-administration.org/users/lee/weblog/21](http://www.debian-administration.org/users/lee/weblog/21)

---

### Post by raintheory on 2006-11-01
Just for reference the aforementioned fix works on Edgy as well.

---

### Post by lowracer on 2006-11-17
I'm in the same boat.  Firewire drive formatted on a mac that only mounts up read-only on Linux. 

Tried the fix at the debian-administration site but the make threw a whole bunch of errors.  I'm just going to format the drive on the mac as a UNIX filesystem and hope that works.

---

### Post by raintheory on 2007-03-30
I get errors now on Feisty...   

Back to square one I guess.

:(

EDIT: This method works for Feisty: [http://www.ubuntuforums.org/showthread.php?t=392287](http://www.ubuntuforums.org/showthread.php?t=392287)

---


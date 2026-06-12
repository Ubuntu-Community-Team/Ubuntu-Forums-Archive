---
title: "Install Issues"
date: 2007-06-30
forum: Colorado Team - US
---

### Post by tnats on 2007-06-30
Hey folks,

I'm having all sorts of issues trying to install an Ubuntu server with software raid 1 on two disks.

I first installed 7.04 and created a raid 1 system using two disks with no  problem. It was very easy. Then, I realized the software I wish to install (plesk) requires 6.06 so I burned the .iso and installed. After the reboot, grub gave me the famous: "file not found" error. I tried to go in and set /dev/sdb to be bootable (ie. grub, device /dev/sdb; root(hd0,0); setup(hd0) but it said the partition does not exist. I played with it for a few more hours and gave up.

Next, I threw in a CentOS disk because I can get software raid running on that with no problems but after the install, I get a "Grub error 17". 

Is there something I'm missing here? In each install, I chose manual partitioning and wiped out any previous partitions and file systems. So, do I need to clear out my MBR on this machine? It can't be this hard to get this done. Thanks for any advice/tips you can give me. I'm all google'd out and have tried many suggestions from those sites. 

-Tom (Littleton)

---

### Post by Tea4all on 2007-06-30
Ubuntu may detect the wrong drive sometimes.  Try this to reinstall grub correctly [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by FunnyLookinHat on 2007-06-30
Tom,
I had a similiar error and it basically resulted from Ubuntu thinking that hd0 was really hd1, so I had to manually edit my /boot/grub/menu.lst file and then run "sudo grub-install hd0" all over again...

Definitely check the above link for troubleshooting grub.  I think your system will work fine, you just have to make sure grub is looking in the right places for a kernel to boot.

Also, why can't you use 7.04?  Is there a specific version of that program only available on 6.06?

Cheers,
David

---

### Post by tnats on 2007-07-01
Ok, I figured it out. I reinstalled and made / sda1 and swap sda2 and it works fine now. I had it the other way around before. All the instructions I've seen say nothing about this. 

I do understand that any machine will read sda1 first so it makes sense to me now, just don't know why I didn't see it posted any where.

Thanks for the help.

---


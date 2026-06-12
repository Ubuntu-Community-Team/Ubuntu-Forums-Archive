---
title: "Home and Swap Encryption - Info needed"
date: 2014-03-23
forum: Desktop Environments
---

### Post by zongosaiba on 2014-03-23
Greetings to all, 

I got my first major issue using Ubuntu 14.04. Just for the context, I have only been using Linux for the past three weeks only :) 
I encrypted my home folder when I installed Ubuntu on my rig with LVM.  I booted into my rig for about three weeks and a few days ago, I suffered from an issue that seemed to have been around for a while:
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/475936](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/475936) (a version of it).  
The errors I got: 
*device-mapper: rename ioctl on cryptswap1 unformatted failed: device or ressource busy 
*The disk drive for / is not ready yet or not present.  Continue to wait; or press s to skip mounting or M for manual recovery
The result of those errors was that I could not log in anymore after the decrypting the folder.  I could not get to the screen where I would be ask for my user password. 

The fix I applied: 
I created another swap partition
#fallocate -l 512m /swapfile1.swp
Format:
#mkswap /swapfile1.swp 
Change the permissions: 
#chown root:root /swapfile1.swp 
#chmod 0600 /swapfile1.swp 

I commented out in /etc/fstab the mapper
#/dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0
#/dev/mapper/cryptswap1 none swap sw 0 0
/swapfile1 swap swap defaults 0 0

Then I was able to log into my Desktop and use my rig again.  

The question(sss) Sorry more than one Question as I am a complete Noob: 

I am now in need of some explanation as far all the encrypted folders. I am attaching crypttab, fstab and  '/proc/swaps' so you guys can have a clear picture of the setup. 
*'proc/swaps' show that /dev/dm-3 is in use 
*crypttab is showing /dev/dm-2 being in use
So this is the first inconsistency that I see and the first question I have. Why is it that swap and crypttab are not using the same partition ?  

You will see in /etc/fstab:
/dev/mapper/ubuntu--gnome--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
Why is it using two swap partitions ? Those two partitions were set up during the install process. I did not set that up. 

When I boot with the partition I created /swapfile1, I do not get the error message:
*The disk drive for / is not ready yet or not present.  Continue to wait; or press s to skip mounting or M for manual recovery. 
If I boot with the old set up created during the install process, I always get the error message mentioned  above. Why is that ? I am afraid that my problem will come back and I will again be locked out.  I have my life in this PC :) Is there a way to safely get rid of the error message above ? I have trolled the internet and found some supposed fix, but I am afraid to try them. 

Recap:
All is working well. Eventhough I did read a lot of man page and how to(s), I still don't get most of it and therefore I would be looking for some explanations (simple wording if possible) to go to bed less stupid :) Of course, if you see any improvments possible in my setup, feel free to let me know. 

PS: You will see that I am using 'zram'. It has not affected the rig in any negatives ways and I don't it had anything to do with the bug I suffered.

Its a long post and I apologise for that. I thank you all for taking the time. 

zongo saiba

---

### Post by zongosaiba on 2014-03-23
So, I have removed the swap partitions in 'fstab' that were created during install process by commenting them in. 
fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--gnome--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=735f6250-439d-4228-ade4-8ec133c73a74 /boot           ext2    defaults        0       2
# /dev/mapper/ubuntu--gnome--vg-swap_1 none            swap    sw              0       0
# /dev/mapper/cryptswap1 none swap sw 0 0

I have commented out the line 'cryptswap1' in /etc/crypttab 
crypttab:
sda5_crypt UUID=e0d9b8f4-a482-4fcf-814c-b10da8408dab none luks
#cryptswap1 /dev/dm-2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

I am left with two partition:
sda5 (swap) - UUID=e0d9b8f4-a482-4fcf-814c-b10da8408dab
sda1 (boot) - UUID=735f6250-439d-4228-ade4-8ec133c73a74

I have rebooted my machine a couple of time and no issue. The error message '/dev/mapper/ubuntu--vg-swap_1 is not ready or not present....' is not showing anymore. The system feels a lot snappier and the boot time has decrease. Is this possibly related ? 
When I run:
cat /proc/swaps I get only the 'zram' pool created. Its normal since I have it installed. If you have a look at the attached screenshot in my previous post, I had  an extra line '/dev/dm-3'. Is it bad Doctor ? 
Finally, when I run 
# free:
Swap:      8174688          0    8174688
Which leads me to think that this setup is more correct than the ones before. I am really not sure. 

_My Guess: _

I encrypted my home folder with a disk encryption during install. I think, this was the start of all my troubles and this is why I had swap encrypted a couple of times. The morale of the story is that if you encrypt your disk, you might not need to encrypt your home folder ? Am I correct in saying that ? 

_1000$ Question:_

Can I safely delete the two partitions below to get back the space ? 
cryptswap1 /dev/dm-2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
 /dev/mapper/ubuntu--gnome--vg-swap_1 none

---


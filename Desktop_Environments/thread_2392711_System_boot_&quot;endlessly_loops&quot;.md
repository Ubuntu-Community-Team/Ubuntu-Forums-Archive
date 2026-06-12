---
title: "System boot &quot;endlessly loops&quot;"
date: 2018-05-24
forum: Desktop Environments
---

### Post by hmag on 2018-05-24
Hello, 

I have been using a (16.4, I think) LTS since a long time with no major issue.
Yesterday, my system did not boot up to XFCE

It seems to "endlessly loop" after the "/dev/dsa8: clean (X blocks/Y)" message then I never reach the XFCE login screen

Other détails:
- "Recovery mode" boot works well and I could backup my home dir
- in recovery mode I could do the following:
  . check of filesystems and all has been reported as OK
  . checked and cleaned packages

I would like to find a solution to make it boot instead of overwriting my current OS release with a new one.
Can you please guide me a little bit in this process ?

Thanks
HMag

---

### Post by oldfred on 2018-05-24
The fsck on boot, often does not do a full file check. I might try that first.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by hmag on 2018-05-27
I ckecked with appropriate e2fsck before posting the above, my disks were all sane. 
I have been bothered and replaced 16.4. by a fresh 18.4


):P< To see all files, type ls -lR / > ):P

---


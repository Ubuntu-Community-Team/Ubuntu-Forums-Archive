---
title: "Can't access data after ddrescue"
date: 2009-02-06
forum: General Help
---

### Post by footygeek on 2009-02-06
Can anyone help?

I was trying to recover data from one of my laptops by using ddrescue from the ubuntu remix rescue cd as windows won't boot up on laptop.

I borrowed a external hard drive off my father-in-law which already had some data on which he'd used to save his photos.

I type 'ddrescue /dev/sda3 /dev/sdb1' and it seem to work and copy data to USB external drive.

However now when I try and access the drive I get the same error as on the laptop, 'Unable to mount'.

I have also tried accessing it through an op XP laptop but it doesn't show.

I fear I may have overwritten the original data which was on the drive and that the data I have copied is corrupt not the hard drive as I thought.

Can anyone suggest how I can look at the external hard drive and data on it, and if I can recover the data that was there before 'ddrescue' run as I didn't back this up?

Thanks for your time.

---

### Post by bumanie on 2009-02-06
Try making a directory to mount the external drive to > sudo mkdir /mnt/rescue > sudo mount -t /dev/sdb /mnt/rescue NB:- /dev/sdb may be designated /media/sdb to find out > cat /proc/partitionsYou should be able to find /mnt/rescue in /home and view the files. Also, it is likely you have overwritten the original content of the external drive if you did not send the dd output to a directory - you may be able to recover the original content with a program like photorec which is part of testdisk - > sudo apt-get install testdisk to start photorec > sudo photorec

---

### Post by footygeek on 2009-02-10
Sorry for the delay in posting again, I have managed to get all photos and music I can off the portable drive using 'photorec'.

However when I try the mount command, it didn't work. I tried the following and it came back with this:-

> footygeek@footygeek-laptop:~$ sudo mount -t ntfs /dev/sdb1 /mnt/rescue 
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


Any idea what this means. and is there anyway I can get round it or 'undelete' the contents back before I borrowed the drive.

---

### Post by caljohnsmith on 2009-02-10
Do you have a Windows Install CD? If you don't, you can download and use a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). I would recommend booting either the Install/Recovery CD, go to the "recovery console", and do:
```
map
```
That will show the drive letters of all partitions, so find the drive letter for your sdb1 USB drive partition, and then do:
```
chkdsk /r X:
```
Replace X with sdb1's drive letter, and run the chkdsk command as many times as it takes until it reports no errors. Then try mounting the partition again in Ubuntu and let us know the results. We can work from there if you want.

---

### Post by footygeek on 2009-02-21
Thanks for everyone's help.

I managed to get chkdsk /F running on crashed laptop and portable hard drive and could access the data.
However, as I feared I had over wrote the data which had been on the drive.

I have now managed to get my father-in-laws old laptop which has a duff motherboard and copied his data off there now.

The crashed laptop now has Ubuntu running on it but still not sure if the hard disk is ok.

Trying to create a dual boot for a Vista installation now.

All your advise has been very useful and once again thanks for helping.

---

### Post by caljohnsmith on 2009-02-21
It sounds like it would be good to check the health of the Ubuntu HDD to see if that might be an issue, so how about trying the following while you are in Ubuntu, and note the directions assume the Ubuntu drive is "sda", so change that if necessary:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so we can see the results.

---


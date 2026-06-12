---
title: "Removing GRUB loader...error 22"
date: 2009-01-17
forum: General Help
---

### Post by mukhul on 2009-01-17
First, I apologize if im posting this in the wrong area, if I need to go somewhere else, dont hesitate to redirect me. 

Also, I'm new to Linux so I've probably made some heinous mistakes...please bear with me. 

Heres the timeline of my problem. It's lengthy but I wanted to paint a clear picture.

1. Windows Vista Home Premium gets trojan virus. Take my Acer Extensa 5620 to OSU computer center where the virus cripples Vista while tech support is working on computer. =(

2. Recovery CD's I made when I purchased computer fail. miserably. Tech support guy (very nice guy btw) suggests linux. I'd been wanting to give ubuntu a spin for a while so I figured it was the opportune time. 

3. I have 2 70gig partitions. Tech guy manages to shrink C:/ and installs Ubuntu on the leftover space in new partition. (Other original partition is safely holding all my data and is left untouched)

4. I go 3 days running ubuntu. I like it very much BUT decide that I need to go back to Vista. (There were just too many issues with not being able to run windows as a student, plus I work in admissions and need to run office 2007 and connect to encrypted networks that dont like Linux. whatever.)

5. I shell out the $35 to have Acer send me new recovery CDs. I reinstall Vista on the original C:/. 

6. I decide I want to remove ubuntu (I didn't want to dual boot, I just wanted my computer back to the way it was.) 

7. UNDER ADVICE FROM TECH SUPPORT GUY: I go into partition editor in Vista and simply delete the partition that had linux, and then expanded the C:/ over the "unallocated space". 

8. I restart computer and get Grub loader error 22. =(

9. Searched google and these forums and found a few solutions...none that worked. I tried a recovery console CD (burned from the iso image) and opened the command prompt and tried all the "fixmbr" or "fdisk/mbr" suggestions that I saw, but nothing. 

10. Tried reinstalling Vista from Acer recovery CD's, thinking it would just wipe the entire C drive and reapply the windows boot loader, but didnt work. 

11. Reinstalled Ubuntu onto C drive. 

12. Now, C drive has ubuntu and vista. Ubuntu loads, Vista does not. 

13. Tech support guy is on vacation and new guy says that OSU wont service Linux system problems. =(

I probably made several mistakes but I'm not an idiot so I can follow whatever advice you can give me. I'm so frustrated. I just want to fix this. 

Thanks in advance.

---

### Post by caljohnsmith on 2009-01-17
It sounds like you just need to reinstall a Windows MBR (Master Boot Record). If your Vista install CDs have a command line available, you can do:
```
bootrec /fixmbr
```
And if the Vista CDs don't have a command line, you can instead download the [Super Grub Disk]("http://www.supergrubdisk.org") and use that to install a Windows MBR. That should get rid of Grub so you can boot directly into Vista.

---

### Post by mukhul on 2009-01-17
Thanks for the suggestion. I entered a command line from the recovery disk but when i entered the bootrec / fixmbr it told me that the task was completed unsuccessfully. 
I went to look at the super grub disk site and im still trying to figure out how to use the grub disk. I have to run it from USB because I'm now only able to run ubuntu from the live CD. 

Whenever I get to the part where i put in:

grub
grub>device (hd3) /dev/sdc
grub>root (hd3,0)
grub>setup (hd3)
grub>quit 

 Error 27: Unrecognized command

Any suggestions?

---

### Post by caljohnsmith on 2009-01-17
What is your ultimate goal? Do you just want to have Vista on the computer, or do you want to keep Ubuntu and have a dual boot setup?

---

### Post by mukhul on 2009-01-17
I just want to have vista. No dual boots or anything like that. maybe in the summer when i have some time I can play around with stuff like that but for now, I need a vista running system.

---

### Post by caljohnsmith on 2009-01-18
OK, how about booting the Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And please post the output of all the above commands. If the last lilo command completes successfully, go ahead and reboot and let me know exactly what happens on start up. We can work from there.

---

### Post by mukhul on 2009-01-18
Ok, i made it to the second command line and get this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2a7c48a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20482047    10240000   27  Unknown
/dev/sda2        20482048    86368133    32943043    7  HPFS/NTFS
/dev/sda3        86381505   166529789    40074142+   5  Extended
/dev/sda4       166539264   312578047    73019392    7  HPFS/NTFS
/dev/sda5        86381568   163156139    38387286   83  Linux
/dev/sda6       163156203   166529789     1686793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo apt-get install lilo
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Sorry but i dont know what to do from here. Thanks for being so helpful.

---

### Post by caljohnsmith on 2009-01-18
Go ahead and run that last lilo command anyway, because if you are using a recent Live CD then lilo will be installed by default. I only included the apt-get command just in case, but try the last lilo command and let me know what that returns.

---

### Post by mukhul on 2009-01-18
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2a7c48a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20482047    10240000   27  Unknown
/dev/sda2        20482048    86368133    32943043    7  HPFS/NTFS
/dev/sda3        86381505   166529789    40074142+   5  Extended
/dev/sda4       166539264   312578047    73019392    7  HPFS/NTFS
/dev/sda5        86381568   163156139    38387286   83  Linux
/dev/sda6       163156203   166529789     1686793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo apt-get install lilo
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ sudo lilo -M  /dev/sda mbr
Fatal: write /boot/boot.0800: No space left on device
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-18
Something seems really broken with your Live CD. How about instead boot the Super Grub Disk, and go under the Windows menu, and there is an option there to write a Windows MBR (syslinux is what they actually use). Sorry I can't give any more specifics, because I'm just going from memory. The Super Grub Disk website also has a help/wiki section where they describe how to do it in detail. Let me know how that goes.

---


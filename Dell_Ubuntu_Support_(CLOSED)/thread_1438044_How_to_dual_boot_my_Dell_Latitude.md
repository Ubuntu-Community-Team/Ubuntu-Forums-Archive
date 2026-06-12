---
title: "How to dual boot my Dell Latitude"
date: 2010-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by savyboy24 on 2010-03-24
How can I have XP and Ubuntu (dell iso) on the Latitude D400 and dual boot. Every time I put one OS on it erases the other what do I do?

---

### Post by rpared01 on 2010-03-24
if you are using Dell's 8.04 LTS, then yes it will remove it. You are better off downloading Ubuntu 9.10 and Dual boot that way. i Recommend you install XP first, then ubuntu.

---

### Post by savyboy24 on 2010-03-24
Right now I am going to try to...
1) install the Dell Iso 8.04.1 LTS (not sure if any other version will work)
2) use the partition editor and make a ntfs partition for XP
3) put XP on that partition

---

### Post by darolu on 2010-03-24
> **savyboy24 said:**
> Right now I am going to try to...
1) install the Dell Iso 8.04.1 LTS (not sure if any other version will work)
2) use the partition editor and make a ntfs partition for XP
3) put XP on that partition

It should work that way, just keep in mind that after you install Windows XP, it will overwrite the MBR making GRUB inoperative and you'll have to reinstall it (GRUB, not the whole OS).

Follow this steps:

From: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)
> 1. Boot from a Live CD, like Ubuntu Desktop, or similar. It is recommended to use Ubuntu 9.04 or newer as this has NTFS write support.

2. Open a Terminal. Open a root terminal (For non-Ubuntu live CDs type su the terminal. For Ubuntu based distros run **sudo -i**) Enter root passwords as necessary.

3. Type **grub** which makes a GRUB prompt appear.

4. Type **find /boot/grub/stage1** You'll get a response like "(hd0)" or in my case "(hd0,3)". Use the output from this command for the following commands.

Note:

You should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type **root (hd0,3)** note the space between root and (hd0,3).

6. Type **setup (hd0,3)** into the prompt. This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your Linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type **quit**

8. At this stage you can either restart the system and install your own bootloader, or you can continue and tell the Windows bootloader where to find GRUB which will handle booting Linux. 

---

### Post by yomuffin11 on 2010-03-24
Ubuntu 8.04 LTS does not work with the Win (XP) duel boot; however, Ubuntu 9.04+ will work. There is an option once you partition the harddrive with GParted that says 'Install side by side...'. Choose that and you should be good.

NOTE: Before switching make sure you back up important files

XD

---

### Post by savyboy24 on 2010-03-27
So, I added Ubuntu then partitioned it then added XP reloaded the grub and can now load Ubuntu. I can see that my XP files are still present but cannot seem to get access to run XP now. ow do I do that?

---

### Post by dentaro16 on 2010-06-18
well i would have recommended to install XP then install 9.04+ using WUBI but my question is...

Are you trying to just access your files that exist on your XP partition when you are in ubuntu or are you just trying to boot into XP after you have installed both operating systems side by side?

if you need to access your files you needs to have NTFS support. im pretty sure that ubuntu comes with support for this (i know that RHEL doesn't natively support it...) if not you need the ntfs-3g package.


i have found it easier now than ever to just install windows first and then install ubuntu. the windows bootloader feels that it needs to be the only one ever to exist. so yes, it will corrupt grub.

i have been running windows 7 and ubuntu dual booted using WUBI and it has been fantastic

---

### Post by waynefoutz on 2010-06-19
> **dentaro16 said:**
> well i would have recommended to install XP then install 9.04+ using WUBI but my question is...

Are you trying to just access your files that exist on your XP partition when you are in ubuntu or are you just trying to boot into XP after you have installed both operating systems side by side?

if you need to access your files you needs to have NTFS support. im pretty sure that ubuntu comes with support for this (i know that RHEL doesn't natively support it...) if not you need the ntfs-3g package.


i have found it easier now than ever to just install windows first and then install ubuntu. the windows bootloader feels that it needs to be the only one ever to exist. so yes, it will corrupt grub.

i have been running windows 7 and ubuntu dual booted using WUBI and it has been fantastic


Wubi is  meant to be a temporary install so you can try out Ubuntu. It's not supposed to be permanent. Your Linux hard drive isn't a hard drive at all, it's a big file residing on your Windows drive. If it gets corrupted, your Linux install and all it's data will be lost. That big file also will drag down Windows' performance as well, because the file is unmovable on the drive, and your hard drive heads will have to work around it when reading and writing data. Wubi is a great way to try Ubuntu, in fact I use all the time on my Windows drive to test a new build of Ubuntu or Mint to see how it will run on my computer, but it's not meant to be left there permanently.

---


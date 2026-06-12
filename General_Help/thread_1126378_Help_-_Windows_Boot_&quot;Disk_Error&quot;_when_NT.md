---
title: "Help - Windows Boot &quot;Disk Error&quot; when NTFS Resized"
date: 2009-04-15
forum: General Help
---

### Post by NightwishFan on 2009-04-15
Greetings all.

I was installing Ubuntu 8.10 on my friends desktop, with the promise I would keep Xp MC as well. WUBI did not work. (His xp was fairly compromized and it had a random error and closed). I tried a normal install and in partitioning shrunk his Windows Xp NTFS disk. The installation of Ubuntu went fine. Grub was also installed correctly with entries for Ubuntu and Xp. Here is the kicker..

When you select to boot into Xp, I get an error, "Disk Read Error - Press CTRL+ALT+DELETE to reboot" Grub is not the problem so I am fairly sure it is wrong reported geometry. (Windows is lame...)

I found what seems like a reasonable solution here but I cannot make heads or tails of it.

[http://fugitivethought.com/blog.php?action=view&blog_id=77]("http://fugitivethought.com/blog.php?action=view&blog_id=77")

As for the solution. I am looking forward to something I can do perhaps from an Ubuntu Live CD. Preservation of data is not an issue as much as getting his XP MCE to boot.

There is a Recovery Partition available. (I think it is a compaq desktop) I can boot to it using Super Grub, but it does not allow Windows to boot, it merely reinstalls it and has the same error.

Will deleting the NTFS partition and creating a new one, and then reinstalling XP from the recovery partition work??

EDIT: Perhaps it has something to do to the partition table? I cannot reformat it though the recovery partition is essential, and I have no Xp disk to reinstall.

Also, feel free to give me any ideas, even incomplete ones but I would feel comforted if someone had already tackled this problem and could simply tell me what to do.

Ok and overview:

Windows will not boot.
The recovery partition is available, not sure about Xp disk, assume not.
I have a super grub disk, and an Ubuntu 8.10 live CD.

Thank you and please inform me quickly if other materials are needed. I want to be prepared to fix his system by this weekend.

---

### Post by StuartN on 2009-04-15
> **NightwishFan said:**
> Will deleting the NTFS partition and creating a new one, and then reinstalling XP from the recovery partition work?

You possibly need an XP install disk and the XP license code as well as the recovery partition. Once you have reformatted the NTFS partition and reinstalled XP you will not be able to boot into Ubuntu immediately because XP will overwrite the Master Boot Record, but you can reconfigure grub after booting from a Live CD.

---

### Post by NightwishFan on 2009-04-15
The issue is not getting Ubuntu to work, I can do that fine. It is getting Windows to boot.

Ubuntu works fine, and I can configure grub manually if I want. I need to find a way to get Windows to boot, with only the materials I have.

Ubuntu Live CD
Super Grub
Xp Recover Partition

I think these should be sufficient, however if I must, I can download other tools. Thank you for the response though! Please keep them coming.

EDIT: It is unlikely I will find an XP Recover Disk, and also it is a "Media Center" so there IS not install disk... I need the Recover partition to work. I think deleting the partition will work, but I need to make sure. The only tool I have to create NTFS disk is.. Ubuntu Live CD. Perhaps Gparted Live if I can dig it out of my CD box.

---

### Post by Monotoko on 2009-04-15
Right, here is what you can do to at least get into Windows, im not too sure if it will fix the problem entirely, but it sounds like XP's booting is slightly screwed, and here is what you need to do:

Get your hands on a Windows XP Disk (Any disk, Home Edition even....your not installing it, you will just use it to repair) and press R during startup to enter a DOS menu.

Run "chkdsk /r"

I'm not sure if it is an MBR problem or not, so you could try restoring the XP MBR for now and see if that helps (Again from the recovery Windows XP Disk, just use "fixmbr" from that recovery console)

Remember, any XP disk will do, Home Edition and Professional will all detect that Windows XP MCE Installation from the recovery console, and since you arnt installing a new one, using another disk will be fine.

---

### Post by NightwishFan on 2009-04-15
I assumed as much after a few seconds of thought.. I might be able to lay my hands on a Xp Home install disk, if that will work. I am about 40% sure it is a partition table error, since the data on the disk is fine. (I can access it from Live CD).

I am slightly in a pinch here. My friend wants me to install Ubuntu, and when wubi failed, he said install normally. I was fairly sure I could, since I have done it before. When it fails all of a sudden it is my fault entirely. He was against the whole idea. :lolflag:

Hopefully I can fix, but I will never deal with dual boots again, unless I use WUBI.

---

### Post by Monotoko on 2009-04-15
Things happen, but not very often, but you have always gotta be prepared for something to go wrong, what worked on one computer may not work on another, i screwed up my parents computer trying to duel-boot it....Windows XP didnt like it one bit.

Just remember it needs to be the actual install disk, not a recovery disk.

---

### Post by NightwishFan on 2009-04-15
Yes, it is a Windows Xp Home Installer, which I spent 4 hrs using to fix another friends Xp, which I had to reinstall. (This was not my fault in the slightest, good sir. ;))

Thank you for your advice. Certainly I understand what I get into, I just assumed that the ntfsresize tool would work flawlessly. That is my fault. Perhaps his system had some obscure registry bug. This will not fix the problem, but hopefully I can get it working. If the recover partition does not work, they will likely try to get me to replace the dam Xp. I will not do that. They wanted me to install it even when I told them the risks.

Alas this is the only time Ubuntu posed a problem for me, and it wasn't really to blame.

---

### Post by meierfra. on 2009-04-15
I suspect that the boot sector of your windows partition is slightly corrupt. In order   get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by NightwishFan on 2009-04-15
Possibly, thank you for the help. I hope I will not have to reinstall Ubuntu to fix their Xp, but so be it.

Will that work from the live CD?

---

### Post by meierfra. on 2009-04-15
> Will that work from the live CD?

Yes.

---

### Post by NightwishFan on 2009-04-15
Thank you all. I must leave, but I will respond with any news or relevance. I will attempt the fix on Friday or Saturday. We will see how this goes.

---

### Post by Monotoko on 2009-04-15
Okay, Good luck, hope our suggestions are of use to you :)

---

### Post by bodhi.zazen on 2009-04-15
From your original post it sounds as if you were having problems with XP before you installed Ubuntu.

If that is the case my suggestion is that the XP install is borked and you are best off re-installing Windows XP. You can try repairing the install with the XP install disk (repair option) , but it is a problem with malware that may not help.

> His xp was fairly compromized and it had a random error and closed.

---

### Post by NightwishFan on 2009-04-15
Thank you for the response. Perhaps I should rephrase. WUBI closed with some generic Windows popup error. So I was told to do a normal installation. His Windows was highly compromised and poorly maintained, but that is not why it will not boot.

My goal is to repair it, or reinstall it from the recovery partition. Considering the fact I will have to somehow hunt for ethernet drivers, to get the rest of the drivers for it, installing from CD is not going to happen. I will need to boot from recovery.

My one friend remarked, using Ubuntu is the best thing that happened to it, but then again they mostly used it for gaming (slow gaming but gaming nonetheless). Which is why they need Xp. It is perhaps 40% my fault why it will not work, and I do not want to be held responsible and pay a repair bill. :D

---

### Post by bodhi.zazen on 2009-04-15
Can you mount the Windows XP partition in Ubuntu ?

---

### Post by NightwishFan on 2009-04-15
Of course. That is why I think it is somehow related to the partition table. Ntfsfix does not help. I was told to try the Windows one from Xp install CD.

---

### Post by bodhi.zazen on 2009-04-15
You can then try to restore the windows boot loader.

You can do this from within linux without the windows cd

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

The first and second posts may help.

From there you can re-install grub.

If you want to look at the partition table, try testdisk. testdisk in in the repos and can be installed and run from a live CD.

---

### Post by NightwishFan on 2009-04-15
It is not grub. I already fixmbr to Windows boot loader, and same error. It possibly is something to do with the way the NTFS geometry is registered. I think the solution is to either, run Windows fix tools. (Which I estimate 7% chance of success). Or reformat and reinstall using the recovery partition. (Which I estimate 40% chance success).

Reinstalling from CD is useless since I will spend all day hunting drivers.

My chances of success seem very poor indeed, which is why I need some alternatives. Perhaps there is a way using NTFS tools or so, I can realign the NTFS, such as in the link in my first post here. However I cannot make heads or tails of it...

---

### Post by meierfra. on 2009-04-15
After resizing an "ntfs" partition from linux  the hidden sector number in the boot sector is sometimes wrong. A wrong hidden sector number causes  the "disk read error". Running the boot info script would  tell as whether the hidden sector number is indeed wrong.  
Running "fixboot", as recommended  in the link posted by bodhi.zazen, often (but not always) fixes the hidden sector number.

The best way to fix a wrong hidden sector number is with testdisk (as suggested by  bodhi.zazen):

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu (or Ubuntu LiveCD)  desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

(here /dev/sda must be replaced by the device name  of the Windows drive) 
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

testdisk RebuildBS will also fix any other parameters which might be wrong in the boot sector.

---

### Post by NightwishFan on 2009-04-16
Thank you good sirs. Now we are getting some alternatives. As far as fixing this goes, I am going to try any options I can find in order of how little change of data loss there is, merely to be on the safe side.

As for the bootfix. Is this been known to fix the disk read error? I am fairly sure it is a small amount of problems that actually cause this error, of course.

---

### Post by meierfra. on 2009-04-16
> As for the bootfix.

Do you mean "fixboot"?  

> Is this been known to fix the disk read error?

It's supposed do fix it, but it does not always work.  I have not been able to figure out when it works and when it doesn't. It might depend on the CD you are using. But even with the same CD it sometimes works and sometimes doesn't.

testdisk on the other hand seems to have a 100% success rate. (but this assume that your problem is really caused by a wrong hidden sector number)

---


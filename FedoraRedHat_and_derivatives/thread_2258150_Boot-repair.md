---
title: "Boot-repair"
date: 2014-12-25
forum: Fedora/RedHat and derivatives
---

### Post by pingo-power on 2014-12-25
Hello, please, thanks, bye !
I follow this tutorial because after the installation of CentOS, grub don't got windows 8.1 entry : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (2nd option).

I follow him up to the command "[...]-repair &)" and it remains bocked, it no longer advance...

[[IMG]http://image.noelshack.com/minis/2014/52/1419420578-test.png[/IMG]]("http://www.noelshack.com/2014-52-1419420578-test.png")

What i should do ?

---

### Post by schragge on 2014-12-25
Check that gksu is installed. Open another terminal window, and type
```

[COLOR=green]$ [/COLOR]which gksu
[COLOR=green]/usr/bin/gksu[/COLOR]

```
You should get the output marked in [COLOR=green]green[/COLOR]. If the *which* command doesn't output anything, try
```

sudo apt-get install gksu

```
Report the result back here. After successfull installation of gksu you'll need to abort execution of boot-repair (click on the orange cross icon), and start it anew.

BTW, have you tried to repair GRUB from inside CentOS rescue mode? How to get there is described [here]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/sec-Terminal_Menu_Editing_During_Boot.html").

---

### Post by pingo-power on 2014-12-25
> ubuntu@ubuntu:~$ $ which gksu
$: command not found
ubuntu@ubuntu:~$ which gksu
ubuntu@ubuntu:~$ /usr/bin/gksu
bash: /usr/bin/gksu: No such file or directory
ubuntu@ubuntu:~$ which gksu /usr/bin/gksu
ubuntu@ubuntu:~$ sudo apt-get install gksu
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet gksu
ubuntu@ubuntu:~$ 

I can boot CentOS in rescue mode i think, but what i should do into him for repair grub ?

---

### Post by schragge on 2014-12-25
> E: Impossible de trouver le paquet gksu
Well that's weird. Check that you have internet connection, and apt-get update:
```
sudo apt-get update
```
Then re-try
```
sudo apt-get install gksu
```

> **pingo-power said:**
> I can boot CentOS in rescue mode i think, but what i should do into him for repair grub ?
There's [some official RedHat documentation on reinstalling GRUB](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/sec-Reinstalling_GRUB_2.html). But I guess this is rather a question for a CentOS forum.

 There's also a [RedHat Knowledgebase entry](https://access.redhat.com/solutions/961353) directly corresponding to your problem, but access to it requires subscription. Anyway, [check this answer](http://www.linuxquestions.org/questions/red-hat-31/how-to-add-windows-entry-to-grub-in-redhat-linux-7-a-4175520467/). Basically you need to add something like
```

menuentry "Windows 8.1 (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
chainloader +1
}

```

to one of the config snippets under /etc/grub.d like described in [Customizing GRUB 2 Menu](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/sec-Customizing_GRUB_2_Menu.html). Obviously, it may be *insmod part_gpt* in you case or whatever partitioning scheme your PC uses.

Also, [here](https://ask.fedoraproject.org/en/question/9766/how-could-i-dual-boot-fedora-18-and-windows-8-on-secure-boot-mode/) is an answer on a related question for Fedora 18. RHEL7 is based on Fedora 19, they should be sufficiently similar.

---

### Post by grahammechanical on 2014-12-25
If CentOS is installed after Ubuntu then as part of its installation process CentOS will put its bootloader in charge of the boot menu. So, your problem is with CentOS. Can you boot into Ubuntu? Do you have Ubuntu installed? When we run boot Repair it produces a report and we get a url to a pastebin location. If you post that url into your thread then we can view the Boot Repair report and try to work out what the problem is.

Are you aware that when installing Ubuntu with Windows 8 already installed we have to take special steps. Perhaps we need to take those same special steps when installing CentOS. What advice do CentOS developers give for installing CentOS on a machine with Windows 8 already installed?

Oh, by the way, I do not give support for CentOS. This Ubuntu forum has a section called Other OS support and Projects with a sub-section called Fedora/RedHat and derivatives. 

Regards.

---

### Post by pingo-power on 2014-12-25
> ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic InRelease
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/main Translation-en_US
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/main Translation-en
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/restricted Translation-en_US
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                  
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg [933 B]      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release [62.0 kB]             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages [87.7 kB]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic InRelease           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates InRelease      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages [8,424 B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en [40.9 kB] 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en [2,268 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release.gpg [933 B]                     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release.gpg [933 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release [215 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release [62.0 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main i386 Packages [1,325 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted i386 Packages [12.6 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en [769 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en [3,315 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main i386 Packages [120 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted i386 Packages [8,424 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en [55.9 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en [2,268 B]
Fetched 2,778 kB in 5s (532 kB/s)                              
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksu
ubuntu@ubuntu:~$

@schragge too information, i'm overloaded, you want i do what ? 
I 'm not very comfortable with the English language , I can not read tons and tons of line in English, because I soon may fall on a misunderstanding , so I would really like you to tell me just typing what and where it will be much easier and go faster.
@graha Basically a have windows 8,1 but in want to dual boot with CentOS, i dont have any other OS

---

### Post by schragge on 2014-12-25
Ah now I understand. gksu is in the **universe** repository which is not enabled on you Live Ubuntu system. Enable it in Software Sources (probably Sources de logiciels on your system). Then try to install it again.

---

### Post by pingo-power on 2014-12-25
My Ubuntu LiveCD is now on english, where is software sources ?

---

### Post by schragge on 2014-12-25
*Ubuntu Software Center* : >> Edit, Software Sources

---

### Post by pingo-power on 2014-12-25
gksu installation is done, 
and after having execute boot -repair , it still has blocks at "Scanning systems. this may require several minutes..."

---

### Post by yancek on 2014-12-25
>  Basically a have windows 8,1 but in want to dual boot with CentOS, i dont have any other OS 				

[https://www.centos.org/forums/](https://www.centos.org/forums/)

I'm not sure why you are posting here (Ubuntu forums) if you have only CentOS and windows?  Someone might be able to help.  The first thing we need to know is which CentOS you have because CentOS used Grub Legacy until version 7.  Do you have version 7?   Maybe you could run the boot repair and select "create bootinfo report" and post that output here for review.

---

### Post by oldfred on 2014-12-25
Moved to Other OS.

---

### Post by pingo-power on 2014-12-25
Yep i have 7, but i can't create rapport for boot repair because he block in loading "scanning systems. This may require several minutes..."

---

### Post by pingo-power on 2014-12-25
i do "
bootrec /fixmbr
bootrec /fixboot" in the CD of windows and now i dont have any boot, just a black screen with a flashing dash

---

### Post by oldfred on 2014-12-25
Those are Windows commands, to load the Windows boot loader to the MBR, and update the part of the Windows boot loader in the partition boot sector.
So now you need to go to a Windows forum for help on Windows issues.

I suggest:
       [http://www.sevenforums.com/](http://www.sevenforums.com/)

There is an Ubuntu French forum and the author of Boot-Repair sometimes is there as he is French.

  [www.ubuntu-fr.org]("http://www.ubuntu-fr.org")

---

### Post by pingo-power on 2014-12-26
I go to the windows forum and i return to you when i have the solution or a problem, thanks

I'm in this topic : [http://windowsforum.com/threads/boot-problem.202674/](http://windowsforum.com/threads/boot-problem.202674/)

actually i do this at the request of the person on this forum, but don't work ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0488701

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   934086655   466683904    7  HPFS/NTFS/exFAT
/dev/sda3       954566656   976771119    11102232    7  HPFS/NTFS/exFAT
/dev/sda4       934086656   954566655    10240000    5  Extended
/dev/sda5       934088704   935112703      512000   83  Linux
/dev/sda6       935114752   936138751      512000   83  Linux
/dev/sda7       936140800   954566655     9212928   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/mapper/centos_pc--portable-swap: 4177 MB, 4177526784 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8159232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/centos_pc--portable-swap doesn't contain a valid partition table

Disk /dev/mapper/centos_pc--portable-root: 5255 MB, 5255462912 bytes
255 heads, 63 sectors/track, 638 cylinders, total 10264576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/centos_pc--portable-root doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install syslinux
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic InRelease
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/main Translation-en_US
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/main Translation-en
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/restricted Translation-en_US
Ign cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20140522) utopic/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release.gpg [933 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release.gpg [933 B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release [215 kB]    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg [933 B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release [62.0 kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release [62.0 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main i386 Packages [1,325 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages [87.7 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted i386 Packages [12.6 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en [769 kB]           
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en [3,315 B]    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main i386 Packages [120 kB]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted i386 Packages [8,424 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en [55.9 kB]  
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en [2,268 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages [8,424 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en [40.9 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en [2,268 B]
Fetched 2,778 kB in 2s (948 kB/s)                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  syslinux-common
The following packages will be upgraded:
  syslinux syslinux-common
2 upgraded, 0 newly installed, 0 to remove and 1152 not upgraded.
Need to get 1,012 kB of archives.
After this operation, 109 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/main syslinux-common all 3:6.03~pre18+dfsg-1ubuntu1 [871 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/main syslinux i386 3:6.03~pre18+dfsg-1ubuntu1 [141 kB]
Fetched 1,012 kB in 1s (738 kB/s)
dpkg: considering deconfiguration of syslinux-common, which would be broken by installation of syslinux ...
dpkg: yes, will deconfigure syslinux-common (broken by syslinux)
(Reading database ... 174703 files and directories currently installed.)
Preparing to unpack .../syslinux_3%3a6.03~pre18+dfsg-1ubuntu1_i386.deb ...
De-configuring syslinux-common (3:4.05+dfsg-6+deb8u1) ...
Unpacking syslinux (3:6.03~pre18+dfsg-1ubuntu1) over (3:4.05+dfsg-6+deb8u1) ...
Preparing to unpack .../syslinux-common_3%3a6.03~pre18+dfsg-1ubuntu1_all.deb ...
Unpacking syslinux-common (3:6.03~pre18+dfsg-1ubuntu1) over (3:4.05+dfsg-6+deb8u1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up syslinux-common (3:6.03~pre18+dfsg-1ubuntu1) ...
Setting up syslinux (3:6.03~pre18+dfsg-1ubuntu1) ...
ubuntu@ubuntu:~$ sudo  dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
dd: failed to open &#8216;/usr/lib/syslinux/mbr.bin&#8217;: No such file or directory
ubuntu@ubuntu:~$
```

---

### Post by oldfred on 2014-12-26
If you have 
ubuntu@ubuntu:~$
Then you are on the live installer. As the live installer is it not updateable, so you should get errors on trying to write updates.
Even if flash drive, it is fixed like the DVD to be all the standard versions, so cannot be updated. Not sure why you would want to update live installer anyway. 
You use live installer to install Ubuntu or use it as a repair tool like any other Linux live boot. You can easily repair Ubuntu, chroot into another system and make repairs, mount and copy data from another file system etc.

---

### Post by pingo-power on 2014-12-26
I use a liveCD of Ubuntu, and i want to repair boot for boot on windows, what i should do ?

---

### Post by oldfred on 2014-12-26
Boot-Repair only does minor fixes to a Windows install, like reinstalling a Windows boot loader (similar to fixMBR command you already ran). Boot-Repair is primarily for Linux repairs.

Almost all Windows fixes require a Windows repairCD or flash drive. And only Windows repair tools can run chkdsk which often is required.

With a Windows boot loader in MBR, can you use f8 to get into Windows repair console. Or how did you run fixMBR before. If you have Windows repairCD or flash you can run auto fix 3 times or use its command line like you did to run fixMBR and run other commands also.
Again the Windows forums know more about Windows fixes, we have only picked up some of the minor repairs to get it working with dual boot.

[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html) 

Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by pingo-power on 2014-12-26
Even Windowsy can not help me [URL="http://windowsforum.com/threads/boot-problem.202674/"]http://windowsforum.com/threads/boot-problem.202674/


chkdsk dont return error, but my boot don't work
[/URL]

---

### Post by oldfred on 2014-12-26
Post a link to the summary report from Boot-Repair. 

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But if internal Windows issues we cannot really help.

---

### Post by pingo-power on 2014-12-28
I can't do that, boot repair stop at "Scanning systems[...]"

---

### Post by oldfred on 2014-12-28
You have NTFS partitions & Centos is in stalled with LVM. 
If Boot-Repair cannot finish scanning systems, then you have some file corruption.
You first need to run chkdsk from your Windows repair disk on all three NTFS partitions.
Run fsck on the two Linux partitions.
And mount and repair the LVM. But I know nothing about LVM partitions. Since that may be the default with OpenSuse, you may do better in their  forum.

---

### Post by pingo-power on 2014-12-28
i run a lot of check disk, not error.

Do you have a solution for reinstall windows and conserve personnal files ? (windows.old)

---

### Post by oldfred on 2014-12-28
My last install of Windows was XP in 2006. :) 

You should be able to use live installer to mount NTFS partitions and copy files to an external drive. 

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

No idea if these work or not. Good backup required before any major changes.

 Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)

---

### Post by pingo-power on 2015-01-04
Hello, please, thanks, bye !

How to add windows to CentOS grub with boot-repair

---

### Post by coffeecat on 2015-01-04
Threads merged. Please do not start duplicate threads about the same problem. If you need further help, you can simply bump the earlier thread.

---

### Post by pingo-power on 2015-01-04
isnt the same problem

---


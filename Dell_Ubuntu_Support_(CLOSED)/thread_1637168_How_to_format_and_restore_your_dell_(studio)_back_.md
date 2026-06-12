---
title: "How to format and restore your dell (studio) back to 'factory settings' and dual boot"
date: 2010-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FirstByté on 2010-12-04
[COLOR="Red"]HOW TO FORMAT AND RESTORE YOUR DELL (STUDIO) BACK TO 'FACTORY SETTINGS' AND DUAL BOOT UBUNTU/LINUX[/COLOR]
_THIS IS MEANT FOR WINDOW VISTA or WIN7_
Suitable for 'Like-*NORMAL*' factory partitioned Restore Partition Drive (e.g. "D:\" )
- After this process, '**F8**' should be able to lunch you into DELL Windows Recovery Environment (at Windows boot section, not [Ubuntu]("http://www.ubuntu.com")/Linux)
- Keep your Restoration Partition and still run a Linux Distro such as [Ubuntu]("http://www.ubuntu.com").

[B]_NOTE_:[COLOR="Red"] DISCLAIMER![/COLOR]
I DO NOT WORK OR WRITE THIS AS A DELL STAFF! THIS IS WHAT WORKED FOR ME AND I HAVE DECIDED TO SHARE IT. WHENEVER POSSIBLE, ALWAYS BACK-UP YOUR HARD DISK BEFORE ATTEMPTING RESTORE/REINSTALLATION. YOU SHOULD CONSULT DELL SUPPORT IN ANY EVENT YOU NEED TO. I WILL NOT BE HELD LIABLE! USE THIS OPTION IF YOU KNOW WHAT IT IS ALL ABOUT!
[/B]
> 
**_DISAMBIGUATION_**
RE-INSTALLATION means or suggests **INSTALLING** a new instance of a software that was previously installed (Often done from a CD/DVD-ROM).

RESTORATION means **RETRIEVING** the exact same files that were *STORED* in a particular location (e.g. External HDD, Restoration Partitions etc.). In most cases, depending on the captured situation, no [system] driver installation is required.


THE FOLLOW ARE THE REQUIRED STEPS.

*** THINGS TO HAVE**
[LIST=1]
[*] DELL RECOVERY PARTITION <INTACT!!! **NOT** the CD/DVD if this HowTo will work for you!>
[*] Back-up storage <Any storage device that can hold the DELL RECOVERY PARTITION that came with your system. Mine was about 5GB>
[*] LiveCD <Ubuntu [LiveCD]("https://help.ubuntu.com/community/LiveCD") or equivalent will suffice>
[*] Windows Vista Recovery Disk <[NeoSmart Has one]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (Or directly from Microsoft)>
[/LIST]
*<You might be LUCKY if the Recovery that came with your system works on yours. Mine works on other systems but mine!!! GREAT DELL>*
[B]
--=====================--
* STEP 00: BACK-UP ALL NECESSARY files
--=====================--
[/B]

It is most advisable to not commence this action until you have a backup disk that is large enough to take all your necessary files and folders. If you prefer the Linux way just do this:

* Mount the drive to be backed-up if not mounted yet
*<see [here for more details]("http://ubuntu.swerdna.org/ubuntfs.html")>*
```
~$ sudo fdisk -l #this is letter lower case L not number one!
~$ [COLOR="SeaGreen"]#this will show you the drive letters e.g. /dev/sda1 or /dev/sdb1 etc I'll call this dev-name-location![/COLOR]
~$ sudo mkdir /media/mydrive
~$ sudo mount /dev/[COLOR="Red"]<dev-name-location>[/COLOR] /media/mydrive [COLOR="SeaGreen"]# in my case mine is /dev/sda3[/COLOR]
~$ [COLOR="SeaGreen"]# use this if you are trying to mount an NTFS drive...[/COLOR]
~$ [COLOR="SeaGreen"]# remove the pound sign though to make it work!!!![/COLOR]
~$ [COLOR="SeaGreen"]# sudo mount -t ntfs-3g /dev/sda3 /media/mydrive -o force[/COLOR]

```
You may use the GUI option if you prefer.
**System**->**Administration**->**Disk Utility**


* Copy the necessary files
```
~$ cd /path_to/copy_from
~$ cp -Rf /media/path_to/my_drive /path_to/backup_disk_location
~$ [COLOR="SeaGreen"]# Example will be ..[/COLOR]
~$[COLOR="SeaGreen"] # cp -Rf /media/my_drive/OS/Users/ /media/my_backup_HDD/Users[/COLOR]
~$ [COLOR="SeaGreen"]# you may use the '[COLOR="Black"]-p[/COLOR]' option if you want to preserve all file permissions from source![/COLOR]

```

[B]
--=====================--
* STEP 01: BACK-UP YOUR DELL RECOVERY PARTITION
--=====================--
[/B]


[LIST=1]
[*] Get a working Linux box such as [Ubuntu]("http://www.ubuntu.com") or LiveCD and boot into it
[*] Mount the Dell Recovery Partition <Follow the process above>
[*] Insert your backup device (e.g. 8GB thumb-drive, external HDD, but NOT your SYSTEM HARD DRIVE. [COLOR="Red"]**We will be formatting this!**[COLOR])
[*] Copy the all files from Dell Recovery Partition <for example, I inserted my external hard drive on '/dev/sdb1'>
[/LIST]

*** Backing up Dell Recovery Partion**
*<for this example I'll assume your backup drive is external HDD (/dev/sdb). It may vary in yours! And my Dell Partition Drive is mounted as [COLOR="SeaGreen"]'/media/RECOVERY'[/COLOR]>*

Mount the external drive if it is not already mounted <see steps above>
```
~$ #create destination folder
~$ cd /media/my_backup_hdd
~$ mkdir DELL_RECOVERY_DISK
~$sudo cp -Rfpv /media/RECOVERY/ /media/my_backup_hdd/DELL_RECOVERY_DISK/

```
*Note: I added the -v option to help you monitor the long copying process.*

[B]
--=====================--
* [COLOR="Red"] STEP 02: FORMAT YOUR HDD[/COLOR]
--=====================--
[/B]


[LIST=1]
[*] Unmount any drive that resides on the system you are trying to recover <This suggests that you might have to use a LiveCD or equivalent if you have been working from your Install Ubuntu Box>
[*] Reslize/ repartition your drives using LiveCD or equivalent
[/LIST]

For me, I had issues partitioning from my LiveCD so I opted for an 100% installation of Ubuntu which helped to wipe out the hard disk.
Next I used an Ubuntu LiveCD to re-slize my Hard Drive which is 250GB in total.
> 
**SUMMARY**
**PARTITION            NAME            SIZE                FLAG**
1                    RECOVERY        10GB                    HPFS/NTFS
2                    OS                100GB(Optional size)    HPFS/NTFS
3                    Linux            240GB(My Ubuntu space)    Extended

[I]Note: I did not create a swap drive yet, I allowed Ubuntu to create it later.
[COLOR="Red"]**I created a partition for Linux because I plan to Dual-boot later**[/COLOR][/I]


[B]
--=====================--
* STEP 03: RESTORE YOUR RECOVERY PARTITION
--=====================--
[/B]

Here, we'll try to copy back the content of the DELL RECOVERY PARTITION

*    You will have to insert a LiveCD or equivalent.
[LIST=1]
[*] Mount the location where you backed-up the DELL_RECOVERY <See description/process above>
[*] Mount the NEWLY CREATED [empty] RECOVERY Drive. [COLOR="SeaGreen"]e.g. '/media/RECOVERY'[/COLOR]
[/LIST]
```
~$ sudo cp -Rfpv /media/my_backup_hdd/DELL_RECOVERY_DISK/ /media/RECOVERY/
```
*Note: This copies the files and still maintaining their initial file permissions.*


[B]
--=====================--
* STEP 04: RESTORE YOUR WINDOWS FILES
--=====================--
[/B]

At this stage we'll be using the Vista Recovery DVD


[LIST=1]
[*] Insert the Vista Recovery DVD and reboot your system
[*] Boot into the DVD-ROM by hitting '**F12**' at booting prompt (Before the Windows/GRUM menu!)
[*] Drop to the Repair->Command Prompt.
[/LIST]

From the command prompt, issue the following commands
```

X:\> D:
D:\> cd tools
D:\Tools> imagex /apply d:\dell\image\factory.wim 1 c:\
D:\Tools> cd ..
D:\>

```
If all went fine to this point, you are a happy man!!
*If you get to check it, a DELL Utility PARTITION is already set-up [PARTITION ID: DE]*

[B]
--=====================--
* STEP 05: FIX THE DEFAULT MASTER BOOT RECORD (MBR) FIRST
--=====================--
[/B]

Boot back into your Windows VISTA RECOVERY DVD and drop down to command prompt as before.

* It is now time to RESTORE THE [COLOR="Red"]Master BOOT RECORD[/COLOR]. The most IMPORTANT PART
I find it quite important to set the path to your systems environment or some commands wouldn't run (on some DVDs).

**<[source]("http://support.microsoft.com/kb/927392/en-us") for fixing MBR...>**

NOTE: I added this line to ensure proper operations...
```

X:\> path=C:\Windows;C:\Windows\System32

```


```

X:\> C:
C:\> bcdedit /export C:\BCD_Backup
C:\> cd boot
C:\> attrib bcd -s -h -r
C:\> ren c:\boot\bcd bcd.old
C:\> bootrec /RebuildBcd
C:\> bootrec /FixMbr

```
*Note: "bootrec /FixMbr" is very important to fix your MBR back to the DELL way.*



[B]
--=====================--
* STEP 06: REBOOT AND SET-UP WINDOWS PROFILE
--=====================--
[/B]

This section is quite straight forward and succinct.

[LIST=1]
[*] Restart your system. * At this time, it should boot up to the Microsoft Vista Screen*
[*] Accept the DELL Licence agreements
[*] Accept the Windows Licence agreements etc.
[*] Follow other instructions.
[*] *OPTIONAL: Remove boltwares!*
[/LIST]

You should now have a fresh working Windows Vista.
NOTE: For some reasons, the DELL Recovery 'D:' drive may be hidden!
You can easily unhid this using GParted on a LiveCD. Just toggle the 'HIDDEN' flag.


[B]
--=====================--
* STEP 07: *OPTIONAL:* INSTALL UBUNTU
--=====================--
[/B]

See here >> [Install Ubuntu after Windows]("https://help.ubuntu.com/community/WindowsDualBoot")



[B]
--=====================--
* STEP 08: ENJOY UBUNTU EVERYDAY
--=====================--
[/B]

---

If anyone sees anything I've omitted please point out!

---


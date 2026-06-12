---
title: "Cloning a hard drive using dd"
date: 2009-05-18
forum: General Help
---

### Post by erictherev on 2009-05-18
I recently had an issue with a dying Seagate hard drive and went in search of a way to avoid having to reinstall my OS (Windoze on this particular system). saikee at [JustLinux]("http://www.justlinux.com/forum/showthread.php?t=134457") wrote the following How-To for those of us who don't want to pay for third-party software to clone a drive:

>  Using a Linux Live CD to clone XP and/or Vista
Recent updates

27 Apr 09 - The procedure set out here is applicable to Xp, Vista and Win7, regardless how many of them in the hard disk. No re-activation is needed but a reboot is generally necessary for the system to update its registry to account for a change in the hardware. Remember to remove the source disk or hide the source partition when booting the new traget partition or disk. Newer M$ systems uses a unique code for each partition identification which will be faithfully cloned. This can cause confusion to the OS if two identical partition codes are encountered. Generally the OS will disable the second partition and possibly invalidate its booting code.

30 Jan 07 - for reliably resizing XP partitions there are now free Linux Live CD on Gparted and Parted Magic
For a modern, informative and authoritative use of dd see AwesomeMachine's thread "Learn dd command"

13 May 07 - Section B added to include cloning the whole hard disk. I have since rewritten Section B as a separate thread in view of it being a general method which is recommended because it is a lot simpler but totally reliable. All you need is a hard disk exactly in size or just larger.

1 July 07 - A worked example to clone Windows Vista has been added in Post #55 of this thread

21 Oct 07 - Recommended block size now changed from 32768 to 32256 as the latter proves easier to finish with a full record in the last transfer.


----------------------------------------------------------------

Section A - Cloning a XP partition

For cloning Vista or an easier scheme see Section B

An installed Windows XP protects itself from being cloned even for the backup purpose. Specialised software like the Norton Ghost, Acronis or PowerQuest Drive Image has to be used so that the OS can be moved to a bigger hard drive in a disk upgrade.

Linuxs dd command also works the same way but this needed to be performed on the whole hard disk so that the MBR and partition table are cloned as one whole lot.

The method described below shows how Linux can be used to clone a XP partition. In the example here the source is a XP Pro partition in a 30Gb IDE drive recognised by Linux as hda1. For simplicity I used a disk with just one partition in it. The source XP partition has a SATA driver previously incorporated when installed. The target is a brand new unformatted 200 Gb SATA disk recognised by Linux as sda (older kernel may report hde).

To demonstrate the power of Linux I use only a Live CD from Knoppix 3.4. There is no other bootable Linux in the hard disk.

(1) Install both source IDE (hda) and SATA (sda) as internal hard disks into the PC and boot the computer up with Knoppix Live CD.

(2) Click Knoppixs terminal mode, type
```
su
```

to become the root user.

(3) Type
```
fdisk -l
```

to check the hda and sda structures if needed (Recommended so that you know what you are doing).

(4) Type
```
cfdisk /dev/hda
```

to write down the exact size of hda1, assumed NTFS type.

(5) Type
```
cfdisk /dev/sda
```

and create a primary sda1 partition, select file type NTFS (type No 7) and size identical to hda1, select it to be it bootable too, let it write the partition table and exit (recommend a reboot here to make the partition table permanent)

(6) Native copying by typing
```
dd if=/dev/hda1 of=/dev/sda1 bs=32256
```

The 32256 is the track size for 63 sectors each 512 byte. Progress is slower if bs is omitted and Linux would use the default block size 512.

(7) When dd operation completes it will show the time taken on the screen. Power down, remove Knoppix, remove the source disk hda. (re-set the new disk as the master, no action is needed if it is in cable select mode for the Pata disk. Sata disk has no master/slave setting and the booting queue is controlled by the Bios only)

(8) Boot system up with a DOS floppy (with fdisk.exe inside) to restore MBR by typing
```
fdisk /mbr
```

This works even on a SATA disk. Alternative boot up any Win2k or XP installation CD, go to the recovery console and issure command
```
fixmbr
```

(9) Remove DOS floppy and the SATA should be bootable with XP cloned.


Did this twice with a XP home and then a XP Pro. The above example has XP Pro in a 28.6Gb partition with 16.1 filled data. It took 4297 second or 72 minutes. On another 10.1Gb partition with XP home in 5.24 Gb data the time was 1409 seconds or 24 minutes. Naturally the two different licenses of XP booted successfully.

If the Linux has been installed from a hard disk and has the 2.6 kernel the time needed can be reduced considerably (about 50%).

The cloning rate for current versions Linux is about 45-55Mb/s for internal disks.
--------------------------------------------------------------

Section B - Cloning the whole disk containing either Win2k, XP, Vista or in any combination with or without other operating systems.

This method is highly recommended because it is the most reliable. The whole source disk is cloned to a target disk. The only essential requirement is the target disk must be as larger as the source disk, down to the exact number of sectors or simply just bigger.

The cloning has been 100% successful in the following applications

From a Pata to a Sata disk or the opposite way, both internal disks.
From an internal disk to an external USB hard disk or the opposite way
From a 2.5" latop disk to a 3.5" desktop hard disk (the opposite way not tried).

The number of operating systems and the types are immaterial to the cloning. I have the maximum 63 partitions in many disks cloned this way and every operating systems in the clone boots exactly as the original. The systems I cloned include a mixture of Dos, Windows (3x, 9x,2k, Xp & Vista), Linux, BSD and Solaris.

I am so confident with this method that on the completion of the cloning process I would remove the original source disk, put it away for safe keeping as the backup and start to use the newly cloned disk straight away, as I have never met a problem in upgrading my hard disk from 200Gb to 300Gb, then to 400Gb and finally to 500Gb.

I shall use the example of cloning an existing Pata hard disk known in Linux as hda into a newly purchased larger Pata disk hooked up as a USB hard disk. To Linux a USB disk belongs to the SCSI/Sata family and is called sda if it is the first one in the PC, otherwise it could be a sdb, sdc, sdd, sde etc.

Here is the simple steps

(1) Obtain a Linux Live CD. Any one will do because the dd command is an integral part of Linux terminal command. However for fast cloning please use the current version of Linux Live CD. Recommeded distros are Slax, Knoppix, Kanotix, Mepis, Fedora Live, Mandriva Live etc. Ubuntu is also suitable but it is slight more work to get root privilege.

(2) Obtain a hard disk enclosure and purchase a new hard disk is has a capacity larger than the original source disk. Cloning is just like putting a carbon paper between two sheets. It will not work out if the bottom sheet is physically smaller than the top sheet as part of the information cannot be recorded out. That will happen exactly to hard disk cloning. It is very simple. The partition table has been copied from a bigger original disk resulting some hard disk addresses cannot be found on the smaller cloned hard disk.

(3) Cut the seal from the new disk and install it into the hard disk enclosure as a raw disk. Hook it up to the PC as a USB hard disk. Boot up the PC with a Linux Live CD.

(4) Select terminal mode and become the superuser by issuing the terminal command
```
su
```

The standard practice in Linux Live CD is to waive the demand of root password which will be demand only if the Linux is installed into the hard disk, but there are always variations. If a root password is demanded take a look at the /home directory as the Live CD developer usually left a hint on how to get the root password. Some distros will work if you just press enter (i.e. blank password), other will accept "root" or "toor". I recommend Slax and its family distros because the root password is printed before the login.

(5) Check the hard disk naming notation in Linux by command
```
fdisk -l
```

Linux call a Pata either hda, hdb, hdc or hdd. For Sata it can be sda, sdb, sdc, sdd, sde, sdf etc. An USB disk also follows the SCSI/Sata notation so it will be call sda if there is no Sata or SCSI disk in the system, otherwise it will take the name sdx where x is the next alphabet not yet taken. One can see the name of the newly hooked USB disk as it has no partition inside and the capacity should correspond to the size purchased. I shall assume this new target disk to be sda. Please adjust according to your own circumstance.

(6) You can start the cloning process by one line of command
```
dd if=/dev/hda of=/dev/sda bs=32256
```

In the above "if" is the input device and "of" stands for the output device. The Block size parameter bs has been chosen to be one complete track of 64 sectors each 512 bytes. Omitting the bs parameter will cause dd to default to 512 bytes in each transfer and this slows down the cloning. The 32256 is about the optimum I have found.

For AMD 3200 Athlon PC with 1Gb ram my cloning speed between internal disk is about 50Mb/s. If one disk is a USB this can drop to about 10Gb/s.

dd does not output any information until the process is completed. The flickering LED of the hard disk tells us dd is busy. On completion dd will always report the number of records, each equal to the the specified block size, transferred. Multiplying the record number with the block size should correspond to the capacity of the source hard disk.

I recommend removing the source disk, put it away for safe keeping as the backup, install the cloned disk in its place and start using the new disk right away.

For those who is not already aware dd stands for "data dump" meaning the binary pattern from a source disk is read and then written on the target disk. Technically it is impossible to clone a disk that is not a 100% carbon copy of the original.

The newly cloned disk's extra capacity over and above the original disk simply become the unallocated hard disk space which can be absorbed into the existing partitions by gparted or Parted Magic. It is recommended the current versions of these software to be downloaded and run as Live CD.

It has been my experience the whole hard disk cloning will always work on XP and Vista.

The current Live CD versions of gparted and Parted Magic are good for resizing XP. To resize Vista I recommend using its own internal resizer program which is faster and the success is guaranteed by M$.

It is recommended Vista to be cloned as the whole hard disk. This is because the current Vista has a new MBR and will conduct a check on the partition table. It can use a change to the partition table, between a reboot, as an excuse for the security risk to refuse to boot. Cloning the whole disk gives Vista no such excuse because the partition table isn't changed. Vista will still be able to detect the hard disk has been altered and demands an immediate reboot, same as XP. After a reboot Vista will work normally after the hard disk serial number has been updated. 

I take no credit for writing this, I merely found it. Also, I have no idea how well this works as I started cloning my 160 Gb drive (connected to my AMD Athlon 64 X2 5000+) onto a new 250 Gb drive (both are SATA) about an hour ago. I'll update with my results soon.

---

### Post by erictherev on 2009-05-18
OK, my results from the second method listed:

4961616+0 records in
4961616+0 records out

160 GB copied in 6663.5 seconds (111.06 minutes) at 24.0 MB/s

After removing the source drive and rebooting into Windoze, everything seemed fine.

PartEd Magic (which uses gparted) did not work for me. It showed the full size of my drive, while Windoze did not. I had to use Knoppix 5.1.0 to resize the partition and get Windoze to see the full drive.

---

### Post by Michael Matthews on 2009-06-29
What if you need expand vista partition size on larger target disk? Or can you do that after the fact in VISTA?
I would rather not spend 60$ to copy vista to bigger disk.
Not concerned with ubuntu migration, can just use tar.

thanks

---

### Post by trinaryouroboros on 2009-10-04
I'm about to undertake this adventure myself, I did find the following to be advantageous in Vista:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

---

### Post by trinaryouroboros on 2009-10-04
Useless, waste of 1.666 hours for me:

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb of=/dev/sdc bs=32256

7752336+0 records in 
7752336+0 records out 
250059350016 bytes (250 GB) copied, 6684.57 seconds, 37.4 MB/s

I let the new hard drive be first boot source, old hard drive be secondary boot source, and it booted off the secondary, leading me to believe nothing works on the new hard drive.  In compmgmt.msc Vista x64 shows the new hard drive as type: Dynamic, status: Invalid - can't reactivate the disk, throws the following error:

"This operation is not allowed on the invalid disk pack."

I'm going to try forcing a boot, if it still doesn't allow me to boot I'm scrapping this project, sorry. No time for the wicked.

---

### Post by trinaryouroboros on 2009-10-05
:KS**[SIZE="6"][COLOR="Sienna"]American Linux Admin Bloopers!!![/COLOR][/SIZE]**:KS


:popcorn:


So I recognized that something was awfully strange when I rebooted and purposely disabled the original hard drive in the BIOS - because the system still booted Normally, off the new hard drive, but bouncing to the serial of the second hard drive as the boot loader indicates it's supposed to do.

:oops:


**[COLOR="Purple"][gets creamed in the face by pie, audience laughs][/COLOR]**


I then decided to force the thing, by disconnecting the original hard drive. What followed was a demand by the Vista bootloader, to insert the MS Vista x64 DVD and select Language: English, and choose Repair.

I did this, and albeit my hard drives are fairly standard, it could Not see the system location. Click Next anyway, and get foiled at every turn, plus the C: drive was not ready, according to the command prompt...

I chose to fake out the installer, by X'ing out of the repair window, and proceding to Install.  Plugged in my Product Key, hit Next, next again, and chose Custom install - then it finally shows me only one partition available - the very partition it claimed it couldn't find before while using the repair utility!

With a smirk on my face, I hit the X to go back to the main vista dvd menu, and chose Repair - this time, it Showed the system volume for repair, and I selected it, and then proceeded to choose Startup Repair - which of course now it detects a problem it needs to repair, and has me reboot to complete the repair process.

Upon rebooting, I get a happy chkdsk running, and finally the system boots up normal after correcting the serial for the new hard drive, in it's boot loader.

[B]
[COLOR="Purple"][audience claps][/COLOR][/B]


So, wanting to get my space back on the previous hard drive, I shut down the PC after confirming compmgmt.msc shows all the whopping free space after my C: partition in Disk Management...and then I plug back in my old hard drive, boot her up, and as it's loading...


**[COLOR="Blue"][SIZE="4"]Blue Screen of Death[/SIZE][/COLOR]**

:cry:


[COLOR="Purple"][B]Wheel of Fortune lands on Bankrupt...

[audience goes "AWWwwwwww"][/COLOR][/B]


So it auto-rebooted, and I found myself with the realization that the C: on the old hard drive is conflicting here.

Booted into Ubuntu Live CD (by the way, all I had was 7.10 amd64 - gotta love it), chose to delete the partitions on the old hard drive...confident the problem is here, folk.


**[COLOR="Purple"][audience boos][/COLOR]**


I hit q after making my changes, reboots...


**[COLOR="Blue"][SIZE="4"]Blue Screen of Death[/SIZE][/COLOR]**

**[COLOR="Purple"][audience gasps][/COLOR]**


What? That's impossible..uh oh, oh boy! What if I can't repair it, I'll waste another two days setting all my junk back up! Oh noes!

Well, Vista's CD naturally didn't help, as no matter What I did the Repair option couldn't find Anything this time, no system volume, although I could see the C: drive by using the command prompt...

Booted back into Ubuntu CD...ran fdisk -l

Ooops...stupid me didn't hit W to confirm fdisk changes...

](*,)


**[COLOR="Purple"][gets slapped by two dozen flying fish, audience laughs][/COLOR]**


Okay, after making the changes, I rebooted, and now all is well, System partition loaded perfectly, detected my old hard drive as an empty fresh disk, and all is running 100% with the system now.

Sorry for the mess.


:redface:

**[COLOR="Purple"][gets slammed by a bus load of marshmallow fluff, audience gives a standing ovation][/COLOR]**



:confused:

---

### Post by sparxesparks on 2010-02-07
Eric the Rev,
 
Thanks for this, I have been trying to 'dd' my IDE 80gb hard drive installation of XP to a new SATA2 500gb hard drive with a few problems. The first time I just used dd to copy the data but didn't disconnect the old hard drive which was my first mistake so will try again. You lose me around step 5 though, 
 
"and create a primary sda1 partition, select file type NTFS (type No 7) and size identical to hda1, select it to be it bootable too, let it write the partition table and exit (recommend a reboot here to make the partition table permanent)"
 
I'm new to Ubuntu, could you let me know how to do this? I didn't do this first time which may have also contributed to the problems.
 
You also say that your XP installation "The source XP partition has a SATA driver previously incorporated when installed." How can I check my XP installation has this? "

---

### Post by trinaryouroboros on 2010-02-23
> **sparxesparks said:**
> Eric the Rev,
 
Thanks for this, I have been trying to 'dd' my IDE 80gb hard drive installation of XP to a new SATA2 500gb hard drive with a few problems. The first time I just used dd to copy the data but didn't disconnect the old hard drive which was my first mistake so will try again. You lose me around step 5 though, 
 
"and create a primary sda1 partition, select file type NTFS (type No 7) and size identical to hda1, select it to be it bootable too, let it write the partition table and exit (recommend a reboot here to make the partition table permanent)"
 
I'm new to Ubuntu, could you let me know how to do this? I didn't do this first time which may have also contributed to the problems.
 
You also say that your XP installation "The source XP partition has a SATA driver previously incorporated when installed." How can I check my XP installation has this? "

You probably have to boot to the live CD, get to a terminal window and use "fdisk" as root, or "sudo fdisk", I believe. Might want to brush up on how to use fdisk, or read the manual on it, editing and making partitions is risky business if you don't know what you're doing. There's also "gparted" if you prefer a GUI in Ubuntu.

---

### Post by uncle-c on 2010-02-23
Trinary,
Saikee is a true legend from JustLLinux and Linux Questions.  I have tried his tutorials on grub, os installation and backup using dd and they haven't been wrong yet. Because they mostly involve command line they can be prone to user errors. Best alternative way to clone a hard drive would be using Clonezilla or Partimage.

ps: His tutorials on installing 100+ operating systems on one computer are interesting reading to say the least !

---

### Post by trinaryouroboros on 2010-02-23
> **uncle-c said:**
> Trinary,
Saikee is a true legend from JustLLinux and Linux Questions.  I have tried his tutorials on grub, os installation and backup using dd and they haven't been wrong yet. Because they mostly involve command line they can be prone to user errors. Best alternative way to clone a hard drive would be using Clonezilla or Partimage.

ps: His tutorials on installing 100+ operating systems on one computer are interesting reading to say the least !

I think you mistook one of my posts as bad talking Saikee? 

Definitely didn't say anything bad about them, if anything I give them big thanks for helping us out. You're mistaken.

---

### Post by uncle-c on 2010-02-23
Sorry dude, I think the wording of my post was ambiguous to say the least.  I just wanted to comment on Saikee and the credibility of his posts. I didn't want to sound as if I was annoyed at  you or anyone so aplogies if it came out like that !
I'm in the process of "dd cloning" one of my servers now so will raise a glass of fine wine to toast our friend !

---

### Post by trinaryouroboros on 2010-02-23
My bust, text: Confusing people since ancient Egypt.

:confused:

---


---
title: "External USB HDD (Drobo) won't mount anymore - bad journal?"
date: 2009-05-27
forum: General Help
---

### Post by jektal2 on 2009-05-27
Disclaimer: I'm a moderate linux newb.

I have a PC running Ubuntu 9, with an external HDD (a Drobo) attached via USB. The Drobo was originally formatted as NTFS and everything was good. Then after adding a few larger drives I exceeded the 2TB NTFS partition limit. I followed a guide ([http://drobo-utils.sourceforge.net/README.html](http://drobo-utils.sourceforge.net/README.html)) to rebuild the drobo using the drobom tools, and ended up with a working ext3 partition (LUN size 16TB, block size 256KB (I think)). 

Everything was working fine with the Drobo formatted as ext3 and mounted to Ubuntu via USB. I never modified fstab, the drive just showed up on the desktop after a few minutes, and was mounted successfully at /media/Drobo01 . Over the course of a few days I moved several hundred GB over to the drive from where I had it backed up (removing the backed up copies while I did so, like an idiot.)

Then something bad happened. My best guess is the apartment lost power and the PC had a hard reboot while the Drobo was in use. All I know is I came home and the Drobo was no longer mounted, and would no longer mount. 

After weeks of frustration, I installed an ext3 filesystem driver on my WinXP64 PC, and connected the Drobo. I immediately received a very verbose message telling me that the journal was corrupt, and suggested that I either run their recovery tools, or connect the drive to a Linux PC (which it implied would automatically repair the journal.) I attempted to use their repair tool, but was told it wouldn't work on a drive with a block size larger than 128KB (mine is set at 256).

Frustrated, but slightly more informed, I reconnected the drive to my Ubuntu PC to try and find a way to rebuild the journal. The problem is, as far as I can tell, Ubuntu can't see the damn thing at all.

After starting the Drobo and connecting it to the Ubuntu PC, almost immediately a new directory is created: /media/Drobo01 . Doing an "ls -l" in /media shows /media/Drobo01 as having full permissions in every category ("drwxrwxrwx 8 root users 4096 ..."), and the actual "Drobo01" text is displayed as dark blue on a green background inside the terminal. Changing into the Drobo01 directory and executing "ls" seems to time out with an Input/Output error

At the same time, executing "lsusb" lists two "root" hubs (I'm assuming internal, on the motherboard), and two other USB devices which are attached to the system.

Executing "sudo fdisk -l" shows 1 disk (/dev/sda, my internal boot HDD) and the 3 legit partitions on it. "sudo parted -l" yields the same.

Running "sudo mount -a" returns no output, and doesn't seem to have any effect.

After a few minutes, a dialog box will popup stating "Unable to mount Drobo01    DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)". Sometimes I will also get a dialog box stating "Could not find /media/Drobo01   . Please check the spelling and try again." After which I have tried manually creating /media/Drobo01 with the Drobo disconnected and then reconnecting it, which just appends a _1 to the directory it seems to be looking for in the error message.

After waiting several minutes, the /media/Drobo01 directory will disappear, and running "sudo mount -a" produces no output, even though the Drobo's USB connectivity light will remain on.

---

### Post by jektal2 on 2009-05-28
To clarify a bit... I'm fairly convinced that the problem is a corrupt journal on the USB HDD (the Drobo), but don't know how to go about repairing it.

More so, I don't know how to even identify the drive so that I could run some tool (like fdisk) on it to attempt a journal repair.

I'm assuming that it'd be assigned a 'name' like the internal drive (/dev/sda) when it's visible but inaccessible at /media/Drobo01 , but "fdisk -l" only lists the internal drive, and "lsusb" doesn't list it either.

Any help would be immensely appreciated, I really don't want to format the drives and start from scratch!

---

### Post by KhurramM on 2009-05-28
**Do this on your own risk...**

plug in the external usb device.

cat /proc/partitions

will show the newly hot plugged device.

CONFIRM THIS DEVICE IS nOT MOUNTED, then:

do:

fsck /dev/sdb1

or what so ever.

Hope this fixes your problem.

---

### Post by jektal2 on 2009-05-28
Well...

Thank you very much for the reply and info. "cat /proc/partitions" was VERY helpful. Using it I was able to see the device (/dev/sdb) and partition (/dev/sdb1) shortly after the Drobo was connected.

After being able to see the device, I tried running fsck and received an error, suggesting to use e2fsck instead. Doing so on /dev/sdb1 after it appeared in the cat /proc/partitions seems to have started working correctly, yielding the output "Drobo01: recovering journal"

However... After about a minute or two the Drobo restarted itself, and e2fsck failed with the following errors:

"e2fsck: Attempt to read block from filesystem resulted in short read while trying to re-open Drobo01
e2fsck: io manager magic bad!"

(Seriously, that's what it says.)

The Drobo would then cycle through it's normal startup routine and reappear in the devices list as before. Repeating e2fsck would replicate the exact same output as above, and the Drobo would restart. I went through this process about 5 times.

At this point, I'm assuming that the Drobo is interrupting e2fsck, which would otherwise work correctly.

I'm fed up with this and frustrated enough that I'm going to pull each drive out, format it, reinsert it in the drobo, reformat again, and start all over. This time though I'll be sure to avoid a journaled filesystem, and hopefully any future failures will allow for easier recovery...

---

### Post by BrowneR on 2009-06-29
Hi jektal,

I have just purchased a Drobo from ebay and while I'm waiting for it to arrive have been doing some reading around the supported file systems. I stumbled across your post here and might be able to give you some advice based on what I've read so far... sorry if this is a bit long winded.

It seems Drobo support for the ext3 Linux file system is still in development (it says beta on the Drobo website) and some features are not fully supported yet. One of the current limitations is that setting a LUN size greater than 2Tb (you set 16Tb right?) leads to file system corruption and data loss. Basically it sounds like this is bad news for your data...

The way I see it there are two main options for using Drobo with Linux (with the current firmware 1.3.0):




[INDENT]**Option 1**) Keep your LUN size set to 4/8/16Tb but don't use ext3! Your other options for a filing system are NTFS, FAT32 or HFS+.

[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

I guess NTFS would be the most suitable provided you have access to a windows machine in case you ever need to run CHKDSK on the drive to fix errors***** (there is only limited NTFS repair functionality available to linux - "[ntfsresize -fi]("http://www.linux-ntfs.org/doku.php?id=ntfsck")").

The 2Tb NTFS limit you mention is in fact a limitation imposed by the master boot record (MBR) not NTFS itself. Because partition tables on MBR disks only support partition sizes up to 2 TB, GPT volumes must be used to create NTFS volumes over 2TB. *****Unfortunately while linux (kernel >2.6.24) can read these fine, windows XP 32bit cannot read GPT disks ([vista and XP 64bit can]("http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx")) - not sure if that's an issue for you? Also means you cannot use XP to repair the file system though. The [drobo-utils]("http://drobo-utils.sourceforge.net/") program for Linux should be able to create a GPT NTFS partition for you with a LUN up to 16Tb.

FAT32 ain't going to play nice with anything over 2Tb and thats overlooking all its fragmentation, case insensitive, file permissions problems.

HFS+ (mac filing system) is another option. Apparently (I have not tested it) it can be read and written by the Linux kernel and I believe you can install hfsprogs to provide the "fsck.hfsplus" file system recovery tool. It is a modern journaled filing system that seems very feature rich and supportive of large files and volumes. Worth a look especially if you also use a mac from time to time.

**Option 2**) Your second option is to reduce the LUN size to 2Tb and then use the filesystem of your choice - ext3 or otherwise.

This way your drobo will show up as a 2Tb drive and as more capacity is added additional LUN's will be created automatically and appear as separate devices in Ubuntu, each with a fixed 2Tb size.

ie. if you have 3Tb of space available on your Drobo you will see for example /dev/sdb with size 2Tb and /dev/sdc with size 2Tb. You will be able to fill one of these volumes to the 2Tb limit and the other to 50% capacity before the Drobo's lights indicate it is full. Adding additional space will simply create more 2Tb LUN's (/dev/sdX).[/INDENT]




Hopefully Data Robotics are working on resolving the issues with ext3 and a LUN size >2Tb and that linux support will then come out of beta in the future. It would have been nice of them to fully explain all these limitations on their website somewhere rather than leaving users to work things out themselves and suffer huge data loss as a consequence. It also seems strange the drobo-utils program doesn't seem to mention any of this in its documentation...

I hope you found that useful and if not it at least means my evenings research is now documented somewhere for future google searches to find.

Like I said before, I have not tried any of this myself but this is the information I have picked up from the many blogs and forums that I have been reading today.

I think I'll be going for option 2 - with a good deal of testing before I put anything too precious on there.

Cheers, Chris

---

### Post by jesterfred on 2010-01-11
I have a DroboS with 5 1TiB drives in it formatted with ext3 and using 2 TiB LUNs.  I recommend against ext3 as I have now suffered multiple DroboS crashes.  That is the DroboS itself crashes and I must power it off then back on by unplugging it to fix.  IN most cases the filesystem journal puts the file system back into working condition.  But, on one occasion it did not and I lost all the data on the disk.  Fortunately I am still in the distrust stage so lost nothing important.

I am now attempting NTFS.  Hopefully, they will get ext3 support through their quality assurance program and directly support it soon.

---

### Post by Baneblade on 2010-03-21
Could I get an update on how you guys are coping with Drobo on 'nix now please?

Iv had one for a while connected to my windows gaming system, but have recently got hold of some old 'nix servers which im fixing up in the hopes of deploying Drobo to one of them.

Currently formatted to 8TB NTFS, but iv always had issues with Ubuntu writing directly to NTFS in the past, so im very wary of connecting it up.

---

### Post by BrowneR on 2010-03-22
Hi Baneblade,

I have a gen2 drobo which I use with my Ubuntu system via usb. Mine is formatted NTFS (2TB LUN) which I think is definitely the way forward. Ext3 still seems too poorly supported by Drobo to be considered safe.

I use mine for backups only and so it is only plugged in maybe once a week. However during that time I then run a number of large rsync jobs on it and regularly transfer many gigabytes of data to the device. So far I have never had a single problem. 

Reading/writing data to the NTFS file system is handled flawlessly by the NTFS-3G driver that Ubuntu uses and I believe this driver is considered to be very stable and safe now. I literally just plug it in and go.

The only thing you have to look out for with NTFS is the loss of file permissions that occurs due to filesystem limitations. So if you want to keep all your ext3 permissions on your backups then it's best to put them in a tar archive first. For most personal and non-system files this isn't an issue though.

Basically I wouldn't hesitate to plug your drobo into your Ubuntu system although I would maybe run a full chkdsk on it from Windows to make sure the file system is clean periodically. Other than that just make sure you follow the safe shutdown procedure when disconnecting drobo and you shouldn't have a problem (the droboutils package helps with this).

Hope that helps you out.

Chris

---

### Post by manishmahabir on 2010-04-02
i got my drobo today...planning to use it with tonido plug as network attached storage. i mostly use an ubuntu box..might be accessing drobo from windows in virtualbox.
do you recommend formatting it as 8 tb ntfs drive?

---

### Post by BrowneR on 2010-04-02
NTFS would be my first choice. 8Tb should be fine.

---


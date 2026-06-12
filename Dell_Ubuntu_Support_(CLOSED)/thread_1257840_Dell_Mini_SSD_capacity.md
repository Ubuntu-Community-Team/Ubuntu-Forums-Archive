---
title: "Dell Mini SSD capacity"
date: 2009-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bofak on 2009-09-04
A few months ago I ordered a Dell Mini 910 with 4GB SSD and Ubuntu 8.04 pre-installed.

When it arrived it had well over 6GB of drive capacity, according to Disk Usage Analyzer (unfortunately I didn't record the exact amount) but was packed with material I didn't want, much of it Dell proprietary stuff, and had very little free space.  In fact when I followed the advice to go online and run an update, I quickly got a Drive Full warning.  So I set about removing masses of junk.

This was when I discovered that Linux is much less idiot-safe than Windows, especially if the idiot is the owner (I'm a complete novice with Linux) and I ended up making the system unworkable.:(

Instead of reinstalling from the disk that Dell had provided, I decided to go for Jaunty 9.04, so I downloaded something called "Ubuntu Netbook Remix" (I assume that just means a collection of components considered suitable for running on a netbook) and installed that.

I'm very pleased with it.  Unlike the Dell mixture, the System is very neat and small (as I always expected from Linux), I have more free space, and I've learned the proper way to remove components I don't want, so I keep slimming it down.

The mystery that puzzles me is that Disk Usage Analyzer now tells me that my total filesystem capacity is 3.3 GB, of which I have 1.3 free.  This is plenty for my purposes (travelling computer), but my question is this:  How did my drive capacity come to be cut by something like half, from much more than I had expected to less than I expected?  Is there space in that SSD that can be used by Dell for stuff they want to push at me, but is not available for other uses?:confused:

---

### Post by snowpine on 2009-09-04
Hi Bofak, 

Dell never should have offered 4gb as an option; it's simply too small for a modern operating system. Just my opinion; now, on to your problem! :)

The following terminal (Applications->Accessories->Terminal) command will list your partitions (how your drive is set up):

```
sudo fdisk -l
```

Please copy and paste the output here so we can take a look.

The reason your filesystem appeared to be 6gb that one time was probably because you had another drive mounted, like a USB flash drive or SD card.

---

### Post by ugm6hr on 2009-09-04
> **bofak said:**
> The mystery that puzzles me is that Disk Usage Analyzer now tells me that my total filesystem capacity is 3.3 GB, of which I have 1.3 free. 

This is about right.

I have no idea what happened when you had 8.04, but you clearly never actually had 6GB (since the hardware only has 4GB).  Likely to have been an error with Disk Analyzer.

As for why only 3.3GB (and not 4GB): did you use the automated install option?  If so, you have created a swap partition of about 600MB.  SSD drives theoretically can have a shorter lifespan if you use swap (hence, I did not).

Other than that, formatting a drive with ext3 (a journalling file system) always reduces the amount of available space.

So, I wouldn't worry about where the lost space has gone, although I would suggest removing the swap partition if you did create one (unless you need hibernate to work).

As snowpine said - 4GB is really too small; Dell should never have sold it in that configuration (they didn't in the UK).

---

### Post by bofak on 2009-09-04
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot-2.jpg[/IMG][IMG]file:///tmp/moz-screenshot-3.jpg[/IMG][IMG]file:///tmp/moz-screenshot-4.jpg[/IMG][IMG]file:///tmp/moz-screenshot-5.jpg[/IMG]Thanks, guys, for the prompt responses.  The following is the output for the command suggested by snowpine.  Please help me interpret it because it means nothing to me.  (BTW in real life I'm called John.)

john@john-laptop:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e73b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         433     3478041   83  Linux
/dev/sda2             434         460      216877+   5  Extended
/dev/sda5             434         460      216846   82  Linux swap / Solaris
john@john-laptop:~$ 
john@john-laptop:~$

---

### Post by ugm6hr on 2009-09-04
That means:

1. Your SSD is 3791MB (i.e. 4GB pre-formatting and 1000 vs 1024 kB/MB conversion)

2. You have a swap partition of around 215MB.

3. Your main partition is 3568MB (i.e. around 3.3GB)

As I explained, you are not missing any MB.

---

### Post by bofak on 2009-09-04
Let me clarify my thinking on all of this.

The reason for not having a swap partition is to avoid having a disproportionate amount of write activity to one small part of the drive?

If I removed the swap partition, would the space simply be added to my main partition?

What would be the consequences of this, other than losing hibernate, which I don't  use?

How would I do it?

I appreciate your patience in helping me with all of this.  I realize now that I'm not missing any drive space.

---

### Post by ugm6hr on 2009-09-04
SSDs have a limited number of writes.  Swap partitions have multiple writes all the time, although with 1GB RAM, it would be used relatively infrequently unless you developed a memory leak or similar.  Nevertheless, I chose not to use swap.

As mentioned, hibernate will not work if you remove swap; suspend will (although if you have an SD card mounted at the time, it crashes).  There are no other consequences, unless you frequently use multiple apps that require more than the 1GB RAM (NB: FF, Evolution, Rhythmbox and OpenOffice can all be open at the same time with 1GB RAM).

As to how to remove it - I should admit I have never done that.  I chose not to have a swap partition at the time of installation, so I am uncertain exactly what changes are required to remove it after installation.  I suspect an edit of fstab and deleting the partition will suffice, but don't want to advise you to do this in case it makes a mess.

If you remove it, you can either leave the spare partition as a separate storage area or you can add it to the main Ubuntu partiton.

Hope that explains it.  If you want to pursue removing swap, hopefully someone else will be able to confirm the exact procedure.

---

### Post by shiningkenmonster on 2009-09-04
did you know Disk Analyzer reports the free space on your harddrive and a SD card reader at the sametime. well thats what i notice for the dell's ubuntu 8.04 for the dell mini 9. 

So i assume you had a 2GB or 4GB SD card in your dell mini when you used the Disk Analyzer. Probably used up some of the diskspace and had an odd higher number over all.

thats what i did too!

---

### Post by jaqrah on 2009-09-05
Here is a link that should provide guidance in removing your swap partition.

[http://ubuntuforums.org/archive/index.php/t-454045.html](http://ubuntuforums.org/archive/index.php/t-454045.html)

Keep in mind the part about the LiveCD using the swap partition.  Download gparted and create a bootable usb thumbdrive or burn to disc and boot with external usb cd/dvd drive.

Also, backup your data first in case you make a partitioning error.  Also, link to a simple partitioning tutorial if you are new to partitioning.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

good luck

---

### Post by Greyed on 2009-09-05
> **ugm6hr said:**
> As snowpine said - 4GB is really too small; Dell should never have sold it in that configuration (they didn't in the UK).

With the presumption that it is the only media on which you will work.  4Gb is large enough for the base OS.

```

{grey@grey:~} df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             107G  4.2G   98G   5% /
{grey@grey:~} free -m
             total       used       free     shared    buffers     cached
Mem:          1000        826        174          0         50        381
-/+ buffers/cache:        395        605
Swap:          511          0        511

```

Note that while my OS takes up 4.2Gb that includes my 500Mb swap file and some data I have put on the drive since...

Once that OS us up the email/web can be accessed which is precisely what these Netbook class machines were originally billed for.  If one needed to store/manipulate larger files one can simply plug in a much larger USB drive on which the actual data is stored/manipulated.  If I recall the marketing around that time the external USB drives were pushed heavily for the SSD Minis precisely because people are not used to thinking of operating in contraints of <40-80Gb....  That is soooo 2000.  ;)   4Gb, 8Gb, 16Gb, all are far smaller than what people are now used to.

---

### Post by ugm6hr on 2009-09-05
> **Greyed said:**
> With the presumption that it is the only media on which you will work.  4Gb is large enough for the base OS.

For 9.04 NBR - Yes.  Probably still best to keep things updated regularly and not keep all the old .debs (i.e. run **sudo apt-get clean** from time to time).

For the default Dell Ubuntu 8.04 NBR - No.  Look at the mydellmini forum, and you will see that there were lots and lots of people who had similar problems due to the release of multiple updates at the same time, which downloaded, but would then not install due to a full / partition, and also appeared to cause issues with FF (for some bizarre reason, presumably relating to its use of a cache).

I would also recommend keeping personal files / data on an external SD card (as I do, despite my 8GB SSD); Sd cards sit flush to the case while USB flash drives do not.  4-8GB SDHC cards are so cheap there is no excuse!  Additionally, set up IMAP (rather than POP) for email, or use a webmail service.

@ Greyed: Interesting you choose to use a swap file rather than swap partition.  Is there any advantage to it?

---

### Post by Greyed on 2009-09-05
> **ugm6hr said:**
> For 9.04 NBR - Yes.  Probably still best to keep things updated regularly and not keep all the old .debs (i.e. run **sudo apt-get clean** from time to time).

Oooo, true, I hadn't thought of large updates via apt...

> @ Greyed: Interesting you choose to use a swap file rather than swap partition.  Is there any advantage to it?No advantages, just no disadvantages, either.  Having the swap file on a partition of its own because of the inefficiencies of hitting the file system is an old-school Linux truism which no longer applies.  Besides, when you're hitting the hard drive whose access is measured in ms as opposed to RAM measured in ns it's not the time to quibble about a few ms here or there for added access; you've already increased your timing by over a magnitude.

But the real reason in this case is simple, my 10v didn't ship with a swap partition.
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe611e8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4       14410   115724227+  83  Linux
/dev/sda3           14411       14593     1469947+  1c  Hidden W95 FAT32 (LBA)

```I'm not sure what sda1 or sda3 are.  Besides, sda1 is too small and sda3 is too large.  So I could go through the whole process of reinstalling or repartitioning and resizing the file systems or I can just...

```

dd if=/dev/zero of=swap1 bs=1M count=512
mkswap swap1
swapon swap1

```I am, at my core, lazy.  ;)

But all of my machine's specs are for an HDD and not really germane to the main part of this discussion.   Nothing to see here, carry on!  :D

---

### Post by bofak on 2009-09-05
Thanks, Jaqrah, for those suggestions, which I will look at carefully.  I notice that you are trying out Karmic, and I'll probably upgrade to it when it is finalized.  That might be a good time to do an install without the swap partition, rather than messing about now.  At my last install I didn't notice that this was an option.

I am following the rest of this discussion with interest because there are various things in there that I should know.  Being a complete Linux novice I have never met the command **sudo apt-get clean.  **What will this do for me?  Sounds useful!

I think I'll keep my problems with multiple updates for a whole new thread.  Update Manager keeps wanting to fill every scrap of space I've got.:(

---

### Post by ugm6hr on 2009-09-05
> **bofak said:**
> Being a complete Linux novice I have never met the command **sudo apt-get clean.  **What will this do for me?  Sounds useful!

Every time you run an update (whether from the Terminal - recommended - or the Update Manager), all the updates are initially downloaded to /var/cache/apt/archives/

Once downloaded, they are then sequentially installed.

Hence the problem with multiple updates at the same time (e.g. after an initial install) - all the downloads (kernels can be quite large) fill the HD (or SSD in the case of the Mini 9), which leaves no room for them to actually be installed.

**sudo apt-get clean** just deletes everything in /var/cache/apt/archives - if you want to keep them, just backup or use rsync to copy everything to a USB flash etc, and then run the command.

It is recommended to keep Ubuntu up-to-date for security and bug fixes.  If you are worried about a repeat of what happened before, try the following procedure to maintain complete control over everything:

Put a USB flash in; assuming it has no label, it will *mount* at /media/disk (if it has a label, it wil be /media/label - replace below as appropriate). 

Install rsync (it is useful):
```
sudo apt-get install rsync
```

Then:
```

sudo apt-get update
sudo apt-get upgrade -d
rsync -rlptoDv --modify-window=120 /var/cache/apt/archives /media/disk/
sudo apt-get clean
cd /media/disk/
ls
sudo dpkg -i *.deb
sudo apt-get install -f
```


If you want to know what that does (as you should - never blindly copy commands, everyone makes typos which can be disastrous when run with sudo):

> updates the repository list
downloads (but doesn't install) all identified updates
rsync backups all downloaded update .debs from the local SSD directory to your USB flash drive
deletes all downloaded update files from SSD
change directory to USB flash
lists all the copied .debs (just to double-check they are in the right place!)
installs all .deb files from USB
checks there are no problems with the above install, and downloads and installs any further required .debs

If you do this at this stage, you should be OK to just use the Update Manager in the future on a weekly (or more frequent) basis, provided you continue to use apt-get clean (& use rsync to backup .debs before, if you want).

I know that all seems a bit overly complex, but it is worth persevering.

NB: I have assumed USB flash is formatted vfat, although it would be better to use ext2/3 if it is to be dedicated to storing your .deb update files (due to rsync's problems with vfat).

---

### Post by Montala on 2009-09-06
> **ugm6hr said:**
> If you want to know what that does (as you should - ever blindly copy commands, everyone makes typos which can be disastrous when run with sudo):
Thanks for a very useful post, which helps to explain exactly what is going on... very useful for beginners such as myself!
 
I shall be trying it out myself later this morning to hopefully clear out some of the 'dross' which would have been left behind after I updated Pidgin, and was informed that there were then 199 updates to be downloaded and installed... which I did! Luckily I have a 16GB SDD on my Mini 10v!
 
I couldn't help having a chuckle to myself though, when I read the sentence, quoted above, as the word 'ever' should, I assume be 'never'... as you say, "everyone makes typos" ! :D

---

### Post by ugm6hr on 2009-09-06
> **Montala said:**
> I couldn't help having a chuckle to myself though, when I read the sentence, quoted above, as the word 'ever' should, I assume be 'never'... as you say, "everyone makes typos" ! :D

Oops  :redface:

Of course, that was a deliberate mistake, just to see if you were paying attention ;)

Original edited...

---


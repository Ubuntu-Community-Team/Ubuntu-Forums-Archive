---
title: "Cannot Mount &gt; 4GB DVDs"
date: 2006-07-01
forum: Desktop Environments
---

### Post by crroush on 2006-07-01
The problem I am running into is that for data DVDs with data just a bit over 4GB I cannot mount.  The DVD and drive work fine when I am in windows, and the DVD drive will mount data DVDs long as they are less than 4GB.  

From my kern.log file when I attempt to mount the drive
> Jun 29 13:52:47 localhost kernel: [17179743.040000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'VIDEOSAMPLE1_1', timestamp 2004/11/23 10:49 (1f10)
Jun 29 15:45:03 localhost kernel: [17186478.188000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 15:45:03 localhost kernel: [17186478.188000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
Jun 29 15:45:03 localhost kernel: [17186478.188000] ide: failed opcode was: unknown
Jun 29 15:45:03 localhost kernel: [17186478.188000] end_request: I/O error, dev hdb, sector 862600
Jun 29 15:45:03 localhost kernel: [17186478.188000] Buffer I/O error on device hdb, logical block 215650
Jun 29 15:45:09 localhost kernel: [17186484.152000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 15:45:09 localhost kernel: [17186484.152000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
Jun 29 15:45:09 localhost kernel: [17186484.152000] ide: failed opcode was: unknown
Jun 29 15:45:09 localhost kernel: [17186484.152000] end_request: I/O error, dev hdb, sector 862604
Jun 29 15:45:09 localhost kernel: [17186484.152000] Buffer I/O error on device hdb, logical block 215651
Jun 29 15:45:09 localhost kernel: [17186484.356000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 15:45:09 localhost kernel: [17186484.356000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
Jun 29 15:45:09 localhost kernel: [17186484.356000] ide: failed opcode was: unknown
Jun 29 15:45:09 localhost kernel: [17186484.356000] end_request: I/O error, dev hdb, sector 862608
Jun 29 15:45:09 localhost kernel: [17186484.356000] Buffer I/O error on device hdb, logical block 215652
Jun 29 15:45:09 localhost kernel: [17186484.356000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 15:45:09 localhost kernel: [17186484.356000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
Jun 29 15:45:09 localhost kernel: [17186484.356000] ide: failed opcode was: unknown
Jun 29 15:45:09 localhost kernel: [17186484.356000] end_request: I/O error, dev hdb, sector 862612
Jun 29 15:45:09 localhost kernel: [17186484.356000] Buffer I/O error on device hdb, logical block 215653
Jun 29 15:45:09 localhost kernel: [17186484.360000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 15:45:09 localhost kernel: [17186484.360000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
Jun 29 15:45:09 localhost kernel: [17186484.360000] ide: failed opcode was: unknown

I am using kernel 2.6.15-25-386 and Dapper Drake 6.06.

---

### Post by crroush on 2006-07-14
I guess I will continue to post to myself, just for documentation reasons or something like that.  I have tried a host of different things, from turning on and off DMA, to compiling the vanilla Kernel from kernel.org.  None of these things have solved this issue.  It seems that 4 gb boundry problem still exists, or I simply don't know what to do to work around it.  I have played with BIOS, made sure it had LBA enabled for the drive, I removed the primary drive and made it the primary drive and the only IDE device on the controller.  I am not sure where to turn to next, other than reboot to windows everytime I need to access a data cd that is > than 4 GB.  Hopefully, someone out there less ignorant than me has a few suggestions on this manner.  I am almost to the point to declare it a lost cause........

---

### Post by Kashirigi on 2006-08-08
At least I'm not the only one with this problem. 

My laptop with Dapper installed has no problem reading DVDs, but the desktop (on which they were burned -- oh  the irony) can't read them. fstabs are the same.

---

### Post by orb9220 on 2006-08-08
Do you have?
libdvdcss2 installed?
Simple foundation for reading DVDs - runtime libraries
To allow applications to access some of the more advanced features
of the DVD format.

libdvdread3 installed ?

Simple foundation for reading DVDs
To allow applications to access some of the more advanced features
of the DVD format, libdvdread offers:

1. A simple abstraction for reading the files on a DVD image
  (dvd_reader.h).
2. A simple library for parsing the information (IFO) files
  (ifo_read.h/ifo_types.h).
3. A simple library for parsing the navigation (NAV) packets
  (nav_read.h/nav_types.h).

libdvdread currently uses libdl to dynamically probe for libdvdcss at
runtime, if found, libdvdcss will be used to decrypt sections of the
DVD as necessary

Did you use easy ubuntu or Automatix to install all necessary codecs?

Just throwing out some idea's since I am new to this. 
Hope you find a solution.

---

### Post by clint1010 on 2006-08-08
I had the same problem. I had backed up all data on a number of DVDs, when inserting the disk, it would not mount. I did the following, and it auto mounts every time.

From a terminal;
sudo gedit /etc/fstab

put a # infront of the last line that will look something like this;
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

so now it looks something like this;
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

this will coment the line out so it will not be recognised, save and close fstab file. You can always go back and remove the # so fstab returns to its original state.

Then from the terminal;
sudo mount -a

Now try your DVD, it works a charm for me. 

Good luck

---

### Post by drewbie on 2006-08-08
I have the same problem not being able to mount data dvds and some movie dvds, have all the codecs etc and have tried the lines 

/dev/hdc        /media/cdrom0   udf,iso9660    user,noauto 0 0
and
/dev/hdc        /media/cdrom0    auto            user,noauto   0 0
 in my fstab, but still nothing will get ubuntu to read them

---

### Post by Tamihania on 2006-08-08
> **drewbie said:**
> I have the same problem not being able to mount data dvds and some movie dvds, have all the codecs etc and have tried the lines 

/dev/hdc        /media/cdrom0   udf,iso9660    user,noauto 0 0
and
/dev/hdc        /media/cdrom0    auto            user,noauto   0 0
 in my fstab, but still nothing will get ubuntu to read them

...I have exactly the same problem...trying to solve it on my own for couple of days now...have all codecs...trying to change fstab - nothing helps...

Can anybody drop us a line...? a hint maybe - please[-o<

tami

---

### Post by Kashirigi on 2006-08-09
My problems were solved when I realized that it was a hardware, rather than a software problem. No OS could read DVDs from the drive -- I replaced it with a better one and all was well, except for the cursing trying to install it in my poorly designed case.

I guess I'm not used to spontaneous hardware failures.

---

### Post by drewbie on 2006-08-09
> **Kashirigi said:**
> My problems were solved when I realized that it was a hardware, rather than a software problem. No OS could read DVDs from the drive -- I replaced it with a better one and all was well, except for the cursing trying to install it in my poorly designed case.

I guess I'm not used to spontaneous hardware failures.

But my windows partition can read the dvds, and i am quite sure breezy used to be able to as well i think

---

### Post by crroush on 2006-08-19
If I boot to windows I have no problems reading the data DVDs that are greater than 4GB.  If I try to mount on my kubuntu partition I got all the errors I posted above.  If I put a regular CD or a DVD that is less than 4 GB works like a charm.  This seems to be some type of driver problem in Linux.  I have tried everything that was posted in this thread above, with zero success.  Only thing I have not done is uninstall the drive and install it in my Mandrake box to see if I get the same results.  Since I had the windows partition, I ended up reading all the data in windows, rebooting and snagging it off my windows partition.  

But I would love a linux solution!  Windows is annoying.

---

### Post by clint1010 on 2006-09-20
Did you try the following procedure from my previous post?
effectivly this will coment out the refered line with a "#" so the OS wont read that line.


From a terminal;
sudo gedit /etc/fstab

put a # infront of the last line that will look something like this;
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

so now it looks something like this;
#/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

this will coment the line out so it will not be recognised, save and close fstab file. You can always go back and remove the # so fstab returns to its original state.

Then from the terminal;
sudo mount -a

---

### Post by mojoman on 2006-09-23
I might be totally in the dark here but what file system do you guys use? If I'm not mistaken, FAT32 have a limit on filesize which I think just happens to be 4 GB so maybe...
/mojoman

---

### Post by crroush on 2006-10-01
> 
From a terminal;
sudo gedit /etc/fstab

put a # infront of the last line that will look something like this;
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

so now it looks something like this;
#/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

this will coment the line out so it will not be recognised, save and close fstab file. You can always go back and remove the # so fstab returns to its original state.

Then from the terminal;
sudo mount -a

Yes I have tried all variations of this, it seems very odd that it is right at the 4GB limit that was a big pain for bios' in the late 90's.  I do not know how the DVD data disks were burned.  But they still work fine under windows, so I am still at a loss.  I haven't had much time in the last month to revisit the issue.  It still doesn't work as of today.

---


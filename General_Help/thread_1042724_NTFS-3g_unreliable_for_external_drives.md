---
title: "NTFS-3g unreliable for external drives?"
date: 2009-01-17
forum: General Help
---

### Post by thomasyen on 2009-01-17
I recently acquired a 640 GB external enclosure drive, with the partitions formatted to NTFS. However, I found out (rather painfully, with some data lost) that NTFS-3g seems to be unreliable for external enclosures. Whenever I transfer folders a few GB in size to the drive, NTFS-3g gives an I/O error, drops whatever was being transferred at the time, and forces me to use chkdsk in Windows to fix the disk errors. I'm quite sure that this is not hardware-related, as the drive works fine under Windows XP. NTFS-3g works fine for my internally-mounted drives, but not for external enclosures. Does anyone else have the same problem? And, should I report this as a bug?

---

### Post by Yashiro on 2009-01-17
I have a Seagate Freeagent Desk 500G connected via USB2.
It's formatted as one NTFS partition and used as a networked movie share via my Ubuntu Hardy installation.
Problem free for at least 6 months.

> *NTFS-3g works fine for my internally-mounted drives, but not for external enclosures*So it's not the 3g driver in itself but something involving file transfers to this drive using 3g. Sounds more like a USB/whatever interface problem.

---

### Post by ju2wheels on 2009-01-17
I use NTFS on my external over usb without a problem. I would recommend you upgrade your ntfs-3g (you may have to compile and install it manually to get the latest version depending on which version of Ubuntu you are using...).

I recall helping someone a while back who had similar NTFS corruption issues and it was due to using an old version of ntfs-3g.

---

### Post by solitaire on 2009-01-17
I've never had problems using NTFS-3g. The only reason i don't currently use it (just EXT3 drives) is the speed of data transfer between my laptop and External drive! Also I don't currently use windows (actually deleted it from my Comp to make room for my "/home" partition.) ;)

I'm going to do a speed test between data transfer to a fat32 and NTFS drive, it would be an interesting personal experiment. :D

---

### Post by lavinog on 2009-01-18
I think it is a usb issue
what does dmesg say after you do a large transfer
are you using 64bit or 32 bit...there are many posts about 64bit high speed usb drivers having issues.

---

### Post by thomasyen on 2009-01-18
I'm currently using Intrepid, I'm not sure if it's using the latest ntfs-3g by default.
   I'll post an error log (from dmesg) the next time I get this problem. Thanks!

---

### Post by lavinog on 2009-01-18
> **thomasyen said:**
> I'm currently using Intrepid, I'm not sure if it's using the latest ntfs-3g by default.
   I'll post an error log (from dmesg) the next time I get this problem. Thanks!

which intrepid? 64bit or 32 bit?

---

### Post by thomasyen on 2009-01-18
Intrepid 32-bit for x86.
Here are the relevant logs (I got the error again today):
daemon.log:
```

Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop hald[5490]: forcibly attempting to lazy unmount /dev/sdc3 as enclosing drive was disconnected
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: Error reading $Mft record(s): Input/output error
Jan 19 10:00:13 thomasyen-desktop ntfs-3g[7086]: ntfs_mft_record_read failed: Input/output error
Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc3 from '/media/Ubuntu backup' on behalf of uid 0
Jan 19 10:00:14 thomasyen-desktop hald[5490]: forcibly attempting to lazy unmount /dev/sdc2 as enclosing drive was disconnected
Jan 19 10:00:14 thomasyen-desktop ntfs-3g[7093]: Unmounting /dev/sdc2 (Windows backup) 
Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc2 from '/media/Windows backup' on behalf of uid 0
Jan 19 10:00:14 thomasyen-desktop hald[5490]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
Jan 19 10:00:14 thomasyen-desktop ntfs-3g[7086]: Unmounting /dev/sdc1 (Archive) 
Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc1 from '/media/Archive_' on behalf of uid 0

```
syslog:
```

Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc3 from '/media/Ubuntu backup' on behalf of uid 0
Jan 19 10:00:14 thomasyen-desktop hald[5490]: forcibly attempting to lazy unmount /dev/sdc2 as enclosing drive was disconnected
Jan 19 10:00:14 thomasyen-desktop ntfs-3g[7093]: Unmounting /dev/sdc2 (Windows backup) 
Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc2 from '/media/Windows backup' on behalf of uid 0
Jan 19 10:00:14 thomasyen-desktop hald[5490]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
Jan 19 10:00:14 thomasyen-desktop ntfs-3g[7086]: Unmounting /dev/sdc1 (Archive) 
Jan 19 10:00:14 thomasyen-desktop hald: unmounted /dev/sdc1 from '/media/Archive_' on behalf of uid 0

```
messages.log:
```

Jan 19 10:00:13 thomasyen-desktop kernel: [  569.792330] usb 5-6: device firmware changed
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793027] usb 5-6: USB disconnect, address 9
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793642] sd 6:0:0:0: Device offlined - not ready after error recovery
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793677] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793690] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793700] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793706] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793712] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793719] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793725] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793731] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793737] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793742] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793748] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.798604] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 19 10:00:13 thomasyen-desktop kernel: [  570.020564] usb 5-6: new high speed USB device using ehci_hcd and address 10

```
By the way, my enclosure has two NTFS partitions (Archive and Windows backup) and one ext3 partition (Ubuntu backup). Should I compile the latest NTFS-3g from source?

---

### Post by ju2wheels on 2009-01-18
[http://www.ntfs-3g.org/support.html#ioerror](http://www.ntfs-3g.org/support.html#ioerror)

Your output seems to fall along the lines of the errors described there.

I believe Intrped shipped with ntfs-3g version 1.2506 so you can see if upgrading it manually helps. If not then it might be driver related as the link above describes.

```

wget http://www.ntfs-3g.org/ntfs-3g-1.5130.tgz
tar xvfz ntfs-3g-1.5130.tgz
cd ntfs-3g-1.5130/
./configure
make
sudo make install

```

---

### Post by tech0007 on 2009-01-18
> **thomasyen said:**
> Intrepid 32-bit for x86.
messages.log:
```

Jan 19 10:00:13 thomasyen-desktop kernel: [  569.792330] usb 5-6: device firmware changed
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793027] usb 5-6: USB disconnect, address 9
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793642] sd 6:0:0:0: Device offlined - not ready after error recovery
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793677] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793690] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793700] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793706] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793712] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793719] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793725] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793731] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793737] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793742] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.793748] lost page write due to I/O error on sdc1
Jan 19 10:00:13 thomasyen-desktop kernel: [  569.798604] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 19 10:00:13 thomasyen-desktop kernel: [  570.020564] usb 5-6: new high speed USB device using ehci_hcd and address 10

```
By the way, my enclosure has two NTFS partitions (Archive and Windows backup) and one ext3 partition (Ubuntu backup). Should I compile the latest NTFS-3g from source?

This error logs indicate that your external drive disconnects and then reconnects itself, which would suggest that it's a USB issue.

---

### Post by thomasyen on 2009-01-19
I've now installed the latest NTFS-3g from source. Haven't tested it yet, though. (I installed it from source without first removing the original NTFS-3g from Synaptic. Is that okay, or did I screw up?)
   If it really is a USB issue, does that mean I have to buy another, different enclosure?

---

### Post by tech0007 on 2009-01-19
Test the latest version of ntfs-3g first.  If you still get errors when copying, plug your external drive to another USB port or get a different enclosure.

---

### Post by Archmage on 2009-01-19
Did you consider using the ntfs-driver instead? Since Intrep this seams to work quite well. I never needed ntfs-3g.

---

### Post by lavinog on 2009-01-19
what brand/type of external enclosure are you using?
the link that ju2wheels posted has some interesting information about western digital mybooks

---

### Post by Yellow Pasque on 2009-01-19
> NTFS.. unreliable...
Yes. Yes, it is. :P

I would recommend a BIOS update to make sure there are no known USB issues (and experimenting with different physical USB ports, as suggested).

---

### Post by thomasyen on 2009-01-19
I'm using the same physical USB port for Ubuntu as the one for Windows XP. That's what's really confusing, because I had (close to) no problems under Windows, so it doesn't seem to be a hardware issue. (Or is Windows just silently fixing the errors in the background? Very occasionally I get an I/O error from Windows, stating that "Delayed writing failed, disk image damaged" or something similar.) I tried using another USB port, as suggested, but I still got the I/O errors. My drive is a Western Digital Caviar ,WD6400AAKS, and my enclosure is a CyberSLIM G70 (small Taiwanese company). Haven't updated BIOS yet, will do so when I can. Also, what's the ntfs-driver Archmage mentioned?

---

### Post by lavinog on 2009-01-19
The problem could be the enclosure.
Sometimes switching to a different usb port wont fix usb issues because some ports are on the same usb header.
Windows will not always tell you when there is is a device "hiccup"...sometimes you can look in the event logs to see error history that you wont normally get notifications of. (start>run>eventvwr.msc)
since you mentioned the delayed write issues in windows, it is likely that the problem is common to both OSes, and looks very much like a hardware issue and not the NTFS-3g driver.

---

### Post by tech0007 on 2009-01-19
> **thomasyen said:**
> 
Also, what's the ntfs-driver Archmage mentioned?


It's another way for linux users to access NTFS partitions. I myself switched from ntfs-3g to ntfsmount just recently. You can find out more about it in [http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by thomasyen on 2009-01-22
Thanks to you all! Looks like I'll be saving up for a new enclosure though.

---

### Post by phaedr_os on 2010-09-09
It is also unreliable for internal hard drives!
I have tried keeping files on large internal ntfs formatted hard drive to
be worked upon using programs from both windows and linux.
But eventually when in windows, u notice errors reported about this drive, and correct them but find: hey where did my myfiles folder go?
 
For limited usage, things may seem OK but - heavy long term usage, problems will show up.
 
Does anybody know whether a vfat formatted common drive (fat 32) would fare any better?

---


---
title: "Can't mount iPod -- Desperate!!"
date: 2005-12-15
forum: General Help
---

### Post by John Jason Jordan on 2005-12-15
It always auto-mounted before. Now I plugged it in but gtkpod can't see it. Turns out it is not mounted. But the iPod has the big "DO NOT DISCONNECT" warning in its screen. I tried "mount /media/iPod" and got "mount: special device /dev/sda2 does not exist." The man pages do not list this error message. What does it mean? Why didn't it auto-mount? And how can I disconnect it without destroying its filesystem, since the iPod seems to think it is mounted?

---

### Post by RAOF on 2005-12-15
The big "Do not disconnect" sign is hugely over-sensitive.  If your iPod is not mounted, then removing it won't trash the filesystem.  (Even if your iPod **is** mounted, removing it will *rarely* trash the filesystem ;))

It's possible that the kernel is assigning a different name to your iPod than usual.  Once you've plugged in the iPod, run "dmesg | tail" from a console.  That should give you some output like:
```
[ 1949.984138] ieee1394: sbp2: Logged into SBP-2 device
[ 1949.984229] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1949.985352]   Vendor: Apple     Model: iPod              Rev: 1.53
[ 1949.985357]   Type:   Direct-Access-RBC                  ANSI SCSI revision: 02
[ 1950.400241] sdc: Spinning up disk....ready
[ 1951.167868] SCSI device sdc: 78126048 512-byte hdwr sectors (40001 MB)
[ 1951.168722] sdc: test WP failed, assume Write Enabled
[ 1951.169008] sdc: asking for cache data failed
[ 1951.169015] sdc: assuming drive cache: write through
[ 1951.170405] SCSI device sdc: 78126048 512-byte hdwr sectors (40001 MB)
[ 1951.171258] sdc: test WP failed, assume Write Enabled
[ 1951.171544] sdc: asking for cache data failed
[ 1951.171546] sdc: assuming drive cache: write through
[ 1951.171548]  sdc: sdc1 sdc2
[ 1951.179330] sd 5:0:0:0: Attached scsi removable disk sdc

```

In this case, the kernel is calling my iPod "/dev/sdc", "/dev/sdc1", & "/dev/sdc2".  The three different names are for the ipod as a whole, the first partition (containing the ipod firmware and ipod system stuff), & the second partition (containing all the files on the ipod) respectively.

If you want to manually mount the iPod, you can run "sudo mount /dev/sd?2 /media/iPod", where you replace sd?2 with whatever your kernel is calling the iPod.

To get it to display the "ok to disconnect" sign, you can run "eject sd?" where you replace sd? with whatever the kernel is calling your iPod.

The program that usually automounts your iPod is called "gnome-volume-manager".  If your iPod is not auto-mounting, you could try running from the terminal:
```

killall gnome-volume-manager
gnome-volume-manager

```
and then plug in your iPod.  See if that helps.

---

### Post by John Jason Jordan on 2005-12-15
[QUOTE=RAOF]The big "Do not disconnect" sign is hugely over-sensitive.  If your iPod is not mounted, then removing it won't trash the filesystem.  (Even if your iPod **is** mounted, removing it will *rarely* trash the filesystem ;))
It's possible that the kernel is assigning a different name to your iPod than usual.  Once you've plugged in the iPod, run "dmesg | tail" from a console.  That should give you some output like: <snip>
In this case, the kernel is calling my iPod "/dev/sdc", "/dev/sdc1", & "/dev/sdc2".  The three different names are for the ipod as a whole, the first partition (containing the ipod firmware and ipod system stuff), & the second partition (containing all the files on the ipod) respectively.
If you want to manually mount the iPod, you can run "sudo mount /dev/sd?2 /media/iPod", where you replace sd?2 with whatever your kernel is calling the iPod.
To get it to display the "ok to disconnect" sign, you can run "eject sd?" where you replace sd? with whatever the kernel is calling your iPod.
The program that usually automounts your iPod is called "gnome-volume-manager".  If your iPod is not auto-mounting, you could try running from the terminal:
```

killall gnome-volume-manager
gnome-volume-manager

```
and then plug in your iPod.  See if that helps.[/QUOTE]
The one and only time I removed without unmounting it first (I forgot), it trashed the filesystem thoroughly. Had to get a Windows XP computer to reformat it, and lost a lot of files that I hadn't made backups for yet. This time I do have backups, but only the mp3s before I edited the tags and placed them on the iPod with gtkpod. Only a couple hours work to go back through and fix the tags if I lose them. Still, I'm very leery of touching it.

I did sudo dmesg | tail and got :
```

sdb: Mode sense: 64 00 00 08
sdb: assuming drive cache: write through
SCSI device sdb: 117210239 512 byte hdwr sectors (60012 MB)
   (this may be my computer's hard disk, as it is a 60 Gb, or it
   may be the iPod, which is also 60 Gb)
sdb: Write Protect is off
sdb: Mode sense: 64 00 00 08
sdb: assuming drive cache: write through
  /dev/scsi/host1/bus0/target0/lun0: p1 p2
Attached scsi removable disk sdb at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
usb 3-2: USB disconnect, address 3

```

So, assuming that sdb is the iPod, I tried "mount /dev/sdb" (and later -sdb1 and -sdb2) and all I get is
"mount: can't find /dev/sdb in /etc/fstab or /etc/mtab"

So then I tried "eject sdb" and got "unable to eject: last error: Invalid argument." I also tried "eject /dev/sdb" and even "eject /dev/sd*." The last one said "unable to find or open device for: sd*"

I didn't try killall gnome-volume-manager because wouldn't that also make it impossible to see my computer's hard disk?

Sorry to be such an idiot n00b here. :(

---

### Post by RAOF on 2005-12-15
The gnome-volume-manager is only for removable discs/cameras/ipods/etc.  Killing it won't hurt your ability to access local discs.

The reason why "mount /dev/sdb2" didn't work is because the iPod **does** have a different name to usual.  That command is a shorthand and uses the information in the file /etc/fstab.  Since your iPod has a different name to usual, the shorthand won't work.  You should still be able to mount it using the full command, here:
```
sudo mount /dev/sdb2 /media/iPod
```
The "sudo" is because normally only root can mount drives.  The /dev/sdb2 is the partition to mount, and the /media/iPod is **where** to mount it.

You could try "sudo eject sdb".  I'm not sure if that will help or not, though.  Try "eject -v sdb".  That will print out what it's trying to do, and maybe it'll be obvious how to fix it from that info.

---

### Post by John Jason Jordan on 2005-12-15
[QUOTE=RAOF]The gnome-volume-manager is only for removable discs/cameras/ipods/etc.  Killing it won't hurt your ability to access local discs.

The reason why "mount /dev/sdb2" didn't work is because the iPod **does** have a different name to usual.  That command is a shorthand and uses the information in the file /etc/fstab.  Since your iPod has a different name to usual, the shorthand won't work.  You should still be able to mount it using the full command, here:
```
sudo mount /dev/sdb2 /media/iPod
```
The "sudo" is because normally only root can mount drives.  The /dev/sdb2 is the partition to mount, and the /media/iPod is **where** to mount it.

You could try "sudo eject sdb".  I'm not sure if that will help or not, though.  Try "eject -v sdb".  That will print out what it's trying to do, and maybe it'll be obvious how to fix it from that info.[/QUOTE]
"Sudo mount /dev/sdb2 /media/iPod" gave me "mount: you must specify the filesystem." I know it is fat32, but don't know how to tell that to the mount command. "mount -help didn't help. :(

I tried killall gnome-volume-manager, which seemed to work, followed by gnome-volume-manager. That produced a long list of things, none of which seemed to have much to do with the situation except I saw a line that said "setting[5]: bool: autoipod = 0." Afterwards the iPod is still not mounted.

Then I tried "sudo eject sdb" and "sudo eject -v sdb." With the -v switch it gave the following, which may be of some interest:
```

eject: device name is 'sdb'
eject: expanded device name is '/dev/sdb'
eject: /dev/sdb is not mounted
eject: /dev/sdb is not a mount point
eject: /dev/sdb is a multipartition device
eject: unable to open '/dev/sdb'

```

I hope some of that gives a clue as to what is wrong.

---

### Post by RAOF on 2005-12-15
[QUOTE=John Jason Jordan]...
I tried killall gnome-volume-manager, which seemed to work, followed by gnome-volume-manager. That produced a long list of things, none of which seemed to have much to do with the situation except I saw a line that said "setting[5]: bool: autoipod = 0." Afterwards the iPod is still not mounted.
...[/QUOTE]
That should be done **before** plugging in the iPod.  gnome-volume-manager only checks for changes.

To specify the type of filesystem, you want "-t vfat".  So the full, absolutely-should-work command becomes:
```
sudo mount -t vfat /dev/sdb2 /media/iPod
```

---

### Post by John Jason Jordan on 2005-12-16
[QUOTE=RAOF]
To specify the type of filesystem, you want "-t vfat".  So the full, absolutely-should-work command becomes:
```
sudo mount -t vfat /dev/sdb2 /media/iPod
```[/QUOTE]
"Absolutely-should-work," eh? I just tried it and got:

mount: /dev/sdb2 is not a valid block device

Of course, I wouldn't recognize a block device if it walked up and bit me in the butt, valid or invalid.

Still looking for an answer. It's getting late, but I'm going to leave the computer running and iPod connected. Maybe in the morning someone will have a brilliant insight. :)

---

### Post by RAOF on 2005-12-16
Well, that absolutely-should-have-worked.  Which means that some or all of my assumptions were invalid.  So, to leave you for something in the morning, let's start from the top!

**First**: is the iPod really plugged in securely?  I thought my iPod was dying once, 'cause it kept almost copying files and then erroring out.  This was due to the connections being not quite secure.  Maybe something similar?

**Second**:  Let's run through dmesg again...  Run dmesg, and search through the output for the ipod lines.  At the end, there should be a line like this
```
[ 1951.171548]  sdc: sdc1 sdc2
```except sdc will probably be replaced with sda or sdb.  If this line is not there, check the first point again.

**Third**: Now that we know the name the kernel is calling the iPod, we can try to mount it: ```
sudo mount -t vfat /dev/sd?2 /media/iPod
``` where the sd? is replaced by whatever the kernel is calling the iPod.  If this doesn't work, double check you've got the right sd?2 from the second step.  If it still doesn't work, check the first step again.  If, after that, it doesn't work, then... it's time to restart the computer, and try again from point 1.

Oh, and additionally:  It is **totally safe** to ignore the "do not disconnect" once you've shutdown the computer.  If you just shutdown linux, the ipod's partitions will be unmounted cleanly if they are mounted somewhere but the ipod won't change to "safe to remove".

---

### Post by John Jason Jordan on 2005-12-16
[QUOTE=RAOF]Well, that absolutely-should-have-worked.  Which means that some or all of my assumptions were invalid.  So, to leave you for something in the morning, let's start from the top! <snip>
Oh, and additionally:  It is **totally safe** to ignore the "do not disconnect" once you've shutdown the computer.  If you just shutdown linux, the ipod's partitions will be unmounted cleanly if they are mounted somewhere but the ipod won't change to "safe to remove".[/QUOTE]
OK, it's morning. I decided to bite the bullet and unplug the iPod. And it still works. (Whew!)
Then I plugged it into a different USB port (computer has three). And I ran dmesg again. This is a copy and paste from the terminal window:
```

[89368.207241] sdb: Write Protect is off
[89368.207250] sdb: Mode Sense: 64 00 00 08
[89368.207256] sdb: assuming drive cache: write through
[89368.210845] SCSI device sdb: 117210239 512-byte hdwr sectors (60012 MB)
[89368.211742] sdb: Write Protect is off
[89368.211751] sdb: Mode Sense: 64 00 00 08
[89368.211757] sdb: assuming drive cache: write through
[89368.211766]  /dev/scsi/host3/bus0/target0/lun0: p1 p2
[89368.224160] Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun 0
[89368.226216] usb-storage: device scan complete

```
I note that there is no line at the end like "[1951.171548]  sdc: sdc1 sdc2." At this time the other USB disk is not connected, so this and my USB mouse are the only USB devices plugged in. Therefore, I conclude that "sdb" must be what the kernel thinks the iPod is.
Then I ran "mount" and this time I got:
/dev/sdb2 on /media/iPod type vfat (rw)
But gtkpod still couldn't see it and its Read button was still grayed out. So, even though I had spent an hour tidying up tags for a bunch of mp3s that I wanted to add, I decided to shut down gtkpod. (As far as I can tell there is no way to save such things in gtkpod, except by using Sync, which won't work until it has read the iPod.) So I closed gtkpod, losing an hour's work. 
When I reopened it its Read button was active. When I clicked it it found the iPod and imported its database. Yay!
So then I added the mp3s again and spent an hour changing the tags to the way I wanted them. And when I hit Sync I got:
"Error opening '/media/iPod/iPod_Control/Music/F12/gtkpod561325.mp3' for writing (Permission denied)."
Grrrrr.
OK, apparently, for some reason, the iPod is owned by root. (Just checked with Konqueror - Permissions tab.) So I did sudo chown jjj:jjj /media/iPod and this resulted in 
chown: changing ownership of `/media/iPod': Operation not permitted
Double grrrr.
Now it looks like I'll have to umount it, unplug it and plug it back in, at which point gtkpod will decide it isn't there any more, so I'll have to shut down gtkpod and restart it and lose another hour's work. 
But I won't do that just yet. Maybe there are some command line things I can do to change ownership that the gurus in here can help me with. (I'm a n00bie here.) Or maybe gtkpod has some features that I am not aware of. (Tip to Linux programmers: Having finished the application you are only half done; the other half of the job is the documentation.)

---

### Post by Dpdk on 2006-08-29
Ok well I followed this post for awhile, but the problems were signifigantly different. I've been trying to get my iPod mounted for a couple of days. I am a new Linux user, and my dad had me start with Kubuntu, but then i ended prefering the Gnome interface, so I switched to Ubuntu. ok so when i run "dmesg" I get:


[17520927.096000] sda : READ CAPACITY failed.
[17520927.096000] sda : status=0, message=00, host=1, driver=00
[17520927.096000] sda : sense not available.
[17520927.096000]  4:0:0:0: rejecting I/O to dead device
[17520927.096000] sda: Write Protect is off
[17520927.096000] sda: Mode Sense: 00 00 00 00
[17520927.096000] sda: assuming drive cache: write through
[17520927.108000]  4:0:0:0: rejecting I/O to dead device
[17521013.452000] usb 3-3: new high speed USB device using ehci_hcd and address 9
[17521013.584000] usb 3-3: configuration #1 chosen from 2 choices
[17521013.584000] scsi5 : SCSI emulation for USB Mass Storage devices
[17521013.584000] usb-storage: device found at 9
[17521013.584000] usb-storage: waiting for device to settle before scanning
[17521018.584000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17521018.584000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17521018.588000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17521018.588000] sda: Write Protect is off
[17521018.588000] sda: Mode Sense: 6c 00 00 08
[17521018.588000] sda: assuming drive cache: write through
[17521018.588000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17521018.592000] sda: Write Protect is off
[17521018.592000] sda: Mode Sense: 6c 00 00 08
[17521018.592000] sda: assuming drive cache: write through
[17521018.592000]  sda: sda1 sda2
[17521018.604000] sd 5:0:0:0: Attached scsi removable disk sda
[17521018.604000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[17521018.608000] usb-storage: device scan complete
[17521062.156000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521062.156000] sda: Current: sense key: Medium Error
[17521062.156000]     Additional sense: Unrecovered read error
[17521062.156000] Info fld=0x0
[17521062.156000] end_request: I/O error, dev sda, sector 58604938
[17521062.156000] printk: 748 messages suppressed.
[17521062.156000] Buffer I/O error on device sda2, logical block 29222144
[17521105.376000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521105.376000] sda: Current: sense key: Medium Error
[17521105.376000]     Additional sense: Unrecovered read error
[17521105.376000] Info fld=0x0
[17521105.376000] end_request: I/O error, dev sda, sector 58604940
[17521105.376000] Buffer I/O error on device sda2, logical block 29222145
[17521148.596000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521148.596000] sda: Current: sense key: Medium Error
[17521148.596000]     Additional sense: Unrecovered read error
[17521148.596000] Info fld=0x0
[17521148.596000] end_request: I/O error, dev sda, sector 58604942
[17521148.596000] Buffer I/O error on device sda2, logical block 29222146
[17521191.856000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521191.856000] sda: Current: sense key: Medium Error
[17521191.856000]     Additional sense: Unrecovered read error
[17521191.856000] Info fld=0x0
[17521191.856000] end_request: I/O error, dev sda, sector 58604944
[17521191.856000] Buffer I/O error on device sda2, logical block 29222147
[17521235.092000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521235.092000] sda: Current: sense key: Medium Error
[17521235.092000]     Additional sense: Unrecovered read error
[17521235.092000] Info fld=0x0
[17521235.092000] end_request: I/O error, dev sda, sector 58604938
[17521235.092000] Buffer I/O error on device sda2, logical block 29222144
[17521278.296000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521278.296000] sda: Current: sense key: Medium Error
[17521278.296000]     Additional sense: Unrecovered read error
[17521278.296000] Info fld=0x0
[17521278.296000] end_request: I/O error, dev sda, sector 58604940
[17521278.296000] Buffer I/O error on device sda2, logical block 29222145
[17521321.544000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521321.544000] sda: Current: sense key: Medium Error
[17521321.544000]     Additional sense: Unrecovered read error
[17521321.544000] Info fld=0x0
[17521321.544000] end_request: I/O error, dev sda, sector 58604942
[17521321.544000] Buffer I/O error on device sda2, logical block 29222146
[17521364.820000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521364.820000] sda: Current: sense key: Medium Error
[17521364.820000]     Additional sense: Unrecovered read error
[17521364.820000] Info fld=0x0
[17521364.820000] end_request: I/O error, dev sda, sector 58604944
[17521364.820000] Buffer I/O error on device sda2, logical block 29222147
[17521408.612000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521408.612000] sda: Current: sense key: Medium Error
[17521408.612000]     Additional sense: Unrecovered read error
[17521408.612000] Info fld=0x0
[17521408.612000] end_request: I/O error, dev sda, sector 58605098
[17521408.612000] Buffer I/O error on device sda2, logical block 29222224
[17521451.944000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521451.944000] sda: Current: sense key: Medium Error
[17521451.944000]     Additional sense: Unrecovered read error
[17521451.944000] Info fld=0x0
[17521451.944000] end_request: I/O error, dev sda, sector 58605100
[17521451.944000] Buffer I/O error on device sda2, logical block 29222225
[17521495.280000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521495.280000] sda: Current: sense key: Medium Error
[17521495.280000]     Additional sense: Unrecovered read error
[17521495.280000] Info fld=0x0
[17521495.280000] end_request: I/O error, dev sda, sector 58605102
[17521495.280000] Buffer I/O error on device sda2, logical block 29222226
[17521538.612000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521538.612000] sda: Current: sense key: Medium Error
[17521538.612000]     Additional sense: Unrecovered read error
[17521538.612000] Info fld=0x0
[17521538.612000] end_request: I/O error, dev sda, sector 58605104
[17521538.612000] Buffer I/O error on device sda2, logical block 29222227

And with dmesg  |  tail I get:

[17521625.308000]     Additional sense: Unrecovered read error
[17521625.308000] Info fld=0x0
[17521625.308000] end_request: I/O error, dev sda, sector 58605100
[17521625.308000] Buffer I/O error on device sda2, logical block 29222225
[17521668.624000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[17521668.624000] sda: Current: sense key: Medium Error
[17521668.624000]     Additional sense: Unrecovered read error
[17521668.624000] Info fld=0x0
[17521668.624000] end_request: I/O error, dev sda, sector 58605102
[17521668.624000] Buffer I/O error on device sda2, logical block 29222226

This is a bit different that the original problem and I have already tried killing and restarting the mount program. Any suggestions?

---

### Post by RAOF on 2006-08-29
The key error here would be:
"
[17521538.612000] Buffer I/O error on device sda2, logical block 29222227
"
And all of its duplicates.  That is, the kernel is having trouble reading from or writing to your iPod.  Check the connections :).

---

### Post by Dpdk on 2006-10-07
Ok well after alot of work, my iPod still isn't working. I have received several messages saying that the disk isnt formatted, even though it works fine with a Windows system. When i plug my iPod into my computer, I shows up in Computer, it is called Apple iPod Music Player. When I try to open it, i get an error message that says
> mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount> 
Any ideas on what I should do?

---

### Post by Old Pink on 2006-10-07
Try upgrading to Dapper?

3 iPods have worked 100% instant with no configuration on my dapper setup.

---

### Post by sda5150 on 2007-01-24
RAOF Cheers!
That worked a charm!!!
Was getting the error "mount: special device /dev/sdc2 does not exist."
Ubuntu was seeing my iPod as sdb2 instead of the usual sdc2.
Mounted it as /dev/sdb2 and it worked!

Thanks...

---

### Post by sda5150 on 2007-01-24
ooh I must add...
If your device is using a different name, ie. **sdb2** instead of **sdc2**, you'll need to change the entry for your iPod in **/etc/fstab** to also be **sdb2**. Otherwise you will not have read/write access to your iPod, and you'll get something along the lines of " Error opening /media/iPod/iPod_control/ "

---


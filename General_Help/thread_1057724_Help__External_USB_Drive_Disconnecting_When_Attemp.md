---
title: "Help:  External USB Drive Disconnecting When Attempting Write"
date: 2009-02-02
forum: General Help
---

### Post by TheOneBlackMage on 2009-02-02
Hello,

I've been having some problems with one of the external USB drives I am using.  I have 4 plugged into a PCI card with 4 USB slots on it, and none of the other drives are currently giving me problems.

I am able to mount the drive properly, but when I try to write files to it, I get errors:

```
cp: cannot create regular file `/home/username/MOUNTPOINT/Directory/Filename': Read-only file system
```

From my /var/log/messages, it looks like USB is disconnecting, but I don't know why:

```

[306654.945287] EXT3 FS on sdd1, internal journal
[306654.945298] EXT3-fs: mounted filesystem with ordered data mode.
[306760.884215] usb 5-4: reset high speed USB device using ehci_hcd and address 15
[306760.940274] usb 5-4: USB disconnect, address 15
[306760.948064] sd 7:0:0:0: Device offlined - not ready after error recovery
[306760.948748] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[306760.948756] end_request: I/O error, dev sdd, sector 1703028287
[306760.948766] lost page write due to I/O error on sdd1
[306760.948775] lost page write due to I/O error on sdd1
[306760.948780] lost page write due to I/O error on sdd1
[306760.948785] lost page write due to I/O error on sdd1
[306760.948790] lost page write due to I/O error on sdd1
[306760.948796] lost page write due to I/O error on sdd1
[306760.948801] lost page write due to I/O error on sdd1
[306760.948806] lost page write due to I/O error on sdd1
[306760.948811] lost page write due to I/O error on sdd1
[306760.948816] lost page write due to I/O error on sdd1
[306760.953745] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[306760.953754] end_request: I/O error, dev sdd, sector 1703028527
[306761.203415] usb 5-4: new high speed USB device using ehci_hcd and address 16
[306761.762042] usb 5-4: new high speed USB device using ehci_hcd and address 17
[306762.320679] usb 5-4: new high speed USB device using ehci_hcd and address 18
[306762.683805] usb 5-4: new high speed USB device using ehci_hcd and address 19
[306762.904656]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[306762.904657]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
[306762.905365] sr: Sense Key : Aborted Command [current] [descriptor]
[306762.905369] sr: Add. Sense: No additional sense information
[306803.955733] __journal_remove_journal_head: freeing b_committed_data

```

If I turn the drive off, and then back on, I can mount it again.  I did a fsck with it unmounted, and found no problems:

```

fsck 1.40.8 (13-Mar-2008)
MONOLITH: /lost+found not found.  CREATED.

    2117 inodes used (0.00%)
      88 non-contiguous inodes (4.2%)
         # of inodes with ind/dind/tind blocks: 1949/1945/0
170774281 blocks used (69.94%)
       0 bad blocks
       1 large file

    1982 regular files
     125 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
    2107 files

```

I found a number of posts complaining about ehci_hcd.  I tried resetting max_sectors for that drive from 240 to 64, but it still has problems.  I have done some hardware changes recently (motherboard, CPU, added the USB card), but everything was working fine for a while.

Running Xubuntu Hardy 8.04.1 (2.6.24-19-generic)

Thanks in advance for any assistance.

---

### Post by ajgreeny on 2009-02-02
Is it a seagate drive?  Some of these can have problems as they go into a suspend mode after a period of inactivity, though I thought this had been overcome in later versions of ubuntu, so I could be leading you up a blind alley.  Search further if it is a seagate and you may find more info.

---

### Post by TheOneBlackMage on 2009-02-02
It's a Lacie 1TB external drive.  I'm not sure what the actual hard drive brand is, but I doubt it's Seagate.  Also, this happens within minutes of remounting it, so it doesn't seem to be a timeout.

Any other thoughts?  I'm reading posts I'm finding based on the error messages I've seen, but haven't found anything helpful yet.

Here is my fstab:

```

# Entry for /dev/sda1 :
UUID=e1557eca-9edc-4863-a140-80532cd47632 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=ac8ae45b-449e-44bf-98c9-bd54a9a2c473 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /home/username/MORE ext3 defaults 0 0
/dev/sdc1 /home/username/DISK ext3 auto,defaults,exec 0 0
/dev/sdd1 /home/username/MONOLITH ext3 auto,defaults,exec 0 0
/dev/sde1 /home/username/MONOLITH2 ext3 auto,defaults,exec 0 0
/dev/sdf1 /home/username/ACCOMDATA ntfs-3g rw,auto,defaults,exec 0 0

```

---


---
title: "Very mysterious but bad ATA errors, please help"
date: 2008-12-19
forum: General Help
---

### Post by YaroMan86 on 2008-12-19
I am having a problem. It seems when I play music, my entire desktop except my mouse and a few apps freeze for a short time, then recover after several seconds.

I did a dmesg and found out that for some reason Ubuntu was having trouble reading from my /home hard disk. So I rebooted and did a SMART test from my BIOS and it returned no errors.

So I booted into single mode (Recovery console) and it automatically did a fsck of the problem file system, reporting that it had errors.

It cleared out a LOT of errors, then died, telling me to run it manually. so I did, and it turns out there were a ton of errors yet that I had to clear out, which I did. (I answered yes to all off its questions.) I restarted and ran Ubuntu normally.

I carried on thinking it was all fixed, but then the same problem occured, it and did it twice in a row.

Here is the dmesg output for those two sudden freezes.
```

[ 1195.819373] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1225.788061] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x19d0000 action 0xe frozen
[ 1225.788079] ata1: SError: { PHYRdyChg CommWake 10B8B Dispar LinkSeq TrStaTrns }
[ 1225.788091] ata1.00: cmd c8/00:50:3f:0d:9d/00:00:00:00:00/e4 tag 0 dma 40960 in
[ 1225.788094]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
[ 1225.788099] ata1.00: status: { DRDY }
[ 1226.504150] ata1: soft resetting link
[ 1227.780065] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1227.804185] ata1.00: configured for UDMA/100
[ 1227.804219] ata1: EH complete
[ 1227.825143] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1227.826785] sd 0:0:0:0: [sda] Write Protect is off
[ 1227.826795] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1227.830866] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1316.264069] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xe frozen
[ 1316.264087] ata1: SError: { PHYRdyChg CommWake Dispar LinkSeq TrStaTrns }
[ 1316.264099] ata1.00: cmd c8/00:50:3f:23:9d/00:00:00:00:00/e4 tag 0 dma 40960 in
[ 1316.264102]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
[ 1316.264108] ata1.00: status: { DRDY }
[ 1316.984047] ata1: soft resetting link
[ 1318.260571] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1318.284947] ata1.00: configured for UDMA/100
[ 1318.284983] ata1: EH complete
[ 1348.284056] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xe frozen
[ 1348.284066] ata1: SError: { PHYRdyChg CommWake Dispar LinkSeq TrStaTrns }
[ 1348.284071] ata1.00: cmd c8/00:50:3f:23:9d/00:00:00:00:00/e4 tag 0 dma 40960 in
[ 1348.284072]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
[ 1348.284075] ata1.00: status: { DRDY }
[ 1349.003676] ata1: soft resetting link
[ 1350.276045] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1350.300128] ata1.00: configured for UDMA/100
[ 1350.300145] ata1: EH complete
[ 1350.321069] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1350.325463] sd 0:0:0:0: [sda] Write Protect is off
[ 1350.325472] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1350.329572] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1350.329943] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1350.330134] sd 0:0:0:0: [sda] Write Protect is off
[ 1350.330139] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

```

I don't think its a disk failure, since my MART was negative. Is it persistant file system problems, perhaps? I need help.

The problem started after I removed Windows completely, installed Linux on the other hard disk, and grew my /home partition to fill the entire hard disk which is reporting this problem.

EDIT: Just as I posted this thread, I had it happen a third time, but I doubt any new information is to be had from this problem.

---

### Post by taurus on 2008-12-19
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by albinootje on 2008-12-19
> **YaroMan86 said:**
> 
```

[ 1195.819373] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1225.788061] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x19d0000 action 0xe frozen
[ 1225.788079] ata1: SError: { PHYRdyChg CommWake 10B8B Dispar LinkSeq TrStaTrns }

```

It could be an irq conflict/problem between your sound card and hard disk.

A search-engine search for "SError: { PHYRdyChg CommWake 10B8B Dispar LinkSeq TrStaTrns }" showed this :
[http://kerneltrap.org/node/15875](http://kerneltrap.org/node/15875)
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

Did any files end up in /lost+found ?
Did you check your hard disk for bad blocks ?
(I'm not sure that SMART checks for that).
What is the motherboard you're using ?
I have an ASUS motherboard (which someone told me has some reported quirks) which started to give kind of similar problems with the IDE disk, i decided to switch to a SATA disk. Everything is fine.

---

### Post by YaroMan86 on 2008-12-19
> **taurus said:**
> Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

```

yaro@irma:~$ sudo fdisk -l
[sudo] password for yaro: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001258f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241   83  Linux

Disk /dev/sdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c28f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            3084        3736     5245222+  82  Linux swap / Solaris
/dev/sdb2   *           1        3083    24764166   83  Linux

Partition table entries are not in disk order

```

```

yaro@irma:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=779fbe32-586a-430c-9b13-fb8baca9340d /               reiserfs notail,relatime 0       1
# /dev/sdb1
UUID=1721836e-3e80-403c-8c65-cfd7258a22be /home           ext2    relatime        0       2
# /dev/sda1
UUID=02123aa6-1ba2-493f-b2de-0302df073257 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

yaro@irma:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              24G  3.1G   21G  13% /
tmpfs                 752M     0  752M   0% /lib/init/rw
varrun                752M  216K  752M   1% /var/run
varlock               752M     0  752M   0% /var/lock
udev                  752M  2.9M  750M   1% /dev
tmpfs                 752M     0  752M   0% /dev/shm
lrm                   752M  2.4M  750M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1             111G   49G   63G  44% /home

```

---

### Post by YaroMan86 on 2008-12-19
> **albinootje said:**
> It could be an irq conflict/problem between your sound card and hard disk.

A search-engine search for "SError: { PHYRdyChg CommWake 10B8B Dispar LinkSeq TrStaTrns }" showed this :
[http://kerneltrap.org/node/15875](http://kerneltrap.org/node/15875)
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

Did any files end up in /lost+found ?
Did you check your hard disk for bad blocks ?
(I'm not sure that SMART checks for that).
What is the motherboard you're using ?
I have an ASUS motherboard (which someone told me has some reported quirks) which started to give kind of similar problems with the IDE disk, i decided to switch to a SATA disk. Everything is fine.

Some files did end up in there: My Amarok settings, some Pidgin settings, and quite a few entries in .gconf. I deleted them all, I figured it's be easy to just reconstruct those settings if need be.

Does fsck not do this? If not how can I do that?

My motherboard came with the machine, according to the HP website, it is this:


Motherboard

    *
      Manufacturer: ECS
    *
      Motherboard Name: MCP61PM-HM
    *
      HP/Compaq motherboard name: Iris-GL6

---

### Post by YaroMan86 on 2008-12-19
Update. I can't seem to save to this partition anymore, I get I/O errors. It crashed Pidgin. Output of pidgin debug and the new dmesg output follows.

```

(17:59:21) dns: Successfully sent DNS request to child 8962
(17:59:21) dns: Got response for '205.188.248.145'
(17:59:21) dnsquery: IP resolved for 205.188.248.145
(17:59:21) proxy: Attempting connection to 205.188.248.145
(17:59:21) proxy: Connecting to 205.188.248.145:5190 with no proxy
(17:59:21) proxy: Connection in progress
(17:59:21) jabber: Recv (ssl)(136): <iq id="purple1c664106" type="result"><bind xmlns="urn:ietf:params:xml:ns:xmpp-bind"><jid>yaro@marupa.net/HomeD592AF41</jid></bind></iq>
(17:59:21) jabber: Sending (ssl): <iq type='set' id='purple1c664107'><session xmlns='urn:ietf:params:xml:ns:xmpp-session'/></iq>
(17:59:21) jabber: Recv (ssl)(1):  
(17:59:21) oscar: Connecting to FLAP server 205.188.179.21:5190 of type 0x000d
(17:59:21) dns: DNS query for '205.188.179.21' queued
(17:59:21) oscar: ssi: syncing local list and server list
(17:59:21) blist: Updating buddy status for +18016238399 (AIM)
(17:59:21) nautilus: couldn't save '/home/yaro/.gnome2/nautilus-sendto/pidgin_buddies_online': Failed to create file '/home/yaro/.gnome2/nautilus-sendto/pidgin_buddies_online.XFXZLU': Input/output error
dns[8962]: Oops, father has gone, wait for me, wait...!
dns[8961]: Oops, father has gone, wait for me, wait...!
Segmentation fault

```

```

[ 5411.666884] end_request: I/O error, dev sda, sector 63
[ 5411.666889] Buffer I/O error on device sda1, logical block 0
[ 5411.666893] lost page write due to I/O error on sda1
[ 5411.673145] EXT2-fs error (device sda1): read_inode_bitmap: Cannot read inode bitmap - block_group = 278, inode_bitmap = 9109505
[ 5412.676861] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5412.676881] end_request: I/O error, dev sda, sector 72876103
[ 5412.680502] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5412.680514] end_request: I/O error, dev sda, sector 63
[ 5412.683936] EXT2-fs error (device sda1): read_inode_bitmap: Cannot read inode bitmap - block_group = 278, inode_bitmap = 9109505
[ 5412.686871] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5412.686883] end_request: I/O error, dev sda, sector 72876103
[ 5412.687713] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5412.687723] end_request: I/O error, dev sda, sector 63
[ 5412.691053] EXT2-fs error (device sda1): read_inode_bitmap: Cannot read inode bitmap - block_group = 278, inode_bitmap = 9109505

```

The dmesg output repeats like that for some length.

---

### Post by taurus on 2008-12-19
If your harddrive starts to act up, I would seriously consider replacing it.  New ones are dirt cheap now.  Then, you don't have to worry about the harddrive (/home) would go belly up any second (although there is no guarantee with the new drive; that's why backup is important).

---

### Post by YaroMan86 on 2008-12-19
I read that first link given by albinootje... and the frightening thing is... I *am* using a GeForce 8600GT now. It could be its sending interrupts to the wrong thing.

So maybe I should try fixing an interrupt conflict somewhere. How would I go about doing this?

---

### Post by albinootje on 2008-12-19
> **YaroMan86 said:**
> Update. I can't seem to save to this partition anymore, I get I/O errors. It crashed Pidgin. Output of pidgin debug and the new dmesg output follows.

```

[ 5411.666884] end_request: I/O error, dev sda, sector 63
[ 5411.666889] Buffer I/O error on device sda1, logical block 0
[ 5411.666893] lost page write due to I/O error on sda1
[ 5411.673145] EXT2-fs error (device sda1): read_inode_bitmap: Cannot read inode bitmap - block_group = 278, inode_bitmap = 9109505

```

The dmesg output repeats like that for some length.

Okay, this looks like your file-system is having trouble.
That does not mean that your disk is dying. After a reformat, and figuring out what the previous posted errors were about, it could be fine again.

It looks like you have to save whatever you can first.
I recommend booting from a linux live cd, and then back up your files to an external usb-disk.
After that find out more about the previous posted errors, and do a fresh install.

---

### Post by YaroMan86 on 2008-12-19
> **albinootje said:**
> Okay, this looks like your file-system is having trouble.
That does not mean that your disk is dying. After a reformat, and figuring out what the previous posted errors were about, it could be fine again.

It looks like you have to save whatever you can first.
I recommend booting from a linux live cd, and then back up your files to an external usb-disk.
After that find out more about the previous posted errors, and do a fresh install.

Well, that cleared out the IO problem, I guess. But the ATA problem remains:

```

[ 4894.320054] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x19d0000 action 0xe frozen
[ 4894.320073] ata1: SError: { PHYRdyChg CommWake 10B8B Dispar LinkSeq TrStaTrns }
[ 4894.320085] ata1.00: cmd 35/00:d0:4f:97:05/00:03:00:00:00/e0 tag 0 dma 499712 out
[ 4894.320088]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
[ 4894.320094] ata1.00: status: { DRDY }
[ 4895.036035] ata1: soft resetting link
[ 4896.312060] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 4896.336498] ata1.00: configured for UDMA/100
[ 4896.336532] ata1: EH complete
[ 4896.385267] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 4896.386069] sd 0:0:0:0: [sda] Write Protect is off
[ 4896.386079] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4896.394035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
This time it DIDN'T mention anything about IRQ. Is my drive failing? I hope not. I can't afford a new drive for some time.

---

### Post by albinootje on 2008-12-20
> **YaroMan86 said:**
> 
This time it DIDN'T mention anything about IRQ. Is my drive failing? I hope not. I can't afford a new drive for some time.

Is this copy and pasted while using a Linux live cd ?
Did you manage to back up your important data ?

---


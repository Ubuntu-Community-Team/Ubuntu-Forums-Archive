---
title: "External USB drive not recognized after boot Jaunty"
date: 2009-04-18
forum: General Help
---

### Post by cross157 on 2009-04-18
I've been struggling to get my USB external hard drives to mount on boot. I've tweaked fstab and rc.local to no avail. The reason I now believe is because my externals are not be recognized after a full boot cycle. They are both on separate power supplies and remain on during reboots.

After bootup
```
sudo fdisk -l
```
_Result_:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           18582       19457     7036470    5  Extended
/dev/sda2   *           1        3647    29294496   83  Linux
/dev/sda3            3648       18581   119957355   83  Linux
/dev/sda5           18583       19457     7028437+  82  Linux swap /   Solaris

```
sudo blkid
```
_Result_:
/dev/sda2: UUID="d43762cc-9f52-4b09-8c78-7c11dd55edb7" TYPE="ext4" 
/dev/sda3: UUID="d1e10d68-ca09-4700-a20e-49ec4651d275" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="6f7cad75-cf59-4c3d-aaa4-1ec49672a8bb"

Now if I power cycle either of the drives BOTH will show up.

After power cycle (external hard drive only):
```
sudo fdisk -l 
```
_Result_:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           18582       19457     7036470    5  Extended
/dev/sda2   *           1        3647    29294496   83  Linux
/dev/sda3            3648       18581   119957355   83  Linux
/dev/sda5           18583       19457     7028437+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9258a496

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

```
sudo blkid 
```
_Result_:
/dev/sda2: UUID="d43762cc-9f52-4b09-8c78-7c11dd55edb7" TYPE="ext4" 
/dev/sda3: UUID="d1e10d68-ca09-4700-a20e-49ec4651d275" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="6f7cad75-cf59-4c3d-aaa4-1ec49672a8bb" 
/dev/sdb1: UUID="2DC35AAC0022D957" LABEL="MyBook" TYPE="ntfs" 
/dev/sdc1: UUID="C8F43344F4333452" LABEL="BIG" TYPE="ntfs"

Also, I get two pop up windows that saying that I don't have permission to mount the two externals. Once the power cycle is done ```
sudo mount -a 
```will mount both drives, but I would like it to happen on boot. I think it will if they are recognized. Anyone have any clue on this one? Thanks in advance.

---

### Post by satsumace on 2009-04-25
I'm having the same problem after an upgrade to Jaunty - my external hd is now not automounting, which is a big problem for me as my /home partition is on this drive.

My impression is that the usb driver or something is not kicking in before the filesystems are mounted from fstab. I didn't have this problem in Intrepid so it must be something new in Jaunty causing the problem...

---

### Post by GJLenon on 2009-04-25
I have the same problem.

My Lexar USB Flashdrive is not showing up.  When I connect another media device after boot (ex: iPod) it'll pop up both the iPod and the Lexar drive.

I also seem to be missing a partition, though that could have been overwritten when I installed 9.04 (64-bit)

Before connecting the iPod:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08ed08ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris


After connecting the iPod:

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08ed08ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1357     7783940    b  W95 FAT32

Disk /dev/sdc: 4026 MB, 4026531840 bytes
216 heads, 32 sectors/track, 1137 cylinders
Units = cylinders of 6912 * 512 = 3538944 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1134     3915760    c  W95 FAT32 (LBA)


Magically it sees the jumpdrive...

Like I said, only difference is I plugged in the iPod.

---

### Post by sahabcse on 2009-04-25
Same issue my-mobile memory card is not mounting.

---

### Post by thehousecat on 2009-04-25
I have exactly the same problem. I have just upgraded (by way of a clean install) from Itrepid to Jaunty Server.

My external USB hard drive (with own power supply) used to be recognised at boot time by Intrepid. Now with Jaunty it doesn't. I have to power cycle the HDD after boot up for it to be recognised.

I also have my /home on this drive so it is a big problem.

---

### Post by pix27 on 2009-04-25
Seems the "usb_storage" module isn't being loaded. Adding this to /etc/modules made it work fine. (Or run sudo modprobe -i usb_storage)

Dunno why this is happening now. Was working fine in intrepid.

---

### Post by thehousecat on 2009-04-25
Excellent, thanks a lot pix27. Now my external USB device is recognised at boot time.

Unfortunately that's not my whole story. My external USB drive is encrypted with LUKS and it doesn't luksOpen on boot anymore (it did in Intrepid). This in my /etc/crypttab:

store                /dev/sdb         /etc/keys/store.key    luks

During bootup some error about /etc/keys/store.key whizzes past too quickly for me to read. Does anyone know how I can see what this message said? It doesn't appear in dmesg, syslog or messages.

(BTW I can use that key file to open the LUKS volume fine after I've booted)

Thanks

---

### Post by pix27 on 2009-04-25
Perhaps the message was dumped into one of the other files in /var/log? Have you tried the "Log Viewer" to search for it?

---

### Post by satsumace on 2009-04-25
I've kind of fixed my problem...

In my case usb_storage was being loaded even without the entry in /etc/modules, but I guess it was loaded too late to be picked up by the automount process. I found if I force an fsck on my root partition this gives enough time for the usb drive to be recognised before it tries to mount it, so for now my solution is just to set fsck to run on the root drive on every boot using tune2fs (not really a big problem for me as it's a server and hardly ever rebooted). It may be that this problem was inadvertently avoided on intrepid by the slower boot time.

It's not an ideal solution so if anyone has a better one please let me know e.g. can I force usb_storage to run earlier in the boot process, or force the mounting of filesystems to happen later?

---

### Post by coldReactive on 2009-04-25
> **pix27 said:**
> Seems the "usb_storage" module isn't being loaded. Adding this to /etc/modules made it work fine. (Or run sudo modprobe -i usb_storage)

Dunno why this is happening now. Was working fine in intrepid.

I have the problem of my USB drive not automounting on boot too, but using your method and rebooting still causes the drive not to be mountable (or even recognized) when the system boots up. I still have to unplug and replug it back in, or do the command you gave each time I start up the machine.

here's my thread: [http://ubuntuforums.org/showthread.php?t=1134501](http://ubuntuforums.org/showthread.php?t=1134501)

I don't know how to add the usb_storage to my etc/modules file manually though.

Edit: Nevermind, I figured it out.

---

### Post by pix27 on 2009-04-26
In a terminal run:

```
sudo sh -c "echo usb_storage >> /etc/modules"
```

then reboot. that should do it.

---

### Post by cross157 on 2009-04-26
> **pix27 said:**
> In a terminal run:

```
sudo sh -c "echo usb_storage >> /etc/modules"
```

then reboot. that should do it.



I tried this and it did not help. Did anyone have success by adding usb_storage to /etc/modules?

---

### Post by coldReactive on 2009-04-26
> **cross157 said:**
> I tried this and it did not help. Did anyone have success by adding usb_storage to /etc/modules?

I did, but I added it manually.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296)

---

### Post by cross157 on 2009-04-26
> **coldReactive said:**
> I did, but I added it manually.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296)

Is there a difference between adding manually and using sh echo append?

---

### Post by jswhite on 2009-04-26
The "echo" method is just one way of adding it manually. Alternatively, you could open /etc/modules in gedit (or your other favorite text editor) with "gksu gedit /etc/modules" and add it that way. The "echo" command is just faster. Either way, you end up at the same place.

---

### Post by Rocks and Water on 2009-04-27
I'm having a similar problem. No matter what I do, I can't seem to access my USB drive.

When I type "sudo fdisk -l", I get this:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc622fdc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38913   292085797+   5  Extended
/dev/sda5            2551       32513   240677766   83  Linux
/dev/sda6           32514       35585    24675808+   b  W95 FAT32
/dev/sda7           35586       38387    22507033+  83  Linux
/dev/sda8           38388       38913     4225063+  82  Linux swap / Solaris

Disk /dev/sdb: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders
Units = cylinders of 441 * 512 = 225792 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              19       17741     3907648    c  W95 FAT32 (LBA)


And "lsusb" gives me this:

Bus 001 Device 008: ID 13fe:3100 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:c303 Logitech, Inc. iTouch Keyboard
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 003: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I believe my USB is the Kingston device, so my computer CAN apparently recognize it, yet it won't mount.

I never had any problem accessing my USB drives prior to updating to Jaunty a few days ago.

I've added "usb_storage" to /etc/modules, but no luck.

Any advice? This is INCREDIBLY frustrating. I'm going to have to format my computer and try a fresh install instead of an update if I can't get this to work.

---

### Post by coldReactive on 2009-04-27
adding usb_storage to /etc/modules only makes it so Ubuntu can see the USB Storage on boot, it's then up to Ubuntu on how to handle how to auto-mount it, if at all.

---

### Post by demonoidmaster on 2009-04-29
I Got Something Also That Is A Bit Like That... It Takes Place After The Bios And Before The Bootscreen (Loading Bar)

[http://ubuntuforums.org/showthread.php?t=1139344&highlight=jaunty+boot](http://ubuntuforums.org/showthread.php?t=1139344&highlight=jaunty+boot)

---

### Post by udude on 2009-05-05
Has anyone figured it out by any chance? Maybe there's an easy way to force-load usb_storage earlier? meaning before fstab is parsed...

Is there by any chance a known Jaunty bug about this issue?

---

### Post by coldReactive on 2009-05-05
> **udude said:**
> Has anyone figured it out by any chance? Maybe there's an easy way to force-load usb_storage earlier? meaning before fstab is parsed...

Is there by any chance a known Jaunty bug about this issue?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366296)

---

### Post by bobbiescap on 2009-05-05
Maybe we should delay the release occasionally to address some of these bugs as I am not happy that I upgraded and wish I had stayed with 8.10, some users delight in sorting out issues and others just want their computer to work like it did with the previous version, I just like it to work. BTW has anybody sorted out this issue?  :-\"

---

### Post by coldReactive on 2009-05-05
> **bobbiescap said:**
> Maybe we should delay the release occasionally to address some of these bugs as I am not happy that I upgraded and wish I had stayed with 8.10, some users delight in sorting out issues and others just want their computer to work like it did with the previous version, I just like it to work. BTW has anybody sorted out this issue?  :-\"

Some users don't have the issue (Exa: Me)  anymore ever since they added usb_storage to etc/modules, so it's mixed at the moment.

Not to mention, Pidgin is NOT set up like it was in Ubuntu 8.10 and earlier (The tray icon is defaulted to show never.)

---

### Post by simonjp on 2009-05-07
I've had the same problem with a 500GB Freecom external HD (formatted in NTFS).  Adding the usb_storage to the /etc/modules file fixed the detection issue at boot.

---

### Post by chrisod on 2009-05-08
I've got my NAT drive added to /etc/modules and it still isn't loading properly at boot. I have to do a* sudo mount -all* to get it accessible.

---


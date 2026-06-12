---
title: "Boots to grub&gt; prompt"
date: 2022-03-22
forum: Desktop Environments
---

### Post by richardth on 2022-03-22
Hi I am a software professional with some experience with Linux.

My son has a Dell G3 P89F002 running Ubuntu upgraded a few weeks ago to 22.04 kernel 5.17.  It dual boots Windows.
He had been using it in this configuration - playing games, watching Youtube and video-editing with OpenShot mostly, for 2 or 3 weeks.

One day, turning the PC on, we get only

```

grub>

```
Using grub commands I can see that (hd0,gpt5) is the Ubuntu partition - I can see /home and its contents.

So I do:
```
set root=(hd0,gpt5)
```
```
ls /boot 

```
gives me various kernels including 
```
vmlinuz-5.8.0-31-generic
vmlinuz-5.15.0-22-generic
vmlinuz-5.16.12-051612-generic 
vmlinuz-5.17.0-051700rc4-generic

```
 and a couple of others and their initrd files.
So I do:
```
linux vmlinuz-5.16.12-051612-generic root=/dev/sda5
initrd initrd-5.16.12-051612-generic
boot
```
I get a whole lot of booting output ending
...
```
[     3.158255] logitech-hidpp-device 003:046D:406A.0007: input hidraw2: USB HID v1.11 Keyboard [Logitech MX Anywhere 2S] on usb-0000:00:14.0-3/input2:1
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Waiting for root file system ... Begin: Running /scripts/local-block ... done.
done.
Gave up waiting for root file system.  Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda5 does not exist.  Dropping to a shell!


BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
The non-existence of /dev/sda5 seems to be the first obvious problem.  What's going on here?

More to the point, what can I do to recover?

Edit: another post suggested I try
blkid
This reveals what might point to a solution:
```

/dev/nvme0n1p7: LABEL="Image" BLOCK_SIZE ....
/dev/nvme0n1p5: UUID="1cd02..... " BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="...."

```
etc

---

### Post by richardth on 2022-03-22
Okay I did
```
blkid
```
revealing (amongst others)
```
/dev/nvme0n1p5: UUID="..." BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="..."
```

The TYPE="ext4" says it's my partition.

Following the grub boot process but with root=/dev/nvme0n1p5 gets me booting into Ubuntu again.

On restart I need to do follow the process again though... so still some work to do.

Anyone know how to repair grub so that I can boot back to my set of partitions?
This is 22.04...

---

### Post by oldfred on 2022-03-22
If you can boot try:
sudo grub-install

Do you have good backups?
If not best to do that, now.
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

I started copying data to another drive, partition. Not a real backup, but its just my desktop and only a copy. But then I started to do copy to multiple flash drives, two locations & have DVDs as full backup of my most critical data.

---

### Post by richardth on 2022-03-22
I installed and ran [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") getting these results: [https://paste.ubuntu.com/p/VVMRF546yV/](https://paste.ubuntu.com/p/VVMRF546yV/)
I later created a bootable version and executed the "Recommended repair".  This ran but said:
"An error occurred during the repair.
Error detected in grub_mkconfig.  Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]"

The results are in [https://paste.ubuntu.com/p/nJ2DPx6Npr/](https://paste.ubuntu.com/p/nJ2DPx6Npr/)

On reboot I was back to the grub> prompt.  I know how to get back to Ubuntu from there (tiresome as it is) - but the Windows partition remains unavailable.

---

### Post by oldfred on 2022-03-22
You should be able to directly boot Windows from UEFI. But you now do not have an UEFI entry.

You need to modify this for nvme drive. see 
man efibootmgr
New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
Probably
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 1

Your install is Jammy which is not yet released and Jammy uses grub 2.06.
But it looks like you have an upgraded system and are using a live installer from Bionic which uses grub 2.04.
Your issue may then be incompatibility between versions of grub.
Use only a live installer with same version as your install.

Also grub 2.06 is turning off os-prober by default for some security reason.
You can manually turn it on, but should turn it back off.
Better to just copy a standard Windows boot stanza into 40_custom.

---

### Post by richardth on 2022-03-22
Thanks @oldfred 

So efibootmgr got me a Windows partition accessible - great!  Thanks for the help in getting that done.

My only problem is that, if my boot order starts with one of the existing Linux partitions - I drop to the grub> prompt and have to boot that manual way.
Similarly if I put the UEFI BC511 NVMe SK hynix partition at the top.

Is there a straightforward efibootmgr command that will fix this?

Current output of efibootmgr -v is:

```

BootCurrent: 0004
Timeout: 5 seconds
BootOrder: 0004,0000,0007,0001,0002
Boot0000* UEFI BC511 NVMe SK hynix 512GB CY07N032510807I3Q 1	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-00-00-00-00-00-00-00)/HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* ONBOARD NIC (IPV4)	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(8c47be48ab79,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.
Boot0002* ONBOARD NIC (IPV6)	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(8c47be48ab79,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot0003  ubuntu	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* ubuntu	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* Windows Boot Manager	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0007* Windows Boot Manager	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................

```

Apologies but I'm a bit lost with this.

Should I do another 
```

sudo efibootmgr -c -L "Ubuntu 22.04" -l "<what goes here?>" -d /dev/nvme0n1 -p 5

```
or something like that?

---

### Post by oldfred on 2022-03-22
You show correct UUID in /efi/boot/grub.cfg.
So from ESP it should directly boot.

Do not know if something now not correct with grub 2.06.
I am booting with 20.04 with grub 2.04, but have a configfile entry to my test install of Jammy which works.

my entry has root hd0,gpt2 which is where my install is.
You could try editing the grub and change from just root at end of first line to add drive & partition like hd0,gpt5

if booted & fstab mount lets you edit (i have to change mine to defaults from theumask=0077).
[FONT=monospace][COLOR=#000000]sudo nano /boot/efi/EFI/ubuntu/grub.cfg

cat /etc/fstab
Mine:
[FONT=monospace][COLOR=#000000]UUID=4954-C122  /boot/efi       vfat    defaults      0       1[/COLOR]

& I typically have to reboot for new parameter to be used. [/FONT]

[/COLOR]
[/FONT]

---

### Post by richardth on 2022-03-23
Hi @oldfred - thanks again.

I'm struggling to properly get what you mean.

My `/boot/efi/EFI/ubuntu/grub.cfg` is
```

search.fs_uuid 1cd02c5d-3cc5-40d1-9c5d-684cb656b610 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```
so I change it to
```

search.fs_uuid 1cd02c5d-3cc5-40d1-9c5d-684cb656b610 root hd0,gpt5
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```


do you think?

I'll throw in some more info in case it makes my setup clearer.
While booted (via the tiresome grub> process) into Ubuntu, blkid gives me:
```

$ blkid
/dev/nvme0n1p5: UUID="1cd02c5d-3cc5-40d1-9c5d-684cb656b610" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="a6eb290d-1112-4a1f-8225-ef6fbdf102cf"

```

My `fstab`:
```

$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during installation
UUID=1cd02c5d-3cc5-40d1-9c5d-684cb656b610 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=586F-E85D  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

So that `umask` is indeed `0077`

So - maybe change it to default and add that `hd0,gpt5` ?

I don't really understand what this will do.
Apologies for my ignorance here!

---

### Post by oldfred on 2022-03-23
Yes, try to change the root to root hd0,gpt5
And first change umask=0077 to defaults, if you cannot edit [FONT=monospace][COLOR=#000000]/boot/efi/EFI/ubuntu/grub.cfg.
If mounting & editing from a live installer, then you would not have to edit fstab, but have to manually mount ESP and use that path in edit command.[/COLOR][/FONT]

I could not edit the grub file even with sudo with the 0077 setting from within my install. And the normal sudo mount -a to remount also did not work to reset the permissions. But I found once I rebooted it did work.
There probably is a better way as the 0077 is to lock up or protect changes to the ESP as it is FAT32 and then does not have Linux ownership & permissions. So 0077 is for better security. Ubuntu used defaults thru 14.04 but then changed to the 0077.
And upgrades or major changes do edit grub in ESP, not sure how they do it.

---

### Post by richardth on 2022-03-23
Successfully made these changes... but no joy.

So still now:
* when the Windows partition is 1st in boot order in the BIOS - great: boots to Windows.
* when ubuntu (or anything else) is 1st in boot order in the BIOS it brings me to the
```

grub>

```
prompt.

I must then go through the steps:
```

set root=(hd0,gpt5)
linux /boot/vmlinuz-5.17.0-051700rc4-generic root=/dev/nvme0n1p5
initrd /boot/initrd.img-5.17.0-051700rc4-generic
boot

```
and then it boots Ubuntu.

---

### Post by oldfred on 2022-03-23
Are you booting in UEFI boot mode?
Query to check if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

And from within your install if UEFI, does this give any error messages? 
sudo grub-install
If UEFI, it should use all the defaults and ESP as mounted with fstab.

---

### Post by richardth on 2022-03-26
I'm not sure it means anything useful: I did a recent `apt upgrade`.  During the process:
```

. . . 
Setting up grub-pc-bin (2.06-2ubuntu6) ...
Setting up grub-pc (2.06-2ubuntu6) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.17.0-051700rc4-generic
Found initrd image: /boot/initrd.img-5.17.0-051700rc4-generic
Found linux image: /boot/vmlinuz-5.16.12-051612-generic
Found initrd image: /boot/initrd.img-5.16.12-051612-generic
Found linux image: /boot/vmlinuz-5.15.0-23-generic
Found initrd image: /boot/initrd.img-5.15.0-23-generic
Found linux image: /boot/vmlinuz-5.15.0-22-generic
Found initrd image: /boot/initrd.img-5.15.0-22-generic
Found linux image: /boot/vmlinuz-5.8.0-63-generic
Found initrd image: /boot/initrd.img-5.8.0-63-generic
Found linux image: /boot/vmlinuz-5.8.0-33-generic
Found initrd image: /boot/initrd.img-5.8.0-33-generic
Found linux image: /boot/vmlinuz-5.8.0-31-generic
Found initrd image: /boot/initrd.img-5.8.0-31-generic
Found linux image: /boot/vmlinuz-5.8.0-28-generic
Found initrd image: /boot/initrd.img-5.8.0-28-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
/usr/sbin/grub-probe: error: unknown filesystem.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
/usr/sbin/grub-probe: error: unknown filesystem.
Adding boot menu entry for UEFI Firmware Settings ...
done
. . .

```

Those two "error: unknown filesystem" lines are probably associated with my current problem I suppose.

---

### Post by richardth on 2022-03-26
I also found someone with [a similar problem]("https://askubuntu.com/questions/1305399/system-boots-to-grub-prompt-only").

I'll start investigating whether their solutions may properly apply to mine.

---

### Post by richardth on 2022-03-26
[This is another]("https://askubuntu.com/questions/1053895/system-always-boots-to-grub-prompt") similar sounding problem.  But the installation of [grub-efi-amd64]("https://packages.debian.org/sid/grub-efi-amd64") didn't go properly for me:
```

----|  Configuring grub-efi-amd64   |----


GRUB failed to install to the following devices: 

/dev/nvme0n1p1 

Do you want to continue anyway? If you do, your computer may not start up properly. 

Writing GRUB to boot device failed - continue? 

<Yes>                                       <No>

```
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABWIAAAIsCAYAAAB4P9B5AAAABHNCSVQICAgIfAhkiAAAIABJREFUeF7s3Qd8FGXixvFn0wuh9947SO8ohC6ooHCgcvpXT /siuJ5euIpng3rneU8y6koFhARRRQEgrQAQXoRpCtFOul1/ 9uEtgkC xuMmGT/ObzUcjszDvv 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 gACCCCAAAIIlGyB39cr5bnHdfqGP nkFeOd/yUuSDlHm9KV9qRjmyeVeuIcm/j16pJefz/APfqd4h395KllflAZN1UoU/05b/vTX7nFXJsTlbLXjQurEEAAAQQQQACBUiDAy7pKwUmkCQgggAACCBSLgD1BmQu/VcoPa5S554iy0kIUUK26Ai/pppArByu4TkixVCPvQY4odcrLSvk5QkHRAxVSJ1KySYFNgi9CXTgkAoUVoD fUzBxr9JmfK20FVuVeSRRCo1SQN2mCho RuGX1T7nblKWMj//h Kn7jLb1FfYf59WWK3zbM5HCCCAAAIIIICAhQIEsRbiUjQCCCCAAAKlRiDjgNKefUZJK80w0qjaCurQQ0ERWbIf EUZ332qrMqdFDz2fGGIRRKJm5S LUPqOEaR9/V3ZLAXWIIU/H PqdzoCAVEXWBTv/y4pNffL1H9p1Jlrj97SH9stZIefk1ph7Jkq9ZIgV1aypYWr6zftih1 d7zB7H7vlHSJ/skx3cz6R4ej80QQAABBBBAAAGLBAhiLYKlWAQQQAABBEqPQIYyP/6XM4S1XTJW5f52hQLNwNPcxX54vdIPR1yc5h47Kbs5sq1yRQ9CWEcVbbLVb6GS xegkl7/i9NNSsxRy1x/9uTMnFTav/9rQthwBd3wgCJHN5PtzDcumbKfSj13IZm/KuXlmcrqfqVC989UqsljWRBAAAEEEEAAgYspUHL/HXIx1Tg2AggggAACZUkgYaVSZv8qhbRW IS8IayDwVbjEoXUyA SosxFs5TyzSpl7Dsuuz1MASYADb58lMIGNswbmp6Yr4QbPlBG19tU4QabUt6bo7Rth2S3VVBg16GKuH1YnuBXudu7HnLBizq54OyK4PveUeSAsDMrMqc9rPhPTBvOLM0V/uEkhVbKXcnzOPK336NKXM36DME2YUXu0WCrnuBgWtesTMP1tZYa9NUViDnG1d6z/p0jxty3jvPiV8maSQyf9VRIe8x8qa8ZhOf7BbwRM/UEStxUr cJ4yth82D1Kb0boN2yrs7tsVUjd7H6/q762n4xDetPccZOdd7UP5Hvv46G8araxVM5T88WJl7E QKpiR3peNUPh1PRVQ6Fk27LL/vEgpMxYrfcuvykqymy8L6iio1yCFjbu0 PvzeU9O/g TlPnjAjMFwHpl/GL64/HTsgeVU0CD5goefFW 63eTksY q7TmwxUeZeZqXvm7bA37KPzBIbJ/9JqSVx6VrW5nhT10q0JqB549UMZRpX/ iVIWbDLXV4Zstcz1Nc5cX/mr4vh53yKlrkmWzdwfIseYEDbPNoGyVTjXl0CZypzxllIOtFHEYz2U9dhMd6WzDgEEEEAAAQQQKFYBt3/fKdYacDAEEEAAAQQQ8GsB 5o4paeZKnbpo DKnlTVjKD95J9KmLZb9kpNFDKwu2wBx5W5LFapr25QxoG/qdwNzQuOYD22VImP7JW9RUeF9G szLWxylj8sRLSK6r833qe3T6yncIm3G4CS7OYR5ZTPohTVpvLFTEkNxmVAlrlnSM2oNdYE3YmmR0ylTHLjK5zTBd5ziVR6a9PVuL8I7LV6aCQK rJdmqH0l94Thk1Ms 5l88f7P1GCf/6QllVmyuoS10FnjqszJ/XKOOwyb5zgljv6p9TE089ZXV7C1m Bz4 2e/ SgnPJMnWo4dCOtmUtW6F0r94XRl70xT1 GXy/Y22dmXFvKaEl1cqK6qhgnv0U3A5M43H7o1KN30vft0BlZsyTkG53xNY3p 91dmvtLc/U1pwEwW1aKeg6hWktJPKXL/GXL9rlfHbIyp3Y77rd70JbvtGK6TrBqUtW6ikB1Y7A9iQQRWV/u1SJb3dWsGP535JcVrpLz hxB/NCPuGXRR6qZmw9eg2pb30jNKrFby sn4yX4aYiDY42twD4vcpfXlOeFutvoK6tldg XOcqT1fK nTAwq67V6FVE7TuV7f560O2yOAAAIIIIAAAoURIIgtjB77IoAAAgggUAYEsnZnv8I8oHGDguGpu/YfWWACEBPCRnVWxKv3KaRSzhi2cd2VdNdL5oU77yt1gHlhTp18O /aJdudz6jc0GrZH6SY7W dorTYH5We2FMhudMhhNRUUP a2dvsPewMYm01W5nwtqO72jjX2RqacLeh43dmksglFwhif56tZBPCquEVKvfiWAXmjI4M7fiK4l/4/ZzH8PWDjFnzFXjdEyp/TaOzvid3K9NMfZu7eFX/3J089bS6vYUs3xMfn x/P66APz vciNy tsfhyn1kYeUHPexUlb1VEQ3H4fFHjX9/98rZW86UlFPjVZgeG7tzAjcr59T/H/nKPmbfooandOHre7PXuPUVsiklxXWtJrLFACmkKxDSn3or0qeNVPpVz2skIouBdcYqIiJ4xSoztINk5V6or7CJ/1JIeVSFHjwViVt3W7C1EuzR7xumqVkE8Kq6WgTSI9UoPNfI3aFdnhJ8a sLVDbzH2/mXXVFZA0Rwm3zVCGGbx8Zgmrq5D7JyqiV5W8 2XuN1MSzFJm0z o/NCq5rMDBcplBQIIIIAAAgggcDEECGIvhnoZPeaQQWPKaMtpNgIIIFCyBbJOZycfAeXLedSQrNhVyjTDVQMGXnk2hHXsGdVJoUPrKm2aY1TbIYWNyQmickut3EehQ3JCMce6sEsU3DFEaYsOKNORxTT36PCF3ihjSawZbRuooCvMlAguWVxA32EKeS9OqccLfYg8BdjrD1GEawjr LSieSFRYQ/joafV7S1s Zb5RHZT6GCX/hZQTSEjuypl83KlL9skdevk0xnInPeDMtLCFHLVIAWkx8vu8oIoW88eCnx7izLWbJTdBLEXfrmcT1Uo5E5RCmyW yY7MwdrYrL5/sL8ag9XYEvj9bN5Qd9uM1rb9XuP6lVzRhCbXx25Z7oJTp23CzMlSVUzdUDiSWU5RtWb6ylj2SpzfZkRrlcMyglhHdvZFNB/uEI XJvv jJTPDiOb4LatPdmK6DHLSp3XTcFRqQoa WXSnojRmkvvqbAxo8r9MztxExJ8LmZkmBfHYW9MlQBxYTM33ML2e3YHQEEEPBQ4Pv50z3cks0Q8E8Bglj/PC/UCgEEEEAAAT8ScLwOy/MlyzmCzabAJmenCsjdO7BxQ/PbX5W537FNviC2dh0F5gtNbBUcgVCy7I4spliWJGXtPWaOVF1BTcvnPWJAAwU6mlTEQWxg986FeAz PCgeeVrd3sKXb5lP3fp5gnaHpK1RA3MulssxCjNLnfKcl6zVs8xcpafygNvaD1NYr ou68zcyNuz5yJOm3KnHNmj2 XECefUGoUO290W7n6lZ/XP3tf 60qlfjxXaT/tNvPbFpwuwG7mvHVc42eWkNxvLMyUII7fnvnZ/D7YMU2IkXAGsWb 2f0nzW9qKLChyxv/HAUFNHRzfZnjZDmOZe4BVUYq4t7 OfeISAUOuFkR 7YpfuYOpf6wT6Hj6ztKkXbPVtLnexV49ZNmHudzTFuQvSX/RwABBBBAAAEEil2AILbYyTkg32DRBxBAAAFrBYp6ZFZA ewwNHtkbL5HgN00xZ7imI0xVLbybv6aYcpyRCNZSW5mbAwPLVha7uvRvcuCC5bj8ZqUnNC3nGy5gwLP7Btm1hV9dBZgRhNasnjkaXV7C1ZT7lzDnODx Vsy4l1YzBzLvYty1T6pyDeVYGBPbIF8SawNA5gNw83v/gDQox06u6XUKrWRO uz1Y9krP6m 2PbRQiQ 8p4yMagoaNFphLczI3fLZ16Z9yQdKWmAmL3YMeXeNkc9Amt84fu8K6xySaubIdU7qbK5756Uf6eH1FSBbuCPZTVNA5w75vqgJUGBbM1ftzEPK2rPPbOMIYg9kT0lQbbDKjW3kOFCxLfz9ttioORACCJRRgaL20ZZaTZfiDg5l9IflArqoAAAggggAACfiMQYEYJSr/LMVesXReeJ9YW5ngLUaLspx2TnOb7q8bp OyXbEXkvqnIb5qZUxETtjrn9EyQPd784vLkuiNBsicUHB14JnTKn9w5ikl2Ezjnb3JQ0Ye7 Q9x7p99aO 5C3PzSRGUfyGf3NDPW/8Ec45NjfOEsfHZ6xQRXiCkDfzjFFX8o5sm5lll9nM km9eAla9rYJaXWj74vvcs/qbqQO na2MpFAF3/sPRQ7MmyRnrCrs0PTc/mDuDwWuLxNiny54fQXUyJ7j1WbOSYElPOc kpaecy7NaPvdjjK V8I13xfYXNqnlNvGmyu5pcI//rtC8w16d7MDqxBAAAEEEEAAgSIV4HmdIuWkMAQQQAABBEqfgK1TJwU7BqWtX6p0Dx7LD6jveAuXXZm79hbAyF0XWC//m7oKbHqRVkQooIFj1O8xZfziSIpcFvs ZRZskpkGM2ck76nT UZRnjaPYbu WegiNem8h/WhvectL/ HVpdvjuer//69ysw3d4DdjKx0DNy0mf7p21 Sw8z8qrVNCSeVEbcnP0YJ NmurMOOqTnMC/Ha5B/Oe0gZ204Xsg2mP9SvZMo4Zq6lpLxlmYsr0zGwNd8S2KyxMxTP2n g4Cjlw79nB7BVKuUE5zUUPHyQQgv810uBzhHuUeZFf47PuxaYliL/cfkZAQQQQAABBBCwQsC3v2NaURPKRAABBBBAAAH/FIjqodARJlxK26Lkl75RZmLeatp/36C0DY55H7OXgO7mZTrmbxhZ82cp7YjLCLfjq5Ty3X6TctVXcK9888P6UcuD vYwIVymMr6eq0yXFy3Zl32vNEdGlX8JM3PbOgbt7Vqj9MNnh2XaN32l1M35N/a/n71ur5dNsLp8 eqftFqp846cbU36QaV9udoEe UU3KeNl608u3ngoEEKMtOiZs6eqtTdqfnKSVfWph Uus5fA3ozt3MtxzBwE7puOntNm9Yoa95HSt3lM8uZHYP6dDfXV4bSZ3 rzDM8JgCOmaM0d1/0dOilYJMJ25d/ndczbZ9Sv9loyg1TUJcWOeU3UMhfblR4gf9GKtiR/6qSgq51fD5EQf46KL/wxJSAAAIIIIAAAn4swNQEfnxyqBoCCCCAAAL IRCsoPH3KnzfM0qO 1Txty5RUIemCogwb1I/sFMZmw8q4LrnFdK YnZ1q0crYtxSJUxbq6T7Jym9e2sFBJgRpivjlHkiWIFj/k hxTkg9vgOpa3NndvTBKxHHdU0o1WX/Ki03PcFVW lkHY58xC0uFLhg1Ypcf5sJdz3m0J6NZTt1HalLTqmgEbB5tHn/GelsUKi6yj18x1KfnCSMno0lS1xnzJWJyrAmGRtOOcrm/IX5P5nb vvvpRzr/W6vecuyu0nVpcvH/2rV1bWu5MUv6WngqqkKWtdnNL3pMnW7SaFdXG8YMrHpfpARdy9VQmvrlLyhAeU1qOzgmqbjpZwRJkbNyrDjJIO lMnhXbwsXyL 0PgkGEKmvOB0t94TAkbeyioRqCydq5V tpMBXWuqfQ1h3yseM5ura5SeH9zfS2aZa6vXQruXN9cXz8rbelx2WoFyZ53Gl7zgq/2CrutmzJeMF/kTPybMnq1V2CEeSna2tXKOJApW8cbFN7LzbQFhasleyOAAAIIIIAAApYIEMRawkqhCCCAAAIIlDKB4DoKnfSsguZ/o5SFPylzzQrzMp8gBVSprqAh4xTS1/WFUyZsvfYRlasxSylzVikjZp4ZZRhmHknuoNA/Xq2wQSbYLE6efUuU/MrCfI81H1La2/89 1b7XneeDWLNi4SC7/y7Iqt/opT5G5Q6Y7NsdVoq9MGJClwyUYm7c94Mf6YNZhThtRMUmfK kmN VvrCIwpo0t543avA1ZOUUNgg1uv6e4vrbXv9rXwf/RtdpXK3HVbyR4uVtsKMUK1YR8Gjb1L4tY4Rm4VZbArof7ei6i5RyszFSt yQqmxJuAtV0kBtU0/urGzGXGb/7F/L45ndX oNUiRz4Uo5f3vlR63QCnp5tpteonCJl r4G1TTBDrRV3dbhql4HseV2Qtc339YEbTz9lmAtgWCrn/YQX99Hcl5g9iTRkBl96pcuWbKGX6EvOFzmJlpJmXeNVoqJDrLlfY6M5yvg MBQEEEEAAAQQQKAECtqlD5rl7tUEJqDpV9GeBds9WLlC93Lcc8lbZAjSsQAABBIpUgPttkXK6FHZaqQ/foeStHRXx2QMKKfWPNlvdXqvLt6ofUC4CZwW439IbEEAAgeIRON/9duPD7ua2KZ56cRQEvBUo3Bf 3h6N7RFAAAEEEEAAgRIgYE/INxGuo86/makMtplf27QvdfNLWt1eq8svAV2KKiKAAAIIIIAAAgggIKYmoBMggAACCCCAAAL5BDI/eliJG8yj6h2bKrB6hOzHdiv9h1hlBtZX2P9dVshH1/2P2 r2Wl2 /4lSIwQQQAABBBBAAAEECgoQxBY0YQ0CCCCAAAIIlHGBgA59FLR/vTIWz1NaQqpsEZUV0GaoIq4dpZDGIaVOx r2Wl1 qTshNAgBBBBAAAEEEECgVAoQxJbK00qjEEAAAQQQQKAwAgE9xirS/FeJhjtnAAAgAElEQVRWFqvba3X5ZeU80U4EEEAAAQQQQACBki1AEFuyzx 1RwABBBBAoIAAL0UsQMIKBBBAwBIB7reWsFIoAggg4JXAg2v 7NX2L3R y6vt2RiBohTgZV1FqUlZCCCAAAIIIIAAAggggAACCCCAAAIIIICAGwGCWDcorEIAAQQQQAABBBBAAAEEEEAAAQQQQAABBIpSgCC2KDUpCwEEEEAAAQQQQAABBBBAAAEEEEAAAQQQcCNAEOsGhVUIIIAAAggggAACCCCAAAIIIIAAAggggEBRChDEFqUmZSGAAAIIIIAAAggggAACCCCAAAIIIIAAAm4ECGLdoLAKAQQQQAABBBBAAAEEEEAAAQQQQAABBBAoSgGC2KLUpCwEEEAAAQQQQAABBBBAAAEEEEAAAQQQQMCNAEGsGxRWIYAAAggggAACCCCAAAIIIIAAAggggAACRSlAEFuUmpSFAAIIIIAAAggggAACCCCAAAIIIIAAAgi4ESCIdYPCKgQQQAABBBBAAAEEEEAAAQQQQAABBBBAoCgFCGKLUpOyEEAAAQQQQAABBBBAAAEEEEAAAQQQQAABNwIEsW5QWIUAAggggAACCCCAAAIIIIAAAggggAACCBSlAEFsUWpSFgIIIIAAAggggAACCCCAAAIIIIAAAggg4EaAINYNCqsQQAABBBBAAAEEEEAAAQQQQAABBBBAAIGiFCCILUpNykIAAQQQQAABBBBAAAEEEEAAAQQQQAABBNwIEMS6QWEVAggggAACCCCAAAIIIIAAAggggAACCCBQlAIEsUWpSVkIIIAAAggggAACCCCAAAIIIIAAAggggIAbAYJYNyisQgABBBBAAAEEEEAAAQQQQAABBBBAAAEEilKAILYoNSkLAQQQQAABBBBAAAEEEEAAAQQQQAABBBBwI0AQ6waFVQgggAACCCCAAAIIIIAAAggggAACCCCAQFEKEMQWpSZlIYAAAggggAACCCCAAAIIIIAAAggggAACbgQIYt2gsAoBBBBAAAEEEEAAAQQQQAABBBBAAAEEEChKAYLYotSkLAQQQAABBBBAAAEEEEAAAQQQQAABBBBAwI0AQawbFFYhgAACCCCAAAIIIIAAAggggAACCCCAAAJFKUAQW5SalIUAAggggAACCCCAAAIIIIAAAggggAACCLgRIIh1g8IqBBBAAAEEEEAAAQQQQAABBBBAAAEEEECgKAUIYotSk7IQQAABBBBAAAEEEEAAAQQQQAABBBBAAAE3AkFu1rEKAQRKgEDm4bWa9t/PtWDTbzpyPFkZps7dJk7V5MFhRVD7dM37 3V6cWVL3fnZZF1ZuWCRR2c puvf3ObyQQWNfPkd3d624LZFvWbllPGaNK Kxr/9qv7YsKhL94fyLuzvD7UsTB287T/ebl YupXIfY9/pwlj39Xm7nfq66f6KcTPGlHU9ytv 4O32xcvX m63i/ /bl0eRZvX RoCCCAAAIIIIAAAlYLEMRaLUz5lgvYT /SvM9na/6KLdp9 LRSAsqpZtM26jVouEYPaa4KOeO 4166UY/OTTpbH1uQwqIqqnaT1up1 VUa3awl1qu mNP uBL4 r/V1va8pVFfO0I3neMxo55SeVH/GYpt/b3vlZ7jqXAyggOEwVqtdTq259dc24wWpbuagGof uWU9P0UdbI9R60GANqltOQTapdrNgy71zDxDVaaTum3DS eOBmKn6/KdiO3QRH iIPrvjDr23o4f Pv8B9S3i0kt cdb4eNt/vN3ed3dr2lt66uNLS4r fuVtf/B2e19ayT4IIIAAAggggAACCCCAwIUECGIvJMTnfi2Qvne nnzoba06blP5Bm3UqV8NRWae1v4t6zX9pZ8UX22q7uuStwnVL4lW13qBUmaKjh/cpY3rftRHa1do6c P6pU/t8kTxvrS KB6nTTkkipmV7vSk J1 JdNiv3yXcUu3a5Jb96jnhV8KTXfPgkbtGpLumydx mfEwcqogiKzFtEkLrdOlkvjotQ7fLuCw9t2FnDGmZ/tmn35yaIzXS/IWt9ELiwvw F tUu3vYfb7f3q8aW9cpYcL/ytj94u33xnrLSf73jWbwCHA0BBBBAAAEEEEDAfwUIYv333FCzCwmk7dD/nnjHhLCR6vznx/T30Y1dAslUHVgxV1vchJ4NB9 ke848vm9XwoapmvDXr7Xni/9p9ogXNLbOhQ58/s9D2w7TPfd2cNkoXouevFfPLlmiT74fq55/qHH Ajz59NgJHTfbhVapZEEI66iATRUbtFTeccCeVIxtikYA/6JxpBS/ELD8fuUXrSxEJbjeC4HnZlc83aCwCgEEEEAAAQQQQMBPBAhi/eREUA3vBU4tnK6v9mcptOsf9VCeENZRVqhq9xyp2hcs1qZy7UdpRJuv9fr6vdqyJVWqE3rBvbzbIErt2pp0d8k2HT/ueJTfxyA2dw5I14PPe1ZD5p1dkXeO2ET9smi 5i9bq/XbD5p5ZE8rLbCcqjdqpV7DRmnskMYql68hez6coD9P3e y9txzxHpnkLu1Xae2LdAnny5Q7Kb9OpJoV0SVumrbd5jGjnJpH5Ss04opXTPtJH89Zrz/EMRdZupejxN6m1bwd32StFc//2R70S51pQrJ4aNMZlRWvdM MJDc8T5idr9w9faOpXsdq455iS7OGq2rClel8xWte58fS2ml75u8wJOv0Waepbs7Vk6yEl2CqocffLdcfdV6hl/hOsVP26bI6mzVyqTfuO6HiSTZEVq6peq3aKHv0HXd4y9wT44uN9f/PWx7rtfWmvozZW9Qdf65MtlLI7Rm971B 8vB69OQFe36 s9PSm4q7benJ d g/1z2iLzVC/5p2o1qc81D79P7ND iTUwP1/Iw/6xIzlYzl13vmMa3 5EN9 J3j/pmpyDqtNOiGm9Ui9kFNLoo5tr2 P3va3/brg5snaNrv3fTI9Im6zHXOIIdvepyeHfOcFkUa84 MubF0LF55njlPidq5YLamf7taG3cd1sn0YFWqUU9tevfXqKv7q2XFnMKd23ta/9zCPb3fnqkMv0EAAQQQQAABBBAoAwIEsWXgJJfOJqZq5dL15gVVgeo qHchR24GyOb8t5ZNgUFFNYeri7r9hOLW7DUrQtS0aSGG25Zrr sfvlvOWVmPrNQ7765SfLsrdP/whmcOVq216xyx /X9mx9rXnBTtW95idrVrKjQ1JPatXaVpr wRqt naR/39Iyz0t9qvW5Xg/VSTTlZWrT9Df07U6XdhT6t3YdXvCKHnh uY5HNVL3XgPUNypLx3eu19IZrxujX/Xcv8ar9Zl3jZ3W0uf/rqcWHVdko24a0q 2Ao9u0cLnntSK6lmFrE2wOoy9Ww8NdBQTr5Xvv6/Fh5po5MOXq/mZkiuqZZ45HzK0feoTevDDncqo3FSXDu2p6rbj2rhkmb54YZ1m2SXr25pfkKwPfFJ/9ji/XPB3brZKsu6jOwiX6NW6G1Cz/Uo mV9cGk3nnC9sPfTtHdL5vrplor9enXWTUjMnXy8G/avnaevqo/wCWI9cXH /7mu1RR7 lLe63sD77UJ8fE4/7g7fXopbnX9ysrPb2su3NzT vTWG3bhOrLmB3aZh5TaOHmxYbO4hJ/0c /SoHdW54JDq293hO18pXH9Ph3RxRmpssZOMrMgX5yuxY 85Riaxb2/ulokLf3Z2/6Wz1FRzfQtA/WKmZ5si4bkDeJTV21TLHmj6naV/Q9Y mokdee9mNa/Nzjen7BYalqM/XqN1R1okzLDv6iuJlvKrVBX/1jQO6fqd7U33nG5fn9Nnv7M//f qGuv drHVXxvQAzXw34EQEEEEAAAQQQQMBCAYJYC3Ep2kqBvdq50/GPybpq0qQw0ZeU stczdtsigpuqY5tCv yq9Qt8/XmG2tNgY45Yk/pwJZ1WvdbgJoOvU1/ji4wRNFzpJDa6jwgZ4zvnkOaZoLYpFptNGBA53OUUUcjJr uW5pXV5jroJ6sq/X5vffr3RnTtfCaxzTUZf6ByMadNaCxo7h0ZS4q4iD2yHy98NJyxTcfrVeeG6vmZ0LOTF076ynd9fpsvTErWq Ny25j5oYZet2EsAHNx rlV0ervvNuZdeYTs/p1ilrztFmT1cHqlaHS1XLufkRHf3CEcRWU9sBl577ZV2/z9MbH 1UalRXPfzmRPWvnIM6vqeevdWMzvr0Hc0abKa2qOtpHQpu55P/LzsVfO8Len1EdTmJkntpyo1P64dli7Q8obcGn lyR7R4znol2Vrprtee1BWugVHGaR08EeJSIR985H1/Kyhwsdb40F5L 4MP9cml87Q/eHk9en1mvL1fWerpde0lj sTqDZtm0ox27Vta6au6m3mH3ez2Lft0Ha71KRtS V 12Tl9W7fNlOvmRBWjUbqhdeuV9Ocy3tM5yn60zMmeCzk4vX92cv Vi 6j5p88LFWx6xU0oB LlPwpGnlojgzFr2Wro52/mF1ZvHW8 jcN/WiCWGD2l6nV54dpUYuf5XIPL5RG066fDHrZf0df654fr8t5MlgdwQQQAABBBBAAIESJWDB8L8S1X4qW2IF4nX6lKPy5VXB9dHxQ7F679X/6l 5/322QQn52rhn3v yP3/pNT31t4m68a7PtN1WS/3v/4sur154kIy9qzTry2/Nf3M15/vlWrs/TdU69NXQwe1Us1ivuCg1aJEbwmYqNTFeJ0 c1ImT4WrexjQ0w4zgKtIRr e32zP3O21IC1fPq4eoRnq8Tp3K/S9JUb17qbXNrh2rN8h5Ws2yZUmsmQc3SF1HDssJYR1rbao68EpFn2vU2fmrUKhPjy2L1VaT/dcaOkr9ckNYR4nlu jaEfVNRrxXPy45WKhj LRz5Us1bnhOCOsoILyj nQ2qUvWr9pnRuCdXTKV6XyfWqCC8mdFQeVVq9qZocg VUPyr/7mYyM83q2k9wdvr0ePYXzc0N88valPpbYtTCyYrm3bHE8 OJYDmv2Pv quR83c4zlrfjVBbIIqmdDWx6lpcl09vN63xizT7 Za7zzqijMhrKOISv2uULTjXZKFXLy9P3vd32r3Uf WNjMLwTIti3epbEqcYmJTTMDcV9GNCtOIQ5o/e72ZrKW2Rt11VZ4Q1lFqYOV26tj47I3S6/qbp0p8vt8GhatipQqqZP6LZLhEYU4y yKAAAIIIIAAAn4pwF/x/PK0UKkLC9jN2MjsxXWwp05s14Jv5ptH nKWljV13dj2eR7P/n39QpmBgWeWoGqd9JcnJmhUs8KNrM0tMHLYo5o5wfGyLrvS4o/r4PY4ffbmh3ptYpx2PvGC7uuefyLUs3Up6t l7F hT9//RgvX7NThRGcKl2dJMnO0OsJN65cUE1Jkzz276OlbtehcBzye/RKyCkrUvr0nzFY11KhxPq ARmrq Ae4421lxbjsc6aaNjVu1qiAWIOmDU1kvM/U2bFN9jjbYqta3bqql 8UVqxY3hw WUnJrrWooR59G2nqzk16864ntKVfJ7Vv3VTNWzZVg0qFHwnuOJL/9Dfr9Ut2f/D2eix7nl6d38at1NaM8J9vwtbTaqzyR9dqwbJd2qEsrTpwhRrWTs2 /wV3U9uzc5/4hurR9Z6k3buPmfJrqFkzx73AZQlooMYNzc Oj31evL0/ 9Lfqqp/dAu9u22jYpbGa9AwM2eAWZKWL9NqM5V7s i 5nmYQiwZO/XzLrN/VGt1bHKhb0h9qX8h7rfNxuj1z13nKy9EO9kVAQQQQAABBBBAwO8ECGL97pRQIc8EzEhYx78vjyXo9Gnza 6o2FY36OP5N5inAufo3uve1zY3heW 0MqeGq99P83Rv6d8of/87WWVf OvGlD9bKJly5441k0JrqvOF2LaFBJVRQ06D9HESfHadctn u7tORrV/Q9qcIFSi Jj 8Ef9Pjdb2ldejV1GjpO17auqcrlw8wYKelozDt6ed5hM2LHMb1D/uGRRXH0/GUkKdE5NLmOhj9ys/rmeQGWy7ah1VXT WOKkp0hYjlFZf/722WjcEWVL446uxzS/DY52YzCMg8Vly/v5rZZvrwZm22yYVNpR9xdrLULD1P d9lkh smZM/9tsLZFJsaXfeYXiw/Q5/MXanFn32oec4cPlTVLhmgOx64Qb1q l5z/ pvzgZbupTs/uDt9WgppbNwf/P0qj62FmrT2qb5W3boZ/sQtYpbr 21u6hn8BrFxZ3SH678zQSx5l7bopUKPfuNR9d7spKTHKrm/pkvhzVD5ovg/unt/dm3/la1X1 1 882rY2J1elhg8w9NlnLF61Vmq2povtn/0nhc89MMnVy3P8qV9KFH7Dwpf7W3m99bjc7IoAAAggggAACCFx0ATeJwkWvExVAwAOB mZuWBOCHjuoXbvTpXrej izhZpHqXuO06T7D mWJ5fp9deWqMuTl57JdIODz3N55ARcIcGeHddWv6VamUBx976d sWM5mlQNINvz u0bfZMrUsMVbcHn9bkIS4TwZq91jse7SzWJUKRzrlKkxRavb2Zi/dCBw9XuHMO2QTFOx5LzTNlRLIJ3wuO7r1QiYX9PNwEII76nD6dYX7N1zfMtwGOaoaEhxdvCOtto2xRanXFTXrS/JeZdEy7N63V4q1MxV3 qfz1bTe6 MMGPofFv8q7/51gZv9irZ/cHb69EbGd 29TdP7 oTrjZtzPQkcWa6l73pSlmzRRW7PqKxIfv0oAllk7ud1DbzlsVaQ1qYyQmKY3G5fzq qMxz/0wx99TC3j 9vT/72N8q9VT/ju9pw9plWnJykIYHrdSiuHTZ2vRVP19vVLn8EaZOju9Rj51wDg6ud97T4mP9Lbzfnre6fIgAAggggAACCCDg1wIXeh7LrytP5cqyQJi69mpn4rB0xS1aWWAeWG9kyve9XuNaBSpxxaf6ZLMjZMteypfPHoqZPTIqb4mJZjSNY4kq7 HLt zmMXFH9mnPUPrZQ QttEh/Mm94PuyYoKGW2rXLG8JKB7V5c 5MrEVz0MhIx5jMNKWakNn9EqYWLeqYj04obtXuvAM13e4QoQYNHOOUjmnPbvN6bNclc7d27na7k48rAxTgHAiaO6ef 2Lq13c8CGvXrl/2FKj/XrPOfB2g g0K9bCs wNbtDYwooqadhuoW556SKNNtTO2bNFWt33TE5/C9bcL95 8CN5u7x2hJ 0157rY oNn9fGujd5ej96V7svWhfH0tj94sr239alvXsJV3txbt21ZozU/BaprtxZq2b2TItet0 qNO7RboWrbtqEvND7sE6FGjRwTwR7Vjh2uE6yaVfY92rXHhyLz7OLt/dnX/halvtGXKChri2IWn9DpJcu0NiNAHQb08mAU6wXaGNRELRzv krYrHXOF3 eb/G1/mfL9Px e7568BkCCCCAAAIIIIBAaRAgiC0NZ7GMtqHSwDG6vJZNScs 1EtzfzUv3Ti72NPTncGYZ0s1Dbr/lH9BHN d8PZ aXrdGmhRz/lN25aIF2uBaeuk/fL3S85SpKrVt7Mh9oun6d/b1WOZO65mpVLFPE2lS7tmMY1EFt2OCYazV3ydShue/riyJ SVfNOrUUYB4b3bZ5X4GQMvfIjYYOdT6Wu /L9zR9V/7ENl1HN8zTnDVnQ4PWl/VUVWVo1cxvdHZzu44tmK2FRTo/bJQqVnQMjTIvt9qb51l FzepSq8eamXumAe/ 0I//H52RJn9WKw mrPPPOLfQJf29aQ/5Cm2GH84oe1r9yk f aQcEgHHKPmIqLkfsYHT3wK19886T uUN5u7x2yJ 0tzv7gWX28a6N515GX16O35Xu7fWGuL2/7gyfbe12fVi3VJtCun7 eqTWp7dXtkkDZ2nZUF9t6fTZzhzJtzc2oWd n/vDWs1W/3mYgbKbWfPm1drr8YXhqyVwtOjOJurelnt3e2/uzr/0tqk9fdQmxa2PM95oVs1GZQW3V/9L8Xy760o6aGjSivULMn5FfvvaVduf7I8l aqs27Dl7n/e /r7eb01bdnymv1xzs8Zcc7/edze/ki/NZR8EEEAAAQQQQAABvxE4z7PXflNHKoKAe4HQlvrTP/5P x96X8temqgbv2qrDs2rKjj5qLb/tN68rdqmynVrmlk9L7yEdb9aVzf9Ue vn6lpP0Xrnk4h5vHHK/WnPsv1/NJZmnDTFnXtWN9MWxCvPWvXasuRdFXodovGdiz4D vUTXP1r1dXmYPalZ54Wkf3bdeGnSeVEVRLV94xvFjmh3W0uNnlI9Tuq3e1 tW/6oH1vdXOzP956pc1ionLVLuutbRy9cG8MMe3m8c D QE2BnafMTx8SltWxyjsNzwuEZrDb4kz3OuzjLC w7TkHfiNHfa03roqDlW1VCjX1XdxkSrRe4EpjXMXLkTNuvBF2L17p13a1mvrmpXp5zsCb9r5/r1Wr8vXq1u76zhnbOrFdDmGt0xIFaTF8zQg7f/ot5dGyrylGNk1DFVrB2spAN5q /7TyHq1KOdgmM3aMbk55U8uK1qRwWbYLmy2g7uogYhOSXXGKTbxy/WxA/j9OIdD2tFr7aqEXBUm1as0vbjwWp07Z80sjADYgvh71nbD i7p/6hecGN1bF9I9WpWVEhKb9r89JYbTodqhY3DdMlbqc89szH6/7mUmmP k8htvfMJ3crz9orq/vDmUp7WB/vGmne4 Td9eht8V5vXwhPS/qPt/UJbSXz7jut Hm3kroNVUfn9DNt1a1zihYsMd90NOivNq7zXVt8vdtaXq27hq7Q4999qYm3/6ZBfRsq/OTPWvTDUdVoHKx4x4uqCrF4fX/2tb9FdFX/7qGKNX8Of2rLVHC3vupTYN5b0xAfPKsOv10T1k/SlJhpuuvG1erVq5XMH0lKOLxLa2I3q8E9H6t9w5w/472uv6/3W9OWjFTFn443L34zX2 6fUqhECeOXRFAAAEEEEAAAQQuugBB7EU/BVSgMAKhjS/X02831dzPv9b8FVu18oeNSg8up5qNemrs5VfomkFNzetKPFlq6arre2nGE0v1/f05hOV5qH isretJLqjd/pqbOXKH1MTvNmM8wE 620cjxY3Td0Gaq4Ca4ytj/k bszz5mQFCYoqrWVPtBAzVk9BXq19g58WmxLLbaQ/WPl0P0wTvfKnblPM3ICFfNZh01/rnx6r7laRPE5qvGnhjz4rL5yjsRwEEteON1LcjdtO99boNYhbbXn//5F9lf/1JLf/haG9IdI0tbqsIIlyDWRLO1Bk7QG/VjNOPzRVqxcam Wp6uoKhKql6nlUbc0k3ReUY6Ran3g0/pyTpTNfX79YqZvVWRdVoq qFJah33kCYXWRBrRjdefpf ceJ9fTR/k Z8uEapGY76t9Y9fV2CWAWrxR//oVdqztBHs2O1ceFcrTT9oUqDTrrmJkd/aGwePi7EUhh/jw5bV9E3jlLG6s3aunm1Ni5Nlq1cJdWo30v/d dIjexd95zz23ri43V/c62zR/3HZQdvt/fI5 xGnrRXVvcHlzp7Vh8vG n19eht d5uX4jry9v 4NH23tanipl6wDxD8fMxtenWUdnfXYWoS/e2Cljyk8q1bZV3HlLLr/dIdb9vsibX FAffrdOcz7doHJ1W2vI3x5Vk8X36p 7ghWS yWTt6fKub2392dv7/ 5lQpVzwFdFb5kqZLtweoR3T3HNl lffG0VVX/R55X3W5fa8bcVdpg7unL00NUsUYdtb7iNl3d2fWvyN7W3/f7rU ng50QQAABBBBAAAEESoyAbeoQ53uzWRAoUoF2zxZ8D/GQQWOcx/h /vQiPRaFIYAAAggggIAnAqf11YRb9MbmzvrrVw8r2pNHRjwplm0QQAABBBBAAAGLBc6XJ R 5mkVXuj8lqebsh0CRS7AHLFFTkqBCCCAAAIIIIDAxRVIiU80s2znXbJ XaQftkhB7TqoIyHsxT1BHB0BBBBAAAEEEECgTAowNUGZPO00GgEEEEAAAQRKs8D29yfoiXV11aNzMzWoEan0Y7u0/Ltl iWwga7/U7QqlebG0zYEEEAAAQQQQAABBPxUgCDWT08M1UIAAQQQQAABBHwVqNHpUnXat1YbF83Vj/GpskVWUYP2w/XA NEa3LRQE8T6WiX2QwABBBBAAAEEEECgzAsQxJb5LgAAAggggAACCJQ2gRq9r9ej5j8WBBBAAAEEEEAAAQQQ8B8B5oj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEAAvHGYAACAASURBVECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9TkIgqsnDJeQwbdq6l7LmIlODQCCCCAAAIIIIAAAggggAACCCCAQKkVCCq1LaNhZVggU1v/c6/u yJJg//5ph7oFlrCLEp6/c/HbdfJjXP1/tT5iv35sBIUoZrNOmrY Os0qkMlFfaboRNbYzRv6Vb9vG2nft6xX0eTsxTQ7wHNfbTH Srl8WdWl 9xRdgQAQQQQAABBBBAAAEEEEAAAQRKnEBhc48S12AqXAYETi3TtDmHZWsyXGNLXAhrzk9Jr/95ulh83Du678H/ae6WdDXqM0jDL20s /YY/fehR/XyilPn2dOzj/bM 1Dvfb5QK3bEK6pqedk8283jrawu3 OKsCECCCCAAAIIIIAAAggggAACCJQ4AUbElrhTRoXPL2DXzplfalVKuC67bpjqnn9jP/y0pNf/PKSZO/Txq/N00F5LVz/znP7cLty5cerwabrn3i8171 fa1CXW9UDxlXOCjBsPu0QtXNVCzBpUUtvJ1jXgsRpkX2Mebj60u35u6sC0CCCCAAAIIIIAAAggggAACCJQsAYLYknW qO2FBJJW6pOvfpXqXa1xfSMKbp1xRCunfaSP5q3XnuMZiqzdStHjb1LrglvmrLHr1LYF uTTBYrdtF9HEu2KqFJXbfsO0/jx/dQkMnfH/frg5gma9ns3PTJ9oi7LzhjPlpoep2fHPKdFkSP0r49uVItzDdU8X/2Pf6cJY9/V5u53avot0tS3ZmvJ1kNKsFVQ4 6X6467r1DLcr7WZ4NeHjlZ37W4Un8pv04fLz s4MaX6s6/Xa7T77 s/y0/opD6XfV/j96hQXUCXbQ89ZGyNsRowSEpsPOVui4nhHUUFNpylP7Q/Rs9v2KJ5q25Se175NyWvGpvdpUqNgyi61O 9vD8zS7Td rD397tP70fv15vsLtW5/ggIr1VOHgdfoT O7qVa UNir8s97cD5EAAEEEEAAAQQQQAABBBBAAIGyJsDUBGXtjJfy9u6fNVNLE0PVfdxwNS4Qdp7W0uf/rsenLteBiDYacvUwXdY0SQufe1LvbspyI2PX4QWv6M5739LsTZlq1GuArr46Wt3qJuunGa/rvvs/0paU3N3qKTq6gRneuVYxy5MLlJW6apliE6Xa0X3PHcKavc5f/5xijy3WPx94XxsCG6vPwN5qWyFePy/8UItMzMuVrI qydrx90iQb3qKHEbfP14t2TTLjcVIOHNlfAzh/1yhs/uhzDGx/Tts3bdNpUr1H71orKIxSuSzo2MWuStWnT3gJ28qi9BXfzdI19 2f665M/6Hj9nrry6gHqWP6Ilk17QROeXa4TnhbCdggggAACCCCAAAIIIIAAAggggMAFBBgRewEgPi5BAiYE/XTmbtlrXK5rB5QvUPHMDTP0 qLjCmg Vi /Olr1nb3frjGdntOtU9YU2F5H5uuFl5YrvvlovfLcWDU/M8A2U9fOekp3vT5bb8yK1mvjajv3rRfdR00FirY1YqaUA/8xqq3CVNKxfFmZjRPJIf3bjgcXLXXKD Z3b8ZaeC731Br4 oLmcTkntpyo1P64dli7Q8obcG54yK9ak NQfr/kfHq6m2KX3sY5p9vKFum3y7hkWlqN6BG/Tylp 1Q/3V0XFcL30OHTxsdrKpZq0a5td4bf5mjlZntteoq1qrSk1HW7bpsNnGriZ553b1sL1nfLz8jf3ACdW5/xU9dXmV7OPePFzTJ9yvd358Tx t6667O7iOAPaycDZHAAEEEEAAAQQQQAABBBBAAAEEcgQYEUtXKDUCh fM1KJTQeow9kq1cpOdbVkSq Mm7us6clhOCOtouk1VB16paDfPsZ 502pIWr59VDVCM9XqdO5f6XpKjevdTaZteO1Rt05hVTtfuof0ub0uOWaVm8C2tKnGJizdDZRn0V3ejc3Beq/5k9K1 qccNzQljHyvCO6tM5xDz7/6v2mVkZziy 1KdGddV0FlBV1aqZX8rVUC3n8NUw87OJlhNO6Hha9hG887ErKTHV7BikiAhzcrbN0jOvfqFPXpuiqevMWYiIcAbXWYlJOjPIOPswkqftzd3e218r9NbowTkhrGPfgJoaMbKLQs2Z/XHxFm9LY3sEEEAAAQQQQAABBBBAAAEEEEDArQAjYt2ysLLECWRs0WfTtymz8kBdO6SKm onat9ex4PmNdSo8ZmJXbO3C2ikpo6A9Ljrbinatm2/c8Wip2/VIjclOlcdN8Gk aWC84eq6h/dQu9u26iYpfEaNCz7Afyk5cu02mSQzcy0BOd8edgF6 9Sgbp1VS/ftAsVKzpGACcrKc sCD7UJyRY2dOiBivEZLsKDTGBZPYS4lyRpjRHnhrirY/djHR1WczcvF3qztdidVEnM6OD9ub73HVbj9vrupMXv2/QUI3z3QnDGzcwPSXW9Jn9Oql2quhFcWyKAAIIIIAAAggggAACCCCAAAIIuBMgiHWnwroSJ3D8 y8072iAWt52lTo48sICS4qSnSFlOUXlnaDUrAtXVPn8Q2iTlOiccLWOhj9ys/pmJ60FSlVo7gjS7I q9uurdv/ZprUxsTo9bJDKm3B0 aK1SrM1VXT/7LGmBQsxee4F6yV3iYqXH xZHMmqgzT9ppomFv62Oz5UwLEKAAR5Euga/NfGbGrCrLOZ2utz4Biox0RLppSkrKlMp30X3/ 1D35TTDvi3ZORLWFhlhxt7mW7xob/5dPfo5qpw5T/mW8lHZ60yy7eg2BLH5gfgZAQQQQAABBBBAAAEEEEAAAQS8FSCI9VaM7f1PIOsXzfhsg9Kj ujaEecKO8MV7py0NUHxjmkDqrs2I1mnT5twMM8SoUjnXKtJJmttr45t8n18rh8r9VT/ju9pw9plWnJykIYHrdSiuHTZ2vRVP8fUqO4Wj rvbkcP1vlSHw KlZlIwFuf7Llh9 nQod/NEWrlOcoxsy7dsdbMH5tvsK9HtSnURvEJzpeI5cnaT8c71yk8vGAwXKiDsTMCCCCAAAIIIIAAAggggAACCJRVAeaILatnvhS1 /SimZpz0KZGV49S94JDRXNaGqEGDRwTwR7Tnt2JeVufuVs7d cHCVOLFnXMyhOKW2VeAJb/43P HKW 0ZcoKGuLYhaf0Okly7Q2I0AdBvSSm2lonaV4Vv9zHvACH3hfnwsUmPOx9z712rR0jjLds2GLicNdl2StX7fLrAhXmzb1PTt8UW61d7d2ZeQtMHn3PjleLRbVoK4qFeWxKAsBBBBAAAEEEEAAAQQQQAABBMqsAEFsmT31paTh9n368pM4pUR01bVX1T/vaMrWl/U0s7hmaNXMb7TLMc pc7Hr2ILZWphnftjsTxoNHao2ZsLUfVp lnd8jZL11HN8zTnDWub XK/iiqT191CbFrY8z3mhWzUZlBbdX/0nM83O5F/XMO7PUvXtXHi9K99Qlof5mizajgjDVfa9rms6/kSt3 laavNG8Aq9Jbg7tkz1DrRTUKv mp5Zox79jZsD3tV82aGadUmRC7b vCl08JCCCAAAIIIIAAAggggAACCCCAgBFgagK6QYkWSFr2pWabFz3VGTtKlxaY zVv0wLaXKM7BsRq8oIZevD2X9S7a0NFnnKMXD2mirWDlXQgH0WNIZo4YbMefCFW7955t5b16qp2dcrJnvC7dq5fr/X74tXq9s4a3jnffiYU7t89VLFLZ lTW6aCu/VVnwKTkGbv4039fT5RXtTHq2N46xPYXNfdM1Cxj/2gLx5 UHsu66x6AYcUt/gn/ZpVRQPuHqdLCpnDZmz5Vq/MyRnefGSrid3NsvU7vTBlTXbTmg7SA6Oa5wnsbbUq6td//1X3ruutSyqnaO alVq5J12Vet u8Z3z3iJ9Kd8rUzZGAAEEEEAAAQQQQAABBBBAAIFSK0AQW2pPbVlo2CHNnrZcCSHtdds1Tc87GjZbI0q9H3xKT9aZqqnfr1fM7K2KrNNS0Q9NUuu4hzQ5fxBrSqw1cILeqB jGZ8v0oqNS/XV8nQFRVVS9TqtNOKWbop2O9I1VD0HdFX4kqVKtgerR3R3Rbo9Hd7W320hHqz0tD4eFJVnE 99KnS7Ta9MqaP/Tf1Bq36cp/VmrtmazS7Tn66/Tld3Otcb0TyvV9bBTZo/b3XeHQ5vNutyViW00/0miHV9NZutxVg9e sevf7hYs1ekqjASnXV 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 ggUgAAC3gnYVLFBS1X0bie2LmUC5VoM1f zdx/wUZT5H8e/Sxot9N4JCAQCSBcCCKE3DyyHBc9 nl2x11NRz4Kn3ome97cg2EEFPFpCr6EJoRMIXXoPBEIS9v9sSNlUdjZts/nM6xUxszPP/J7388xs9rfPPPPU4IEKa1ZRqYNfE/dO0ej7v9W2mTO05K/t1L cm5X2baYRTzdL2Xml3prjSMQ20XVPP3TlUfPHT qE2TOgamWSsG7ysxsCCCCAAAIIIIAAAgi4J0Ai1j039vJUAf/qCn3oYY1Y 7R 3DhFv64foAfbON//el675vysiVMjtWH3ccXZy6haoxYKHXajbh0QpGzvYnWprkf108MP6YvopvrbN29pRI3MO/2hCfc rm//CNHj3/9dg9IyVBbiOTFLo0d oU1dHtJvb/SSv9Mhtnz2oB6ffE5D3vlaj7bPfOwr/b5d/7n1Bf2qofrXd3eoeY6b79X4u5/U96f76t3J96ut7Zx2zI9QxNK1ioo aOZZPKOLPuVVo3Gwug0aoZGZPZ3in3SPNPGzaVq85ZDO2ioqqMtgPfjIMLVIa4ALmvn87fpwtXMwkXqj301OK1rq0cmvacjlIXE5Rp39C 6Wb6G9sj wC2vPKWbuNE2asUobdh7WqQQ/Va5ZX61Ce2vE9b3VopLzKG8L8RSC/ 4Jo3X/xH1OdcxljlhL8Zgi3er/dp3eOlff/zBXkRv36eg5u8pWraeQHoM0alQvNXE3CZhcw4Ls/1auJ7dqz4MFff5aiSf9 tZs0EilpkpTO4VvgxCFmDmDtx05q7NxZm2e2sCF0yl1k9T 47xL NsaEJ6 wv05Yt3zkdw7f/P3 u8EknhUK777Rt ER2n3iUSVqxOssFF3qWWOzBbiz7GM/HjBc/0P/PCs7vpip7q/8IOeqDNfX341Q8sd73um49cIaqObRz ifvXzYlAQ7xfr9cHwMZrV/Dr9rcI6fbvssPyCeuqh5wfrzPgP9NWyo/Jv0El3vvig tVN fvqwBQ9cMe32t3rcY0P26dPx8/Tun1n5VO5vq7ue4PuHdVZtZ1HqFu6nrv7fm39 l8w7eWGp6X3F3f7v4V Z/X9OrloV68P7ravhfiTN43X/qXT9d0vS7Rx71GdiLOpXKVqqh/cWmE3/lmDW6S GbkTj8W/B1JCd62/uROPRRtL56Mp2 r5bjEcd8t3zTM1GFf7p7v19ZTrTyFcH6y2L9sjgECyAIlYOoL3CZRqpB6htfTjD4e0evUeqU1QSh0TFT3xNT01IUaJVZqq58CuqmE7oQ2Ll rnsev0 x v6KO7W8i9qWWrq/ Qtvp62zrNDt vEaPqZXC1b5uvOSaU0mb 2l5pSdiCjMdKswYppFWAfl2wXVvNMLHmOT1Y6dwObdsv XRpoebJucB9mv3ptwr3a6o2Ldqqda1KCog/pZ1rV2rS2DVauf8V/fueFhkSxslRHV oN5/cpVPBHdW9bxPtX71ca dN0IsJVfT1K6EpyXA/XT3yET3T17FDrFaMH6 Fh5po HODnRI7ldTC7fua3Sm/ENrLflwL3/m73p17WKp2lbr1Gqi6gdKZgzu0 pdPFd wh17tk/pp1s14CtC/evfb9Ezdc6bNkrRx0ieaEZPc4rkvLsWTexHZv2rX4bkf6sl3l lEYGN16dZHPQIv6URMlJZMHqfVa/brnX NUku3n81UkP3fyvUkSGsK/Py1Ek/2rZG69szquVpyxPzxcVVnda6e 7b5 mr5NrrtuUeUPKva0RX6/IuVim09TE8MaZR2mOotc5rL4EqRuOPj5vl7pVDcfv2Mlrz7kt6Yf0LlGnfWgF515HNss a987qW17g8F3vGoj0pfs/3v7Rrip5//ycdqNFCrTvXl 30YW3fslIbD8n9RGxBv1 sjdCca/uq/zVR t iCL3/SKTK1e k/gMra9Fvi/ThJyHq mbvDF9g26N/1LNL4lShe6iu63RJB9Ys1ZLvxmrz/sf1ycvdVNmt/unO 3Xerv8F0l6WPK28v7jT/91qCBf/fnOUbeX64E77Wo//8Iz39MgHUUqsHqzuvTqoVtkknTr8h6LXhmtqgz5OiVh34rHSXlljz72/uRNP1mMUxJqCOd/TI3W3/Nw9rfZPd LxpOtPIV4fCqKTUSYCXixAItaLG7ckV61BA0ci9JAO7NqnBAUp eP1kXB98k2M4gM76blPn1bvKikjC0d11dv3vaP5P3yuKf3HamTGHKrLjJV69VHXT9dpcfh87bjtdjVNG7h4SevDF mw bgycHAXlUktsYDjcTlwc9Nwq5Cm0oJobd2SpD FZv8EHfvW7Yq2S01CWuhy7qquho4Zp3ua1VBp50Gal67XT489oS8mT9K8G17WwMz3pIkd9jYzVuaI3L3wSd76b37nhLc5bO17KzoeqfPCrWR7Wv7pkyrcRRHfvZkYitrpA Pa9827FLFXej/EJor2MzP9X7JgnrG3KrPnx7hBo7fSuQdGKD1p8qlV47d MpQP9yQR3UJ/l7jwQlzXcxEetSPC41asaNjkZo7D XKbbZjfrwHTMyMy1pn6Rbpryhh8dN0ydTwvTxzXXcKNyxS0H2f8n160nhnL ux5MTp10nVn6lF16foyPVOuupl66Tm5fanA6Q 3r/OurQJ6Wtdx/SdyYRG1e7lfr06ZD7fi6 atnH3fPXxXisbpa0frLGmSRsqWYj9cFHN6pB8l Hdt3U/h3d996arMV5WPye7r/ml9kKvv0fmjgyKG06jKSTO7UnMSutq2sK/P2iVn898eIoNdVWJYx8WdNONNJfxzygQYEXVP/AX/TB5m3art5q5xSw/cBJ1X3iQ70xuKqS/yy4e4gmjX5Cny/6Ut s66JHrs7 74vc6 zG 3Uer/8F0V6y5Gnt/cVy/88dPOdXXX2/tnR9cKN9c44wh1eOauH0KMXZgvXwx69rmPOAg8QzOnjS R4zd Kx1l6Zg8y9v7kTT YjFMzvBXO p8fqbvm5e5ryLfVPN LxsOtPoV0fCqabUSoCXivg9Knea tIxUqgQED5sslJPvvZc YWwMvL8aWR2mIG9tQeOEK9UpOwjpcqdNQtQxuYjfdo0eKD7muV6aRBvc198gcXafYGp4nTE6IUPv kVKOnBnZMH3FV4PFYqEnlkOYm6ZmgrVvNsN3k5YCmvfqsHn7xN 1OWbPfJGLPmvEsrUIuPwpHClTD5qlJ2CTFn4vVqZOndPJUGTVrZeZmSDQjbLMbEVmlp24ekpKEdZRdpp26dzB/BF/ar71mxK2nLgXfXocUMS3K3DxXRyMe/lOGJKzDxKdKa7ULSv8Q63Y8nuZfQPHsnjlL6y WUdfrB6hmQqxOn079iVNgaDe1tNm1fdV6nXa7wxVw/7dwPSmU89dCPNmRnl71uZ76 0ztq9pdL3wwWn3ruJOQya5kD1ln0cft87eAqrt5caSZN9dXnYYPSknCOg5kU7W 1yksm7skPC1 ebh/YsPBeswpCevQ9akcpCC3R4UXwvtFzRqqldzfqqm6I87yNVXb3KFh7u0xv5tvts6auZYvJm QvlQM1Y39U5KwjrXmoXpDh3c0dxqd1qKFmzNtXHC/5vX6n//tZepqydPi 4vF/u 2vIvv1x53fTB36SQl/1nuI9/Mbz2 FVS7utu3xqRQWmyvTA1QIP3N7Ua2sGNBn 9uln8lT7f7p4vxeNz1p7CuDxa6DpsigABTE9AHvFYgZYim3QzhTFn2Jmf5bAq6qvHlkRpOdW/YtJH5CLpXe/c4tnH38V4 aj 4l2rOmKr5s9bqr206Jo/EPb9svpbESg2H91Gw08jRgo/HQuMGBSvEfK6KMMnWM2YEcYVjazV36U4z2uWSVh4YpkZ14k2S1sz96ddZIU6TPl7YrPnX2wAAIABJREFUt1w/jP f5q2J0eFzWZ/aGWfm5HSYZ1jq1VP9TKsqVargkFLceQsxF/KmBd5eiTHattNUKrCl2jW58ndkbsfjaf4FEs Fy/3VcM5/6z7Nz6mvnLj80Ca3phk2ZRZs/7dwPSmU89dCPJm9L23WhLHh sO/rZ5471H1rJHpApB5 2L5uzUft8/fArE5Z977zJeFqqnGQZkm7S3VWE0bm5ccTzdzWjwrfkdgnu3foGtH8xVbPi6F8X7h73f5biLzX3/HgMEA/7Spm/yTV1zUxXjzj/NgwoaNFJTpXrsyQQ1Nz4o0fWyfmRqkdSE8xDHv1/98by9H01v0tPb Yq3/u90TXXy/9rzrQ01d06OxJsZs1KcPv6bNvdqrTcumataiqRpWdndKmoyK1tor474F0t/cbmQLOxb0 e5m VfydLt/uhSPJ15/Cun6YKHrsCkCCJCIpQ94qUC8GQnruOPPFlg bf6y8 cvmDWlVaFCNjNyVKggRyrwxPnz5ntzx0c69xZb8z4aGDRNXy ar UPd1TPsue0KHy1LtiaadBAM rWaSmMeFyuha25WrW0KWLzdm2zD1Dw6ihF1 morn5rzDy7p/Xn6/4wiS0znLh5sFql/M1qPzhHf3/kM61LqK72A2/WLS1rqUqF0sl2xxZ8rg/CD5sRCGafzJplSqdPz5AWoCMxY5K26Xlzl0MvrA0LvL3i4pSct65SWdkMQMtSTbfj8TT/AonHWCYPha rIS/crR45ZVoDUkd8ZeG94orC6P8uX08K6fx1OZ7MeoeitdmRyGvfRT28Mgl7ucJWfNw fzPb5svvF2Te sxSXoHJIx6dlzIKrJD1HdGz4r8cryf716zp9tDXzA1y ffCeL w2VK Ri2lUo63aKfvT2zmNXMbiy453uKdF/M3l NvqQxLhcDL68w3rY5ulnm2osyb5/33vF//8729HJWy4OnO 4uV/u 2sYvv1553fbCp8a0v6/0Kk/X9zBVa OMEhSePEwhQ9bZ99OCTf1G3Wlmvc646udNezmUXSH9zNfi8bFfQ57ub5V/J0 3 6VI8nnn9KZTrQ176EvsiUAIFsslIlUAFqux1Ape/7TRjWxvVTxnRYe6AN39AmnvpdOaMI0WbqeufOWMeCWUGLJQpkzltaNGmtgYMbqmJH6/R7IVn1LPLcoWvTpBfxz7qa 7Wd14sx5P6IciM8s2crzx/ VO0xVgzRKNWrUyieLWZTmBPgi6s2axKnV7QSP 9esokZc93PqWt5ik3tQc0T3vYxtZpv2jduQB1fuotjRmQ8aNVVKQj6e1di X2slr9smVVztHGx0/quPnnSg/SLvB4rMZf0Ntb6v/GMnmu4TgF1Gijdq3yP7jC6f uXk/KFNL562o8mbwvmpFzjlWlA1Lml87/9vCMEl33sXz Wur/VjXKqEzyHMpnFet4I8zwXnXevGdmvdvBcvxWQ3Jre8/19/XN5z 3PfX9Itb8jWXaLsN3X2dik9eZP8LSz/8C7c95v/7ne3tZ7M/uvb 43v8thmN5c4 8PtgCFTzsLr1ufpLijmvXxrVaOPVX/bJyht58u7q /HCoGbnt3uJee6Ufq6j7W9qXLFY/X7h6vrvHap7V6 L1JFP5V/J0u3 6FI nXn885/rgbndgPwS8TeDK9796W42pj/cLXNqtxUvNo4hNyrBTp4Zp9b38AC 7du7YnSWRucesSzBbNmiY98fHVO3bV50DkrRm9mKtj5ivjZdKK3RQNzOjasbFcjwmkZw8i9XpM5nmtTyjfXtTZ8J1v3kbmIdwVdBBbd28Rmt 91Gnzs3Vokt7lVu3Tqs2bNcuc1NiSEijlAOYJ4IePmb v7Zat848vuWgNm1yf bNrDUwo3GSByqkzvGVdYu8rXGtfMvtZTUo3yZq7njQ1dlNWheTeZhR1sIKPJ60Q7rmkzXCfF5jqf XVvPmdU0AJ7V65a4s53veIyu8/u/y9aSQzl9X48lgXDtMz38wRu/fc3Uev jKe8sVdAmu lg fy31f6u1LKuGDR3j8I9r965zGXdO2qWYXVnLsxx/1iIKZE3x9HeDwlPfL/bs0s5MDyA7v2uveVipmXXH/H1VObWqbvdnV96PCvr670Z7WdrF/fcXV/u/pXDc2Nj964Mr7etGQJl28SlbVU0799U9bzyjG82f/YmbN2tLtg/OcyUe99vLek1cicd6qXL3fHT1fHcjpORdCqh8t/unS/EU7vWnXDnHI6AvKt4xTcwVFk 5PlwhTF5GoMQIkIgtMU1dQip68aiWjftYv5rpTANC/qQRbdJvNara7RoFmx5/cNbPmnMkfYSP/Xikvpm 19yi1FA9e7g7P6yTb7kuGnxtoOybpuofv5inVVXspgFdsz4IwHI8peuqgePuxh0rteRQ pjYs t/1rQN dC wS3Uyseubb/9ojXxbdS5rY9sIe3U0RalH3/ZriQzvUKrVqmeNtWp4xg2dVDr1zvmFkxdknRo5nj9nN1DutwOMVCVKjmGz5iHee3JPBbY7UKddnStfMvtZTm0Wuo3tI2Zbu gfv14qnZl qPKfnqL1u9O77cFH09qBVzzsVxdqztY7P NBw5MnkZj769fatLOzH hJujY nBNX MY/ufOUoj938XriQrr/HU1HmfWM4e1LTpG2/eeSv7Cy6sXF30sn78W 79V45bXdjWPZErUyl/ p/TTxa7jc6dpXqb5YR1lW47fOaBzUZr45gd6y/z8vDHraFursWfYvpj6W6 zh75fnF6myeHH07/8urhfU35ZbR5CGagePVqmV9Pt/uza 1HBXv tt5a1PfLw/uJi/7cWj/Wt3b8 uNa 1iM6qei1exWb Tvus4d0wDFcu6yZPiPbmQlciScP7WW5Iq7EY7lQc7eKm58vXD3f3QgpeZcCKt/t/uliPIV5/alVt7ZKmUlftm7ae VBB 5cH7b/qL/dcLduuuEJjd/qbkOyHwIIZCeQz/dKZXcI1iFQsALRM/6rj8zt/3EnD2vHpmjtj01SQMMwPfvC4IyP3arZTw MWqinJ6zW w8 p XdQlSz1DFtXL5S0Sf81PiWezU87wNiTWX91GlwT1ULn65j5gNsjet7q112Z5rleJqqb796mvJdtP776PPaEnqVyp/drdUr4lT/6sravy5zssmie0CwzLMLtHzbLsV1Hqh2AY79Q9S5wwXNXWz Um3YW62chvVeNXioWk/9Qqs elZPRoWqtZlf6/SONVqwOkmtO9XWilUHLQaQ0 b an9Na/lFrtfkMe/qfP8Q1Qn0M394VFFI/45q6PygkJyKyHW9i Vbbq9cD5rti9WGPKDRUa/ovQXf6eE7Vqlbt2DVNbfYnz28U2siN6nho9 qTaOUTwuFEM/lIF30ORGt asPpCTaErXpqGPv09q6cIFKpz7/p2ZL9W baY6ObCWyW2mx/9ccoKdHb9JTYyP1xUOPaGm3TmptMO1njygmKkpRe2MV/EAHDemQ3bGuvK7w r L15NCO39djMeZ8ECkxn86S2fa3ad 3RukTRdzZeVctkiM1q8fROjydz7HtDX5O5oYTXtvnFYk71ZfAx69Tq2Tr2OFubjoY/n8tdj/LVa5VKsb9GCfSI2ZO1lPPbBDoZ0aqdzpzVqw8Lgq1fFT3IFMBVqO32n/ INau2CZNplVF695WDeEZJsBsViD1M2Lp787lfXE9wtb7Ura/ 9n9di6ULWtckF71qzQit0Jqhz6gEZ1cP5DyN3 7OL7UQFf/91pLyv7uP/ 4mL/txKMO9u6fX1wsX0tx3RAs954VeF QWrXprHq1qok/wtHtGlJpDaeCVDzuwaprdMcyOnFuxaP1ltSKuxWO1VMm989H18916RI49Cqx8N/uny/EU4vWnTI9BGvD5as387i09c8x8FqsWYGaaqKbON4WpuWOwbIbFjetDYrxik6eXMenebEeNZz4GvyOAgKsC2aWHXN2X7RDwCIGDayJ0yMdPZcpXVM0mXXR9aJiGD2qrmlk gPup e2v6sNak/XNtEhtmDfTfGAvraoN2 uGu27SrQOD0p4InNeKlWrVU71rT9ekg7XVb0AL52dcOBVtNR6bmt7 rJ4//7kmzNuiZRGHVb1pO1035g6FRD6vNXlNxKqqmXqgqrTtuFp1bqfLuTN/dewSolKLf1f5kOAM85ba6gzUqx/46 vPZyhyRbgmJ5ZRravaadQ7o9Rl81smEZtXxfT9qw5 WK eHK9vIjZq oQ1ik90ZF1a6tEe ZGINaO7XCrfanu5UX9bNfV 4V3V6/ybJs9cqfWmjy5L8FelmnXVcthfdX2GD7KFEE9KFVzy2b1A/34vQhlvbD6ouZ M09xUih6P5yERa7X/21S772h90mCBJv9kHp63YYmmLkuQb2Bl1agbrKH3dFZYz8zTarjeZoXZ/127nhTe etaPK5burXlpUP6PXyBVmbY ajWm3WXl9Zq9UBRJGIl13ysnr9W 79V1UCFPvWGXq87URNnR2nBtC0qV7eFwp55RS1XP6MxmROxJp3u9vvpuXMp14nKqlkj//8MLZ7 VtvLbO B7xe25iP19n27NW7CQk1bfE4 lesp9Jbrdd/t15i/MJwX9/uzS 9H5q ugrz u9FalnbJy/uLa/3fUjhubOz 9cG19rUaUj2F3TFCias2acumVdqw5Lxs5c31p0E33fnQcA0PrZfjtDmuxJOX9rJaE1fisVqm40l87ny cP18tx6RY4 CK9 9/ul6PIV4/Qloo/vf/Jvs437Vkjm/aX2C4/NRC1Ucml0i1tW/T9xrL/ZCAAFrAraJA5KfG8mCQL4KtH4763PfB/S7KfkYsyMm5euxPLKwU/P03C2fal3QbRo/brhqeWSQBIUAAsVCwNOuJ54Wj6c1Ij65tsjp/43RyI/Wy /qe/XVewPM2J18XvDPZ1AXijswRQ/c8a1293pSM1 8xoUd2KTABOj/BUZLwSkCBX2 F3T5VhvS0 KxGr/z9l5wfcgtn5D6mqtEYzt85uqmbIdAvgswR2y k1IgAkmKnjxNaxN91WFob5KwdAgEEMiDgKddTzwtnjzQFsiu OTOmqB1a7eauexqaNjdffM/CWse6sj7b 4twKveLED/9 bWpW4I5E2A60Pe/NgbgfwVyP97wvI3PkpDoPgInNis/4Vv0dE/1ml2 B y1RqkW/pULD7xEykCCHiOgKddTzwtHs9pqcuR4ONai9i3ae26iypzzZ81Mjgf54bF3zV/tvJOAfq/d7YrtUIgPwS4PuSHImUgkO8CJGLznZQCS6zAsbX68YspOupXXnXbDNIDj9 ukDw/SKrEalJxBEq2gKddTzwtHk/rHfi41iK2ED3 8yQ97trWrm Fv tWbOl9AvR/72tTaoRAfglwfcgvScpBIF8FmCM2XzkpLFWgxM8RS1dAAAEEEEAAAQQQQAABBBBAAIF8EWCO2HxhpBAPEGCOWA9oBEJAAAEEEEAAAQQQQAABBBBAAAEEEEAAAe8WIBHr3e1L7RBAAAEEEEAAAQQQQAABBBBAAAEEEEDAAwRIxHpAIxACAggggAACCCCAAAIIIIAAAggggAACCHi3AIlY725faocAAggggAACCCCAAAIIIIAAAggggAACHiBAItYDGoEQEEAAAQQQQAABBBBAAAEEEEAAAQQQQMC7BUjEenf7UjsEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8AABErEe0AiEgAACCCCAAAIIIIAAAggggAACCCCAAALeLUAi1rvbl9ohgAACCCCAAAIIIIAAAggggAACCCCAgAcIkIj1gEYgBAQQQAABBBBAAAEEEEAAAQQQQAABBBDwbgESsd7dvtQOAQQQQAABBBBAAAEEEEAAAQQQQAABBDxAgESsBzQCISCAAAIIIIAAAggggAACCCCAAAIIIICAdwuQiPXu9qV2CCCAAAIIIIAAAggggAACCCCAAAIIIOABAiRiPaARCAEBBBBAAAEEEEAAAQQQQAABBBBAAAEEvFuARKx3ty 1QwABBBBAAAEEEEAAAQQQQAABBBBAAAEPECAR6wGNQAgIIIAAAggggAACCCCAAAIIIIAAAggg4N0CJGK9u32pHQIIIIAAAggggAACCCCAAAIIIIAAAgh4gACJWA9oBEJAAAEEEEAAAQQQQAABBBBAAAEEEEAAAe8WIBHr3e1L7RBAAAEEEEAAAQQQQAABBBBAAAEEEEDAAwRIxHpAIxACAggggAACCCCAAAIIIIAAAggggAACCHi3AIlY725faocAAggggAACCCCAAAIIIIAAAggggAACHiBAItYDGoEQEEAAAQQQQAABBBBAAAEEEEAAAQQQQMC7BUjEenf7UjsEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8AABErEe0AiEgAACCCCAAAIIIIAAAggggAACCCCAAALeLUAi1rvbl9ohgAACCCCAAAIIIIAAAggggAACCCCAgAcIkIj1gEYgBAQQQAABBBBAAAEEEEAAAQQQQAABBBDwbgESsd7dvtQOAQQQQAABBBBAAAEEEEAAAQQQQAABBDxAgESsBzQCISCAAAIIIIAAAggggAACCCCAAAIIIICAdwuQiPXu9qV2CCCAAAIIIIAAAggggAACCCCAAAIIIOABAiRiPaARCKE4CCQo/KWbNKDfy5p2oiDiLejyCyJmyixSgaPT9Vg/0yf/vkhJRRpI0R98xXujzLn5mCbuLqpYiv/5m3R4rSaOeV53jvyLhjj6lfl5OfxCPoFe2efYLy8nHzP95159ujGfDn FYoq /1whQK97 cr9weuqTIUQQAABBBBAAAEEEEgR8EUCgeInsFEf3fCaZsSF6tUZj6urLacarNc/h4/R7MSeGvPbI qc43Y57e/u qP68cEH9eX2a/RSxJPq4W4xxWQ/ 5mdCv9pmiKWb9auw2d0oVR51WraSt36DdGNA5qpYsrXPav/eYdenBmXXiubr0oHVlKdJi3VbfCfdGOvBirjVOeNn9yvJ389oTYP/5/e 1OlDBrnw/ h4e/9rgpDX9akx9okv5a6zukAKuVXWhVr1Fdw5x664eb CqmSH989laz2td4N8bFuVtR7HNGUt97TN1vKqmW//upXr7x8zfWyzlV hRZYYPvhenz0qeTjHVgwUT/9XmiH5kB5EihB5/v5A4qcPkvhS6K0eddRxdrLqnrtRuo45EbdNqSFKvvkCZKdEUAAAQQQQAABBEqIAInYEtLQ3lXNuqpf39Ro0xEdOmb rZ5D7WKP6PA581qTOqqf5ySsrzrfN0bv31xWdSrkcLw8rS7o8vMUXI47J yJ0OvP/J9WnrCpQsNWat rpsolndG zVGa9M/fFVt9oh7vmHH3Gm3D1KmcSadEEnDu7UhnWL9M3a5Vqy7UV9eH rDMnYHA cywu 9dtrQNuqZgu7EuJidXjHRkXoUil0TrlU8fVdeKuezMSwi4JVA8z9 0qp5dr5WbE2TrcLPefLqvyrplkNtOV/YJaNRBgxpdLmPjrp9MIrakj/POzbO4v3bl/uCJNfz9sxf19 nxqhzUUm16Bsv/3AGtXxml3/5tzp Y5/WfJ9oVwLnjiRLEhAACCCCAAAIIIJAXARKxedFj3yISqGwSsSZV4EjEHjYh5JSIPXxUjpf96tdVzTxHalOlhi2UcVxmngt1KqCgy8/PWFPKurhdX732uUnCllOH 1/WSzcGOX0IjdeB5TO1OZukZ6P d nR/qVTCrHr7PqJGv3sb9r981eaNnSsRtbNW6wBIYP06GNXOxUSq/mvP6a3Fy/W97NHquuf894b8hYhe3ufQDE8f50b4fhJOWZcCahauYASScXcx/s6bBHXqHj2h/LNB qpwQMV1qyiUge/Ju6dotH3f6ttM2doyV/bqX 5Iqbl8AgggAACCCCAAAIeL0Ai1uObiACzE6hfv45ZvUOHD1 UQvylw7/pkVETFK2Gumv8WN1sknn2w0d01GxVr0FdOd QfuCHZ3XXFzvV/YUf9ESd fryqxlavuWQzqqcagS10c2jH1E/x4hbs yeMFr3T9znFEILPfTjGF1XJXNUFzTz dv14Wrn9ZF6w8x5mL601KOTX9MQp Sk6 WbUk7M0uiRX2hTl4c06R5p4mfTtNgRt62igroM1oOPDFOL8pniSjquVd9P0IRZUdp9Iknl6gar31/uVvPIpzQmvKpG/d9Hur1R5rq49vvpeZM0dd8lBXS6Xc9kSMI69g9Qna7D5Wil3BebyrcZoaGtftO4qD3avDleqhuQ y6WXw1U6xDTIRZv1YkTjluf3UnEute ZsIE7ZrzsyZOjdSG3ccVZy jao1aKHTYjbp1QJAyN5flqiXvcElHlv oz76ep3V7Y2WrVFdtw4br3ttDVS8LpdV4XN3eXR LNU48qhXffaNvwh39OVHl6gQrbNRdapljMXad3jpX3/8wV5Eb9 noObvKVq2nkB6DNGpULzVJS5rs09d3j9Z3RzrrhUlP61rnOTIcZSes1ts3vaP55YbqX9/coeYpI wtnb9pMZ5TzNxpmjRjlTbsPKxTCX6qXLO WoX21ojre6tFJefh 67GnyNAzi kXk ctwh/WwPC01d0fnqixqR9aXJOO ZHKGLpWkVFH9TRE2d00ae8ajQOVrdBIzQym/7snk/OIWd9xaKP5f6T9YhFv8ZK/3H1/DW1svT 4t75bqk/WIonY/y/vdFL5q CtGXLZw/q8cnnNOSdr/Voe cWtNZ/mg0aqWaZOoBvgxAz5Y207chZnXXMvEMiNpMQvyKAAAIIIIAAAghkFiARm1mE34uFQE2TiPU3idhDB4 YeOspMTpGu5Ij36fobZeTeccOHVWiScHWr1872zpd2jVFz7//kw7UaKHWnevLdvqwtm9ZqY2HlJaIrd79Nj1T1zG/QZI2TvpEM2KyLcqs9NPVIx/RM30dr8dqxfjxWnioiYY/N9jpg1sltch0z6/r5Tsd9/hCvfnkLp0K7qjufZto/ rlWjtvgl5MqKKvXwl1Su6d04oPX9bfZx1VaXO7ft8RZg7WU9Ga9483FFnrUk4VcXF9vFaYefISzbigLv1C8zhSuJRsybknm3x882MO10xVsJ/U6jV7zEp/NW3q7nBbd9o3UdETX9NTE2KUWKWpeg7sqhq2E9qweKl HrtOv//xij66u4VJWedxiflZL7x TuVCQ3VdJ5sOrlmqxT9 qE274jXuzTDVSCveajxWtnfHx2q9z2jJuy/pjfknVK5xZw3oVUc xzZr3juva3mN7PqzXYfnfqgn312mE4GN1aVbH/UIvKQTMVFaMnmc6RP79c6/Rqll8uDs goLa6jvvl6rBcvO69o GTOx8SuXKtJcBuoM65GWhHXsZfn8tR/Xwnf rnfnmrH61a5St14DVTdQOnNwh1b/8qniG/bQq31S52W1Er9VS7N9 Ta67blHlDwr69EV vyLlYptPUxPDGmUVlj1ls5zxO7T7E /VbhfU7Vp0Vata1VSQPwp7Vy7UpPGrtHK/a/o3/e0yJAAs xjqRpWfaz2H0vBFM7GlvqPlfPXKXyX3l/cO9/d6g8uxeMOv9X k/0xzqyeqyXmzxDfqzqrc05352S/K2sRQAABBBBAAAEESqgAidgS2vDFvdo2M92AI6V22Ew/4EjE7jKJ2IQqzRTsF63o6N1SWHMdOuRI0tZQ/QbZd/M1v8xW8O3/0MSR6bfUJ53cqT2J6TrlgjqoT5Dj9wQlzc8tEeuj2lf31OWU71Ed 9mRiK2ukD49c31Yl vlO7XYjhj5PTZW44bWUHLNznfTe3e8pTlL52vZ2VD1Txlmad/6iz42SVg1Hq6xH9 mpilDhG7q8J7u/Ydj0oa8LHsUE NIftVTkyZ5SyXG75ip8E2mKL8Watcq7w8Hit8coU8/WWsKdMwRe1oHNq/Tuj9KqenAv r MHfHoLrRvkfC9ck3MYoP7KTnPn1avaukjHQc1VVv32dGV/7wuab0N1Mx1MtLO5h9Dx9X9Yc/1Dt/qmFS2Wa5a6h fepx/WflBH29vLue7prS8FbjsbS9Gz4Wq520frLGmSRsqWYj9cFHN ryaW3XTe3f0X3vrcla2tEIjf3nMsU2u1EfvmNGsqV9CZKkW6a8oYfHTdMnU8L08c2Xx23XD uuJl9/q1ULViiuTy nW/QvasX81WZsc21dH5Z8MUhbrJ6/x2Z qvdNEtY35FZ9 PYINXY6dZJObND6U05fRFiMPyvAFdb411GHPilj1ncf0ncmERtXu5X69OmQw451NXTMON3TrIZKOw/avXS9fnrsCX0xeZLm3fCyBjrN32LVJ4cDZ7/aoo/l/pP9UYt0raX Y n8daqWS 8v7p3vbvUHl Jxo1ks9p sR7DrxMqvzJdgc3SkWmc99dJ15t2QBQEEEEAAAQQQQACBKwsUwPCzKx ULRDIs0Bt88Auk4WMM6NezyrOJF9NciO4n64L9tfRbTE6aRKnhw ZsV42s10OgyATGw7WY05JWEdMPpWDFOTpo1qq9NTNQ1KSsI6gy7RT9w4m2XZpv/buT5fdsmCpjpgRqx1GDEtLwjperdxrmMIcz7LK0xKrM6cdBVRQRed5YA9F6suP/qt/pf78uN60T8Zld/hXl1//58d64/mndcfDPyraVlu9n/ibBqcP33Q7usQ9KzXl1xnmZ6amz16mtfsuqvrVPTSwf2vVKsQr3vGlkdpictW1B45Qr9QkbDJZR90ytIHJE /RosUH3a5n2o7lu rGQSlJWMfKUjU0 IZrzEPPzmnp4vUmHX15sRqP1e3zXpHcS9i8ONLMY qrTsMHpSRhHdvbVK3vdQrLMlWImVZk5iytv1hGXa8foJoJsTp9OvUnToGh3dTSZtf2VeuV3I0dS53u6t3CZmYhWKqlsakrzb8XVmtB5AVuMaVxAAAgAElEQVTzhUYPhTV2Wm/5fw8pYlqU4s2EHSMe/lOGJKyjKJ8qrdUuKP2x65bjtxyP1R0C1bB5ahI2SfHnYnXq5CmdPFVGzVqZEzdxu7bmeMeA1WNdeXurPlb7z5UjKOwtrPUft89fF99fCq32BRSP1f6Tub6nV32up/4 U/uqdtcLH4xW3zrp527mbfkdAQQQQAABBBBAAAFngeyHCmKEgKcL NRRPcfwU/O0rkOK0fbtdgWNbKG2/mbE2pfmd/vVZrSsSUHVMInYHAZsNuja0YU5TD0Qol491XcekWZCrFSpgvnvecWdT403Trt2HTe/1NRVVzlec1pKNVRQI/O742W3F3tagi9DKCejNfd/ETqWWm6LWrp1ZJsMc6EeiZqn6VHpB/at3l5/e220RlyVQ0NZjLHcoBf1y2jHw7rsuhh7QgejV vHTyfo46dXK a1sXq8S FM4rc3OStuU9BVjS PVHWqR8OmjUxKca/27nFsk/3UGS5Xu55pT cJEc2OAU0amRHji7XDlH9EHZNnxbUaj9XtXY7XrQ3PGauTZs aahyUqf1KNVZTR4LU8bSptOWCtm69PLfz/Lfu0/ycjnni8kOqLn XUE29zUj6L7Zu0IIlseo3yMwZYJa4ZUu1ysx2clVYj7yNeEuM0badpsDAlmrX5ErfCLgTf06VzL/1F/Yt1w/j/6d5a2J0 FxSloLjzBy8jj5f8ItVH6v9x/0aHIv8WT uSp7wIW0pf/VQ3dHDnbmpnQqx1H sn 9pR3Lp/cV9H8t7Fkg8VvtPpqgvbdaEseH6w7 tnnjvUfWsURh93rIcOyCAAAIIIIAAAgh4qACJWA9tGMK6kkBtM WASWZEHtWh/TGKjq2gVsG1VNW/mapfWKPoPUdNItaU0apujsmTmjU9fehrDgZlSpvRjpkXxwdBkwRJHf5okrLnHQ8OMSnQwEx5WDOE1qzL6 gdMxLWUe7xszpzxvybOio2 C/6NuIvZs7J6Xrs1vHamjlM83vqA4Ds8bHa /t0/fu9n/Wf5z9QhU eVR nD7S2yxPHZlOC86rcPgDb5B9YVQ07DNDTr8Rq5z0/atb/TdeILn82j3Qr OX8eTOKUqVVoUI2l9kKFcxYYpM7PH/ezD5sRkPmJZwKpo0z72/WJTe7icERRfL/WozH6vaZQ8jf3y Y B0lmrpmqWx2/TlO55KHYtfVkBfuVg/nUdvOgQXUUC2n36v16qHW/9mqtQsidWZQP2N4Xsvmr9VFW1OF9Xbe0o3axZmYHOdnlcrKZgBvpgLdi9 NqFzexX5wjv7 yGdal1Bd7QferFta1lKVCqWT6xBZ/rg/DDSkpyTFeSp97sYjxWfaz2HxfDyGaz01sWadq0AxleqeYTmvdErKX Y/18TwvYpfeXbCpeUKsKJB6r/SdT5Q5Fa7Pji5/2XdSDJGxBtTzlIoAAAggggAACXiuQTYbAa tKxbxKwNc8hMvcDrv0iPYts2tPqat0o Nxxr5mnlj/37Rt9R5dMInIauahXlmTlpchfH29ufuXUZnkOTHPKtaRKM1wy/8FxcZmHc1mrXs0MHPDmiTo8YPauSvBPOvI tyutgBzq3PXm/XKE4d0z tLNe7jxer4es 0nK6fXy7tk5Jw9vdz7bi2Bi0UbBJ4u/bGaIcZ3dgwfwbf5kpWxiQQHP5nzjgmHc5UF5O9dtz97l mTN7TVmdMG5uyMlTJrHM0u8qVTZvr1Go8VrfPFSPPLzr1Z0dlM/Tn88Y4c38uq3LJ0wHHKaBGGzP3sIsBVO6q3u2 1Pq15oFnp/ppiO8KzV dIFurHuqVxwGNKmticnxvcPxk8mD0 rmG5Gb8uZaZtxe3TvtF684FqPNTb2nMAKeJYE2xUY6pGwp1sepjtf 4X5kmd32k2Xe5v3 Oe1rqP brtsK6/uQYcCG/kPqdnD39bo3UCM5f/hbHKSCr/SdTXS5e1EXHqtIB5qs2FgQQQAABBBBAAAEErAlc6f5Ia6WxNQKFKFAvefLXI1q2yDyVvvFVCnZ8IjKJ2BZNzdyPi1bIMSC2fk4TxBZonKVUKnlQWJIZIVagB8ql8LJq3NgxEewxM22D84SXZpV9t3buzmVXl14qrU7dWpv0YoJWz1 RZR5Yl4pI2ahCj9t0c7CPzi3/Qd9vSn9SWoUKl4c Xh6ZmbHEc2Z0mGMJNCM/XVrsZtoGR67InqgEp4exubRvlo1ca98GDRyPbrFr547d6QOVU8raY9aZ9LUaNMyHx7vs262Y5KxA hK/c4/ ML WNTFUS1ltNR6r26cf3TWfjBFf6beyatjQMY70uHbvOpdx46RditmVef/Sat7ccX04qdUrd2Xxz7x1 u B6hHWVr7m1uMFC0/qzOKlWptYSlf36ebCKNacS01 xbeJmpuZU3R2k9YlP gut8Xd HMrMy vmSfMH3ZMOFJbrVtnTMJKB7VpU9pMu3k5SNq 5co5vj67qHjzpUn2i1Ufq/0n 6MW6VpL/cdcWwrr qOCON/dkDaJ5 Sk6Okz6fM JxdzRvv2Zp6p3Gr/yRRP7TA9/8EYvX/P1Xn/Is2NqrILAggggAACCCCAQPEWIBFbvNuvREdfxox2rWbGAkZvO6qKwc1SZtqsrJYtq nk1u0mRRtopi/Ich9zIZgFmjlbHcNzzMOz9qTNFVAIx814iOBeoWbgYJLW/PqbYhxZv5Tl9OKZmp82iav7YVXue5MG17YpbukE/XPmfvMQovTFnpCQnGh0bamuIbf1MLeBH9X0r akzS9bs1VzOVLJMfPnartz4fF7NXue46lAgaatXZlfNUH7p83WyuTMpxkxnecpYl1r36rdrlGwucIenPWz5hxJz8jbj0fqm l7zVSaDdWzhyvxX0HxXKR nnkkPdmYcEBTJ0eam rLq/u1rdNm7LQaj9Xt06N0zecKtcrycstru5rzPVErf/mfdqb1B7uOz52meRnmh728a OBA9XKDJjeuXmpS Q0q5CTq2PlzT12T6ksLRq7r3UEd/uzYsmK0pCzYoyTdEvXtmTj5mCc FFbXUb2gb ZvE5a8fT9WuTElGktWr87vZ 4G78LgbixiU116jiGIR/U vWOuXpTlyQdmjlePztOx3xcatWtbdJ757V1094ck hWfaz2n3ysTj4VZa3/uH/ Wg23YM53q1GodF01cMw2tGOllhxKf989u/5nTduQtTSr/SdDCWcOa1u0mYt 7ykL73NZY2ANAggggAACCCCAQMkUyOXe35IJQq2LkYAZ7eq4vfeYSTW1CG6aFnhTk5T1tS8zKRvzeu73/ Ze2RPR5rbkAykftBK16ahj89PaunCBSqcm82q2VP 2Ge6TNtv4q/01reUXuV6Tx7yr8/1DVCfQzyQWqiikf0c1TH2wktvl5x526qu2Ftfr4YHL9fdZv rpB/5Qvx6NVObUNs2fc0w1g/wU63hwUF6WgBa699U7te Z8Vr6z6d1x9QQXd2smvzOH1P071HabdqlSr1aLt26WbrL9bq 6SKNj/pF3/0epkfb 5vbwa/Tvd2X6d0lUzT6rs3q1K6BmbYgVrvXrtXmowmq2PkejWyXdT7K I0z9a PVpqa2ZVw7oyO7Y3W phTSvStreseHJIP88O62L41mBUQv19ITVev/B57S8W4hqljqmjctXKvqEnxrfcq G58OAWNWsqqP/eU6Pbuyuq6td1L7fV2r5zouqeM19uqOz09QNVuOxun1aX3LRx2LfK9XqBj3YJ1Jj5k7WUw/sUGinRip32jFy9bgq1fFTXMZpOc1zvczcwKM36amxkfrioUe0tFsnta5bXvazRxQTFaWovbEKfqCDhnTIFEjZTurdJUCRpt/9YEuSX ce6p5lnmWzjxvnb7UhD2h01Ct6b8F3eviOVerWLVgmJJ09vFNrIjep4aPfqk2jlD7tbvwWXV3d/KrBQ9V66hda9dGzejIqVK1r ej0jjVasDpJrTvV1opVBzMW5YZPagFlegzSgM9Xa Z3b mZY ZY1QLM1aSaOt8Upuapc81Y9LHcf1yFKcTtrPWfQrr eMj7ndRUffvV05TvovXfR5/XltCrVP7sbq1eEaf6V1fW/nWZvvmw2H8yNPOBSI3/dJbOtLtP/bo3kGsT5BRiR FQCCCAAAIIIIAAAh4tQCLWo5uH4HIVKG8SrZWltSfrKzg4fSZYP5OIbapl2pryeq5l5Pbi7gXmQVIRyngj9EHN/WSc5qbu1 PxbBKxUtXBD vVk P1TcRGTZ wRvGJjhE6LfVoD6dEbB7Kzy3s9NfKqcvjYzSm5gRNmLVO039Yr/L1WmrA8y qycLH9OZOP/mnJoVdKzDLVgFBg/XW/zXVzJ9 U8TyLVoxZ4MS/MqrVuOuGjl4mG7o19SMy3Rlqa0/3dZNk19botlfzdJN7a8zI5yrKOyVf6p xC a MtyRS2IMWPkSpvkbisNH3WTbh14lSpm86yuxH2/a/q y8cs5VtagdVqqU2/vhpw4zD1CkqeODfPi0vtaz6eN7/9VX1Ya7K mRapDfNmaoWJv2rD9rrhLkf8QRnndXU3qiY36K2HDuo/4 frtyVnZatcV91G3qd7/ IYQeq8WI3H6vbpx3LNx2qFAxX61Bt6ve5ETZwdpQXTtqhc3RYKe YVtVz9jMZkTsSa1F3tvqP1SYMFmvzTfC3fsERTlyXIN7CyatQN1tB7Oiss25GuAerap5PKLF6i83Y/XRPWRdkOonbn/LVVU 8X3lW9zr9p8syVWm/6xLIEf1WqWVcth/1V13dwfkt2N36rrq5tb6szUK9 4K vP5 hyBXhmpxYRrWuaqdR74xSl81vmURspnLc8UktIqCN7n/zb7KP 1VL5vym9QmO62cLVRzqlIi13L5W 49rLoW6laX 4/75a7VOLp3veekPLgVkU9Pbn9Xz5z/XhHlbtCzisKo3bafrxtyhkMjntSZzItZy/3EpCDZCAAEEEEAAAQQQQOCKAraJA8KL7t7pK4bHBsVVoPXbWZ8LPqDfTcnVmR0xqbhWy0viPqOpo /RJ5s66NmpzymMp414SbtSDQQQQAABBBBAAAEEEEDAOwVyyyekvuZqzcd2 MzVTdkOgXwXYI7YfCelQAQ8R BC7DkzRUPG5dLZqz2Tw7qPXVakcS1nMai0gQQAABBBBAAAEEEEAAAQQQQMCrBZiawKubl8qVdIHo8aP12rp6uqbDVWpYs5wSju/UsllLtcOnoW67N0xmZgcWBBBAAAEEEEAAAQQQQAABBBBAAIFCECARWwjIHAKBohKo2b6n2u9dqw3zZ2pRbLxs5aqqYZshenLUjerfNI8TxBZVpTguAggggAACCCCAAAIIIIAAAgggUAwFSMQWw0YjZARcFagZepteND8sCCCAAAIIIIAAAggggAACCCCAAAJFK8AcsUXrz9ERQAABBBBAAAEEEEAAAQQQQAABBBBAoAQIkIgtAY1MFRFAAAEEEEAAAQQQQAABBBBAAAEEEECgaAVIxBatP0dHAAEEEEAAAQQQQAABBBBAAAEEEEAAgRIgQCK2BDQyVUQAAQQQQAABBBBAAAEEEEAAAQQQQACBohUgEVu0/hwdAQQQQAABBBBAAAEEEEAAAQQQQAABBEqAAInYEtDIVBEBBBBAAAEEEEAAAQQQQAABBBBAAAEEilaARGzR nN0BBBAAAEEEEAAAQQQQAABBBBAAAEEECgBAiRiS0AjU0UEEEAAAQQQQAABBBBAAAEEEEAAAQQQKFoBErFF68/REUAAAQQQQAABBBBAAAEEEEAAAQQQQKAECJCILQGNTBURQAABBBBAAAEEEEAAAQQQQAABBBBAoGgFSMQWrT9HRwABBBBAAAEEEEAAAQQQQAABBBBAAIESIEAitgQ0MlVEAAEEEEAAAQQQQAABBBBAAAEEEEAAgaIVIBFbtP4cHQEEEEAAAQQQQAABBBBAAAEEEEAAAQRKgACJ2BLQyFQRAQQQQAABBBBAAAEEEEAAAQQQQAABBIpWgERs0fpzdAQQQAABBBBAAAEEEEAAAQQQQAABBBAoAQIkYktAI1NFBBBAAAEEEEAAAQQQQAABBBBAAAEEEChaARKxRevP0RFAAAEEEEAAAQQQQAABBBBAAAEEEECgBAiQiC0BjUwVEUAAAQQQQAABBBBAAAEEEEAAAQQQQKBoBUjEFq0/R0cAAQQQQAABBBBAAAEEEEAAAQQQQACBEiBAIrYENDJVRAABBBBAAAEEEEAAAQQQQAABBBBAAIGiFSARW7T HB0BBBBAAAEEEEAAAQQQQAABBBBAAAEESoAAidgS0MhUEQEEEEAAAQQQQAABBBBAAAEEEEAAAQSKVoBEbNH6c3QEEEAAAQQQQAABBBBAAAEEEEAAAQQQKAECJGJLQCNTRQQQQAABBBBAAAEEEEAAAQQQQAABBBAoWgHfoj08R0cAAQQQQAABBBBAAAEECl/g1LBRhX/QfDxipdycfSKAoBBBBAAAEECkOAEbGFocwxEEAAAQQQQAABBBBAAAEEEEAAAQQQQKBEC5CILdHNT URQAABBBBAAAEEEEAAAQQQQAABBBBAoDAESMQWhjLHQAABBBBAAAEEEEAAAQQQQAABBBBAAIESLUAitkQ3P5VHAAEEEEAAAQQQQAABBBBAAAEEEEAAgcIQIBFbGMocAwEEEEDAawROL3hfN/S7Sdc9OVNHsq3VSc147nYN6He7Xpp9ItstWIkAAgggUDwF/J78So6HZFX69QX5V85Uh a3qoLjtZdCi2fliBoBBBBAAAEEClyARGyBE3MABBBAAAFvEqjY607d1S5A8et/0ueLzmap2rnl3 rrNRfk3 rPeqh/lSyvswIBBBBAwAsEfFsqYGA9L6gIVUAAAQQQQACBwhQgEVuY2hwLAQQQQMALBKpqyCM3qZnvWS3874/aeNGpSok79O1ni3SqVAONfHSwatu8oLpUAQEEEEAgk0CC7OcS5DOwv3x9wUEAAQQQQAABBFwX4E8H163YEgEEEECgJApcOqfdKxdr9qxNqnHnkxrRSLLVH6pHbpivR3 M0H8mD9C/b60nR871jylfaeofUp3r79PIIJ9MWnad3jpX3/8wV5Eb9 noObvKVq2nkB6DNGpULzUplxk3XvuXTtd3vyzRxr1HdSLOpnKVqql cGuF3fhnDW6RssOhCL398V41G9RHfa5ppIqZD5u5WH5HAAEEEHBNoFQ5 XToJv/ LXVp4keK35u6W4IS5qyW35 6KyD0RyUuPHeF8krLp/dwlR7aWb4Nqshmu6BLe7cpYcavujBnt ype9cMU9n76yspfIEurtoje9IViuVlBBBAAAEEECh2AiRii12TETACCCCAQMEL2HX wEYtmDVPs8JXaOvxBMmvif56T qRfdRs1L0aNO81zfhhvCIGvqT Pkv032 ilVillx66o4X8MgRp1 G5H rJd5fpRGBjdenWRz0CL lETJSWTB6n1Wv2651/jVLL0uk7HZ7xnh75IEqJ1YPVvVcH1SqbpFOH/1D02nBNbdAnPRHrY9fxdbP02YpZ qJyY3Xt10cDB3ZXh/rlkpPDLAgggAACVgRsstVuKbvRTQt6N8qpirecIunR fqYw14brYuacChl2rUgtn6FKOh/CVzy0vqvytjWU7GaOLESt0yV5FvqHXKOCxNvKt8w dnRB9ORmbZFOptv3k36mfypzarYR5CxQfsUyJNyLJ0XEEAAAQQQQKB4CZCILV7tRbQIIIAAAgUpEH9cm5bM16yZ87Ro/VFdsPupWnAnjTQjVvv1aqv65Z0OXjpEdz8QqiWvL9WXXyxTWb9vFHmunLo/drs6ls0U5NEIjf3nMsU2u1EfvjNSzdJeT9ItU97Qw Om6ZMpYfr45jopOx7VwulRirMF6 GPX9cw56lmE8/o4En/9ANU7693f2qttQsXKiJ8kZb 9LkW/zRB1Vtdo/6DwjTg2paqWZqUbEF2G8pGAAEvEPB3JEd7yr/ftfILqW5GrSbo0rY1uvDDYl1ctEHm5oiMi3234qdvV8C9/RTQdKbO70gb15pxu p9VOZmk4SNXaO4xz7UxZMp2/2wQmU/Hi3/GU/9wXFG/uptCxuTp7 yb5du8u/z7d5Xf9nebnVl3askoXHaNkl2zVpQs5HMcLmoAqIIAAAgggUBIESMSWhFamjggggAACuQgk6eT2VZpjkq z5q3TfjNlQECNFgq95Xr169dN7eqVzXFkaWCPO3R3x9/1YcS/9JaSVLrdffpb7wpZjrV75iytv1hGva8foJoJsTp9On2TwNBuavnJRq1ZtV6nTSK2YvJLSUpKviXVR76ZpxrwraDa1TMewla2ttoPutn8jDQjeTdpUYRJys6J1HdjF m7T2rq6l5hGjiot0JbVM40UjdLqKxAAAEESpCAj2xN25vkqxn9em0blSpnk/1otBImTdPFeSuU EfuI1EvRYQrYdRD8h92tS58sDZ9igEnwVLXmOkIzFM5Ls0xZaYmYR2vx/6u Fn75X9rA/l3q6X4SYcu7xV3SInhk83Pz2ZkbrD8wnrIv3cnlX4sVKX/eliJixaaUbKLlbDtZAlqJ6qKAAIIIICA9wiQiPWetqQmCCCAAALuCBz4TS8K1ibOV1VdgNenLgterRtpbKuDSItLIGPny9/nfXt9phb6jbH mnTDlSE9EFbd26Lzmy W/dp/k5xXjipE6Y1y4nYmvqmh6NNTFmoz59 DVt7tVebVo2VbMWTdWwcsZJDzIWZ1OZOiEacIf5 cu9OrQhUnNmz9a0md/rHzPm69bP/q07gnIKgPUIIIBACROoPUjlP7hZPvazSlo4VXGOBOeGw7K7Oug0bqXi590qv34D5PflWjk/uzFVslSDuuZ/7UrasScLbtLO3WZdPZWq79gmJRGbtpVd9oObdfFb8/PdeJVq1Un fc3o2/5/VrkB1 rCo09mKY8VCCCAAAIIIOD5AiRiPb NiBABBBBAoCAFStdQgxoBijlyVnvWrtWqKhVUoUJ3dQoKNONRr7zY6tZRXZO03WGvrXr1s8vexuncWUc5dTXkhbvV43KmNWvBATVUK22tTY1vfVnvV5is72eu0MIfJyjckRiwBah62z568Mm/qFut3KJLUuyeTVq1cq1Wr92j02Zf/2r1VDvLA8GyhsEaBBBAoMQIXDimpKMX5VO9vEq1aSO/k2dkP7NcCbtjXSRIUuL/5ipp8I0KGFhHF9dl3c1WOsCsjJc9NjHri2dik eWLVXWaYLwLFuZUbv1zcjYDm3l27a mTLBpHWP/5F1qoQs 7ECAQQQQAABBDxRgESsJ7YKMSGAAAIIFJ5AlW567pt2GrVmiWbPnKuIX7/Uoklfq2JQO/Xq11N9wzqqmeNhLW4vZVUueW7ZODPlQRu1a ViQbZABQ 7S6 bn6S449q1ca0WTv1Vv6ycoTffrq4vPxyqmpmKSjy1SyvmLdKcOYu1cvtpJfoGqkmX/nrosTCFdaqv8ub2WBYEEEAAgRSBk5GKuydKF9p1VYCZnsB/2F/kN I22XdHmakJluriwjVKOpFNAtUZcN88xUcNV9lB/eW7IeuYWPuFeLO1eXhioONjV6ayKgQmT31jj7uQtUkqNpRfLzNXbO9u5lmR5hu8xFglrZ6r858s1EXzgEe7yeBmno48ayGsQQABBBBAAAFPEyAR62ktQjwIIIAAAoUvYCujeh376R7zc eZPVoxx8wXO3ORfvtstab XznVNx/S 5gP6f2vba6qlt85S6t5c3Pb6ao/tHrlLv21lXloi8Ua pStqqad 6ppp6tU6u6n9MPmzdqSaBKxjliSTit68QLNjlikhWv2KtY8dbt8/bYadF8fDezfUU0rWQ7YYnRsjgACCBRjAft5Xfp9ns47fgIbmDlZrzVzxoYq4O72CrgzTklRK5RgvuC6uGS7LmWbkz2jhN9WyP5SdwV0i8wCcWmv4ylczeXTpKG0KCbD6z5BDZPfD5L2ObYxi09F XQzc8KGmQRsu3qy ZjpCfZvUPxX5kFdc383l/tsA8hyTFYggAACCCCAgOcK8OnMc9uGyBBAAAEEikDAp0JDdbv LvMzSse3rlKEGSU7e8FcjV9jPgw3 lh3NrEeVOOBA9Xqxy 0yYy2nXTtS/pzkONW1dQlQcfWz9eKhK4a0iEwZeVJRa NVe22DRToPIr17CEdOGM2KRuoCqkzExyerw/e/Fa7SldX675/Ng/lClP3VlXlfATrEbMHAgggUAIFYvcqYepE8/O9SjXrKP/ ZpRsz17mQYwtpb1P6sLO7E3sK2fr4mGTvO3bOcsDuy6tWKnEe5vLt9 f5P /j3TxaPKTGKUqnVV6YH0zHHavLi5LmR 2Rk VfWakfC4cVeL8n3UxfJESthzPUmb2UbAWAQQQQAABBIqDAInY4tBKxIgAAgggUAQCfqraoptudvw8cFTrF5kHsVRwM4yaA/T06E16amykvnjoES3t1kmt65aX/ewRxURFKWpvrIIf6GASsanlH9CsN15VuF Q2rVprLq1Ksn/whFtWhKpjWcC1PyuQWqbOqy2bFNd98TLurpXa9Uua3WsrZv1YTcEEEDAqwUSdSk6UhccP59Xk29oW8nxJVhOi32n4qfHmFG0TbLe8XDETCfwQ3eVv7W9yn7wuvxWbNalS1Xl26WjfConKGnSeF1MGRCruBjFf/y2Ehdt0qXzrj4xLKegWI8AAggggAACnihAItYTW4WYEEAAAQQ8S8CMNm3Tv38eYrKpdt/R qTBAk3 ab6Wb1iiqcsS5BtYWTXqBmvoPZ0V1rOSU/n1FHbHCCWu2qQtm1Zpw5LzspWvrJoNuunOh4ZreGi99AeJVQrRoMF5CI1dEUAAAQRyFjAP9EqcOzfn11NeuRQxWwm3PSi/LLcjJCrp 7d09twHB28AABbSSURBVPBwlR7SWb69 ptk7QVd2rNO8RN/0YWI3ekjXk9v1sXZVzwUGyCAAAIIIIBAMRawTRyQ/BxmFgTyVaD121WylDeg303J62ZHTMryGisQQAABBBBAAAEEEChMgVPDRhXm4fL9WJVybfy6RABBBAwFMFcssnpL7mauxjO3zm6qZsh0C C/D85HwnpUAEEEAAAQQQQAABBBBAAAEEEEAAAQQQQCCjAIlYegQCCCCAAAIIIIAAAggggAACCCCAAAIIIFDAAiRiCxiY4hFAAAEEEEAAAQQQQAABBBBAAAEEEEAAARKx9AEEEEAAAQQQQAABBBBAAAEEEEAAAQQQQKCABXwLuHyKRwABBBBAAAEEEEAAAQQ8ToCHXXlckxAQAggggAACXi/AiFivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wuQiPX6JqaCCCCAAAIIIIAAAggggAACCCCAAAIIIFDUAiRii7oFOD4CCCCAAAIIIIAAAggggAACCCCAAAIIeL0AiVivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wuQiPX6JqaCCCCAAAIIIIAAAggggAACCCCAAAIIIFDUAiRii7oFOD4CCCCAAAIIIIAAAggggAACCCCAAAIIeL0AiVivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wv4en0NqaDHCQzod5PHxURACCCAAAIIIIAAAggggAACCCCAAAIIFKQAI2ILUpeyEUAAAQQQQAABBBBAAAEEEEAAAQQQQAABI8CIWLpBoQnMjphUaMfiQAgggAACCCCAAAIIIIAAAggggAACCHiSACNiPak1iAUBBBBAAAEEEEAAAQQQQAABBBBAAAEEvFKARKxXNiuVQgABBBBAAAEEEEAAAQQQQAABBBBAAAFPEiAR60mtQSwIIIAAAggggAACCCCAAAIIIIAAAggg4JUCJGK9slmpFAIIIIAAAggggAACCCCAAAIIIIAAAgh4kgCJWE9qDWJBAAEEEEAAAQQQQAABBBBAAAEEEEAAAa8UIBHrlc1KpRBAAAEEEEAAAQQQQAABBBBAAAEEEEDAkwRIxHpSaxALAggggAACCCCAAAIIIIAAAggggAACCHilAIlYr2xWKoUAAggggAACCCCAAAIIIIAAAggggAACniRAItaTWoNYEEAAAQQQQAABBBBAAAEEEEAAAQQQQMArBUjEemWzUikEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8CQBX08Khli8R2DDcycsVeapNfdb2p6NEUAAAQQQQAABBBBAAAEEEEAAAQQQKE4CjIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFCARWyybjaARQAABBBBAAAEEEEAAAQQQQAABBBBAoDgJkIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFCARWyybjaARQAABBBBAAAEEEEAAAQQQQAABBBBAoDgJkIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFLBNHBBuL5aREzQCCCCAAAIIIIAAAggggAACCCCAAAIIIFBMBBgRW0waijARQAABBBBAAAEEEEAAAQQQQAABBBBAoPgKkIgtvm1H5AgggAACCCCAAAIIIIAAAggggAACCCBQTARIxBaThiJMBBBAAAEEEEAAAQQQQAABBBBAAAEEECi AiRii2/bETkCCCCAAAIIIIAAAggggMD/t2PHJAAAAAzD/LuujkIcjOwrAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXIO/QVLi8NHo8AAAAAElFTkSuQmCC[/IMG]
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABWIAAAIsCAYAAAB4P9B5AAAABHNCSVQICAgIfAhkiAAAIABJREFUeF7s3Qd8FGXixvFn0wuh9947SO8ohC6ooHCgcvpXT /siuJ5euIpng3rneU8y6koFhARRRQEgrQAQXoRpCtFOul1/ 9uEtgkC xuMmGT/ObzUcjszDvv 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 gACCCCAAAIIlGyB39cr5bnHdfqGP nkFeOd/yUuSDlHm9KV9qRjmyeVeuIcm/j16pJefz/APfqd4h395KllflAZN1UoU/05b/vTX7nFXJsTlbLXjQurEEAAAQQQQACBUiDAy7pKwUmkCQgggAACCBSLgD1BmQu/VcoPa5S554iy0kIUUK26Ai/pppArByu4TkixVCPvQY4odcrLSvk5QkHRAxVSJ1KySYFNgi9CXTgkAoUVoD fUzBxr9JmfK20FVuVeSRRCo1SQN2mCho RuGX1T7nblKWMj//h Kn7jLb1FfYf59WWK3zbM5HCCCAAAIIIICAhQIEsRbiUjQCCCCAAAKlRiDjgNKefUZJK80w0qjaCurQQ0ERWbIf EUZ332qrMqdFDz2fGGIRRKJm5S LUPqOEaR9/V3ZLAXWIIU/H PqdzoCAVEXWBTv/y4pNffL1H9p1Jlrj97SH9stZIefk1ph7Jkq9ZIgV1aypYWr6zftih1 d7zB7H7vlHSJ/skx3cz6R4ej80QQAABBBBAAAGLBAhiLYKlWAQQQAABBEqPQIYyP/6XM4S1XTJW5f52hQLNwNPcxX54vdIPR1yc5h47Kbs5sq1yRQ9CWEcVbbLVb6GS xegkl7/i9NNSsxRy1x/9uTMnFTav/9rQthwBd3wgCJHN5PtzDcumbKfSj13IZm/KuXlmcrqfqVC989UqsljWRBAAAEEEEAAgYspUHL/HXIx1Tg2AggggAACZUkgYaVSZv8qhbRW IS8IayDwVbjEoXUyA SosxFs5TyzSpl7Dsuuz1MASYADb58lMIGNswbmp6Yr4QbPlBG19tU4QabUt6bo7Rth2S3VVBg16GKuH1YnuBXudu7HnLBizq54OyK4PveUeSAsDMrMqc9rPhPTBvOLM0V/uEkhVbKXcnzOPK336NKXM36DME2YUXu0WCrnuBgWtesTMP1tZYa9NUViDnG1d6z/p0jxty3jvPiV8maSQyf9VRIe8x8qa8ZhOf7BbwRM/UEStxUr cJ4yth82D1Kb0boN2yrs7tsVUjd7H6/q762n4xDetPccZOdd7UP5Hvv46G8araxVM5T88WJl7E QKpiR3peNUPh1PRVQ6Fk27LL/vEgpMxYrfcuvykqymy8L6iio1yCFjbu0 PvzeU9O/g TlPnjAjMFwHpl/GL64/HTsgeVU0CD5goefFW 63eTksY q7TmwxUeZeZqXvm7bA37KPzBIbJ/9JqSVx6VrW5nhT10q0JqB549UMZRpX/ iVIWbDLXV4Zstcz1Nc5cX/mr4vh53yKlrkmWzdwfIseYEDbPNoGyVTjXl0CZypzxllIOtFHEYz2U9dhMd6WzDgEEEEAAAQQQKFYBt3/fKdYacDAEEEAAAQQQ8GsB 5o4paeZKnbpo DKnlTVjKD95J9KmLZb9kpNFDKwu2wBx5W5LFapr25QxoG/qdwNzQuOYD22VImP7JW9RUeF9G szLWxylj8sRLSK6r833qe3T6yncIm3G4CS7OYR5ZTPohTVpvLFTEkNxmVAlrlnSM2oNdYE3YmmR0ylTHLjK5zTBd5ziVR6a9PVuL8I7LV6aCQK rJdmqH0l94Thk1Ms 5l88f7P1GCf/6QllVmyuoS10FnjqszJ/XKOOwyb5zgljv6p9TE089ZXV7C1m Bz4 2e/ SgnPJMnWo4dCOtmUtW6F0r94XRl70xT1 GXy/Y22dmXFvKaEl1cqK6qhgnv0U3A5M43H7o1KN30vft0BlZsyTkG53xNY3p 91dmvtLc/U1pwEwW1aKeg6hWktJPKXL/GXL9rlfHbIyp3Y77rd70JbvtGK6TrBqUtW6ikB1Y7A9iQQRWV/u1SJb3dWsGP535JcVrpLz hxB/NCPuGXRR6qZmw9eg2pb30jNKrFby sn4yX4aYiDY42twD4vcpfXlOeFutvoK6tldg XOcqT1fK nTAwq67V6FVE7TuV7f560O2yOAAAIIIIAAAoURIIgtjB77IoAAAgggUAYEsnZnv8I8oHGDguGpu/YfWWACEBPCRnVWxKv3KaRSzhi2cd2VdNdL5oU77yt1gHlhTp18O /aJdudz6jc0GrZH6SY7W dorTYH5We2FMhudMhhNRUUP a2dvsPewMYm01W5nwtqO72jjX2RqacLeh43dmksglFwhif56tZBPCquEVKvfiWAXmjI4M7fiK4l/4/ZzH8PWDjFnzFXjdEyp/TaOzvid3K9NMfZu7eFX/3J089bS6vYUs3xMfn x/P66APz vciNy tsfhyn1kYeUHPexUlb1VEQ3H4fFHjX9/98rZW86UlFPjVZgeG7tzAjcr59T/H/nKPmbfooandOHre7PXuPUVsiklxXWtJrLFACmkKxDSn3or0qeNVPpVz2skIouBdcYqIiJ4xSoztINk5V6or7CJ/1JIeVSFHjwViVt3W7C1EuzR7xumqVkE8Kq6WgTSI9UoPNfI3aFdnhJ8a sLVDbzH2/mXXVFZA0Rwm3zVCGGbx8Zgmrq5D7JyqiV5W8 2XuN1MSzFJm0z o/NCq5rMDBcplBQIIIIAAAgggcDEECGIvhnoZPeaQQWPKaMtpNgIIIFCyBbJOZycfAeXLedSQrNhVyjTDVQMGXnk2hHXsGdVJoUPrKm2aY1TbIYWNyQmickut3EehQ3JCMce6sEsU3DFEaYsOKNORxTT36PCF3ihjSawZbRuooCvMlAguWVxA32EKeS9OqccLfYg8BdjrD1GEawjr LSieSFRYQ/joafV7S1s Zb5RHZT6GCX/hZQTSEjuypl83KlL9skdevk0xnInPeDMtLCFHLVIAWkx8vu8oIoW88eCnx7izLWbJTdBLEXfrmcT1Uo5E5RCmyW yY7MwdrYrL5/sL8ag9XYEvj9bN5Qd9uM1rb9XuP6lVzRhCbXx25Z7oJTp23CzMlSVUzdUDiSWU5RtWb6ylj2SpzfZkRrlcMyglhHdvZFNB/uEI XJvv jJTPDiOb4LatPdmK6DHLSp3XTcFRqQoa WXSnojRmkvvqbAxo8r9MztxExJ8LmZkmBfHYW9MlQBxYTM33ML2e3YHQEEEPBQ4Pv50z3cks0Q8E8Bglj/PC/UCgEEEEAAAT8ScLwOy/MlyzmCzabAJmenCsjdO7BxQ/PbX5W537FNviC2dh0F5gtNbBUcgVCy7I4spliWJGXtPWaOVF1BTcvnPWJAAwU6mlTEQWxg986FeAz PCgeeVrd3sKXb5lP3fp5gnaHpK1RA3MulssxCjNLnfKcl6zVs8xcpafygNvaD1NYr ou68zcyNuz5yJOm3KnHNmj2 XECefUGoUO290W7n6lZ/XP3tf 60qlfjxXaT/tNvPbFpwuwG7mvHVc42eWkNxvLMyUII7fnvnZ/D7YMU2IkXAGsWb 2f0nzW9qKLChyxv/HAUFNHRzfZnjZDmOZe4BVUYq4t7 OfeISAUOuFkR 7YpfuYOpf6wT6Hj6ztKkXbPVtLnexV49ZNmHudzTFuQvSX/RwABBBBAAAEEil2AILbYyTkg32DRBxBAAAFrBYp6ZFZA ewwNHtkbL5HgN00xZ7imI0xVLbybv6aYcpyRCNZSW5mbAwPLVha7uvRvcuCC5bj8ZqUnNC3nGy5gwLP7Btm1hV9dBZgRhNasnjkaXV7C1ZT7lzDnODx Vsy4l1YzBzLvYty1T6pyDeVYGBPbIF8SawNA5gNw83v/gDQox06u6XUKrWRO uz1Y9krP6m 2PbRQiQ 8p4yMagoaNFphLczI3fLZ16Z9yQdKWmAmL3YMeXeNkc9Amt84fu8K6xySaubIdU7qbK5756Uf6eH1FSBbuCPZTVNA5w75vqgJUGBbM1ftzEPK2rPPbOMIYg9kT0lQbbDKjW3kOFCxLfz9ttioORACCJRRgaL20ZZaTZfiDg5l9IflArqoAAAggggAACfiMQYEYJSr/LMVesXReeJ9YW5ngLUaLspx2TnOb7q8bp OyXbEXkvqnIb5qZUxETtjrn9EyQPd784vLkuiNBsicUHB14JnTKn9w5ikl2Ezjnb3JQ0Ye7 Q9x7p99aO 5C3PzSRGUfyGf3NDPW/8Ec45NjfOEsfHZ6xQRXiCkDfzjFFX8o5sm5lll9nM km9eAla9rYJaXWj74vvcs/qbqQO na2MpFAF3/sPRQ7MmyRnrCrs0PTc/mDuDwWuLxNiny54fQXUyJ7j1WbOSYElPOc kpaecy7NaPvdjjK V8I13xfYXNqnlNvGmyu5pcI//rtC8w16d7MDqxBAAAEEEEAAgSIV4HmdIuWkMAQQQAABBEqfgK1TJwU7BqWtX6p0Dx7LD6jveAuXXZm79hbAyF0XWC//m7oKbHqRVkQooIFj1O8xZfziSIpcFvs ZRZskpkGM2ck76nT UZRnjaPYbu WegiNem8h/WhvectL/ HVpdvjuer//69ysw3d4DdjKx0DNy0mf7p21 Sw8z8qrVNCSeVEbcnP0YJ NmurMOOqTnMC/Ha5B/Oe0gZ204Xsg2mP9SvZMo4Zq6lpLxlmYsr0zGwNd8S2KyxMxTP2n g4Cjlw79nB7BVKuUE5zUUPHyQQgv810uBzhHuUeZFf47PuxaYliL/cfkZAQQQQAABBBCwQsC3v2NaURPKRAABBBBAAAH/FIjqodARJlxK26Lkl75RZmLeatp/36C0DY55H7OXgO7mZTrmbxhZ82cp7YjLCLfjq5Ty3X6TctVXcK9888P6UcuD vYwIVymMr6eq0yXFy3Zl32vNEdGlX8JM3PbOgbt7Vqj9MNnh2XaN32l1M35N/a/n71ur5dNsLp8 eqftFqp846cbU36QaV9udoEe UU3KeNl608u3ngoEEKMtOiZs6eqtTdqfnKSVfWph Uus5fA3ozt3MtxzBwE7puOntNm9Yoa95HSt3lM8uZHYP6dDfXV4bSZ3 rzDM8JgCOmaM0d1/0dOilYJMJ25d/ndczbZ9Sv9loyg1TUJcWOeU3UMhfblR4gf9GKtiR/6qSgq51fD5EQf46KL/wxJSAAAIIIIAAAn4swNQEfnxyqBoCCCCAAAL IRCsoPH3KnzfM0qO 1Txty5RUIemCogwb1I/sFMZmw8q4LrnFdK YnZ1q0crYtxSJUxbq6T7Jym9e2sFBJgRpivjlHkiWIFj/k hxTkg9vgOpa3NndvTBKxHHdU0o1WX/Ki03PcFVW lkHY58xC0uFLhg1Ypcf5sJdz3m0J6NZTt1HalLTqmgEbB5tHn/GelsUKi6yj18x1KfnCSMno0lS1xnzJWJyrAmGRtOOcrm/IX5P5nb vvvpRzr/W6vecuyu0nVpcvH/2rV1bWu5MUv6WngqqkKWtdnNL3pMnW7SaFdXG8YMrHpfpARdy9VQmvrlLyhAeU1qOzgmqbjpZwRJkbNyrDjJIO lMnhXbwsXyL 0PgkGEKmvOB0t94TAkbeyioRqCydq5V tpMBXWuqfQ1h3yseM5ura5SeH9zfS2aZa6vXQruXN9cXz8rbelx2WoFyZ53Gl7zgq/2CrutmzJeMF/kTPybMnq1V2CEeSna2tXKOJApW8cbFN7LzbQFhasleyOAAAIIIIAAApYIEMRawkqhCCCAAAIIlDKB4DoKnfSsguZ/o5SFPylzzQrzMp8gBVSprqAh4xTS1/WFUyZsvfYRlasxSylzVikjZp4ZZRhmHknuoNA/Xq2wQSbYLE6efUuU/MrCfI81H1La2/89 1b7XneeDWLNi4SC7/y7Iqt/opT5G5Q6Y7NsdVoq9MGJClwyUYm7c94Mf6YNZhThtRMUmfK kmN VvrCIwpo0t543avA1ZOUUNgg1uv6e4vrbXv9rXwf/RtdpXK3HVbyR4uVtsKMUK1YR8Gjb1L4tY4Rm4VZbArof7ei6i5RyszFSt yQqmxJuAtV0kBtU0/urGzGXGb/7F/L45ndX oNUiRz4Uo5f3vlR63QCnp5tpteonCJl r4G1TTBDrRV3dbhql4HseV2Qtc339YEbTz9lmAtgWCrn/YQX99Hcl5g9iTRkBl96pcuWbKGX6EvOFzmJlpJmXeNVoqJDrLlfY6M5yvg MBQEEEEAAAQQQKAECtqlD5rl7tUEJqDpV9GeBds9WLlC93Lcc8lbZAjSsQAABBIpUgPttkXK6FHZaqQ/foeStHRXx2QMKKfWPNlvdXqvLt6ofUC4CZwW439IbEEAAgeIRON/9duPD7ua2KZ56cRQEvBUo3Bf 3h6N7RFAAAEEEEAAgRIgYE/INxGuo86/makMtplf27QvdfNLWt1eq8svAV2KKiKAAAIIIIAAAgggIKYmoBMggAACCCCAAAL5BDI/eliJG8yj6h2bKrB6hOzHdiv9h1hlBtZX2P9dVshH1/2P2 r2Wl2 /4lSIwQQQAABBBBAAAEECgoQxBY0YQ0CCCCAAAIIlHGBgA59FLR/vTIWz1NaQqpsEZUV0GaoIq4dpZDGIaVOx r2Wl1 qTshNAgBBBBAAAEEEECgVAoQxJbK00qjEEAAAQQQQKAwAgE9xirS/FeJhjtnAAAgAElEQVRWFqvba3X5ZeU80U4EEEAAAQQQQACBki1AEFuyzx 1RwABBBBAoIAAL0UsQMIKBBBAwBIB7reWsFIoAggg4JXAg2v 7NX2L3R y6vt2RiBohTgZV1FqUlZCCCAAAIIIIAAAggggAACCCCAAAIIIICAGwGCWDcorEIAAQQQQAABBBBAAAEEEEAAAQQQQAABBIpSgCC2KDUpCwEEEEAAAQQQQAABBBBAAAEEEEAAAQQQcCNAEOsGhVUIIIAAAggggAACCCCAAAIIIIAAAggggEBRChDEFqUmZSGAAAIIIIAAAggggAACCCCAAAIIIIAAAm4ECGLdoLAKAQQQQAABBBBAAAEEEEAAAQQQQAABBBAoSgGC2KLUpCwEEEAAAQQQQAABBBBAAAEEEEAAAQQQQMCNAEGsGxRWIYAAAggggAACCCCAAAIIIIAAAggggAACRSlAEFuUmpSFAAIIIIAAAggggAACCCCAAAIIIIAAAgi4ESCIdYPCKgQQQAABBBBAAAEEEEAAAQQQQAABBBBAoCgFCGKLUpOyEEAAAQQQQAABBBBAAAEEEEAAAQQQQAABNwIEsW5QWIUAAggggAACCCCAAAIIIIAAAggggAACCBSlAEFsUWpSFgIIIIAAAggggAACCCCAAAIIIIAAAggg4EaAINYNCqsQQAABBBBAAAEEEEAAAQQQQAABBBBAAIGiFCCILUpNykIAAQQQQAABBBBAAAEEEEAAAQQQQAABBNwIEMS6QWEVAggggAACCCCAAAIIIIAAAggggAACCCBQlAIEsUWpSVkIIIAAAggggAACCCCAAAIIIIAAAggggIAbAYJYNyisQgABBBBAAAEEEEAAAQQQQAABBBBAAAEEilKAILYoNSkLAQQQQAABBBBAAAEEEEAAAQQQQAABBBBwI0AQ6waFVQgggAACCCCAAAIIIIAAAggggAACCCCAQFEKEMQWpSZlIYAAAggggAACCCCAAAIIIIAAAggggAACbgQIYt2gsAoBBBBAAAEEEEAAAQQQQAABBBBAAAEEEChKAYLYotSkLAQQQAABBBBAAAEEEEAAAQQQQAABBBBAwI0AQawbFFYhgAACCCCAAAIIIIAAAggggAACCCCAAAJFKUAQW5SalIUAAggggAACCCCAAAIIIIAAAggggAACCLgRIIh1g8IqBBBAAAEEEEAAAQQQQAABBBBAAAEEEECgKAUIYotSk7IQQAABBBBAAAEEEEAAAQQQQAABBBBAAAE3AkFu1rEKAQRKgEDm4bWa9t/PtWDTbzpyPFkZps7dJk7V5MFhRVD7dM37 3V6cWVL3fnZZF1ZuWCRR2c puvf3ObyQQWNfPkd3d624LZFvWbllPGaNK Kxr/9qv7YsKhL94fyLuzvD7UsTB287T/ebl YupXIfY9/pwlj39Xm7nfq66f6KcTPGlHU9ytv 4O32xcvX m63i/ /bl0eRZvX RoCCCAAAIIIIAAAlYLEMRaLUz5lgvYT /SvM9na/6KLdp9 LRSAsqpZtM26jVouEYPaa4KOeO 4166UY/OTTpbH1uQwqIqqnaT1up1 VUa3awl1qu mNP uBL4 r/V1va8pVFfO0I3neMxo55SeVH/GYpt/b3vlZ7jqXAyggOEwVqtdTq259dc24wWpbuagGof uWU9P0UdbI9R60GANqltOQTapdrNgy71zDxDVaaTum3DS eOBmKn6/KdiO3QRH iIPrvjDr23o4f Pv8B9S3i0kt cdb4eNt/vN3ed3dr2lt66uNLS4r fuVtf/B2e19ayT4IIIAAAggggAACCCCAwIUECGIvJMTnfi2Qvne nnzoba06blP5Bm3UqV8NRWae1v4t6zX9pZ8UX22q7uuStwnVL4lW13qBUmaKjh/cpY3rftRHa1do6c P6pU/t8kTxvrS KB6nTTkkipmV7vSk J1 JdNiv3yXcUu3a5Jb96jnhV8KTXfPgkbtGpLumydx mfEwcqogiKzFtEkLrdOlkvjotQ7fLuCw9t2FnDGmZ/tmn35yaIzXS/IWt9ELiwvw F tUu3vYfb7f3q8aW9cpYcL/ytj94u33xnrLSf73jWbwCHA0BBBBAAAEEEEDAfwUIYv333FCzCwmk7dD/nnjHhLCR6vznx/T30Y1dAslUHVgxV1vchJ4NB9 ke848vm9XwoapmvDXr7Xni/9p9ogXNLbOhQ58/s9D2w7TPfd2cNkoXouevFfPLlmiT74fq55/qHH Ajz59NgJHTfbhVapZEEI66iATRUbtFTeccCeVIxtikYA/6JxpBS/ELD8fuUXrSxEJbjeC4HnZlc83aCwCgEEEEAAAQQQQMBPBAhi/eREUA3vBU4tnK6v9mcptOsf9VCeENZRVqhq9xyp2hcs1qZy7UdpRJuv9fr6vdqyJVWqE3rBvbzbIErt2pp0d8k2HT/ueJTfxyA2dw5I14PPe1ZD5p1dkXeO2ET9smi 5i9bq/XbD5p5ZE8rLbCcqjdqpV7DRmnskMYql68hez6coD9P3e y9txzxHpnkLu1Xae2LdAnny5Q7Kb9OpJoV0SVumrbd5jGjnJpH5Ss04opXTPtJH89Zrz/EMRdZupejxN6m1bwd32StFc//2R70S51pQrJ4aNMZlRWvdM MJDc8T5idr9w9faOpXsdq455iS7OGq2rClel8xWte58fS2ml75u8wJOv0Waepbs7Vk6yEl2CqocffLdcfdV6hl/hOsVP26bI6mzVyqTfuO6HiSTZEVq6peq3aKHv0HXd4y9wT44uN9f/PWx7rtfWmvozZW9Qdf65MtlLI7Rm971B 8vB69OQFe36 s9PSm4q7benJ d g/1z2iLzVC/5p2o1qc81D79P7ND iTUwP1/Iw/6xIzlYzl13vmMa3 5EN9 J3j/pmpyDqtNOiGm9Ui9kFNLoo5tr2 P3va3/brg5snaNrv3fTI9Im6zHXOIIdvepyeHfOcFkUa84 MubF0LF55njlPidq5YLamf7taG3cd1sn0YFWqUU9tevfXqKv7q2XFnMKd23ta/9zCPb3fnqkMv0EAAQQQQAABBBAoAwIEsWXgJJfOJqZq5dL15gVVgeo qHchR24GyOb8t5ZNgUFFNYeri7r9hOLW7DUrQtS0aSGG25Zrr sfvlvOWVmPrNQ7765SfLsrdP/whmcOVq216xyx /X9mx9rXnBTtW95idrVrKjQ1JPatXaVpr wRqt naR/39Iyz0t9qvW5Xg/VSTTlZWrT9Df07U6XdhT6t3YdXvCKHnh uY5HNVL3XgPUNypLx3eu19IZrxujX/Xcv8ar9Zl3jZ3W0uf/rqcWHVdko24a0q 2Ao9u0cLnntSK6lmFrE2wOoy9Ww8NdBQTr5Xvv6/Fh5po5MOXq/mZkiuqZZ45HzK0feoTevDDncqo3FSXDu2p6rbj2rhkmb54YZ1m2SXr25pfkKwPfFJ/9ji/XPB3brZKsu6jOwiX6NW6G1Cz/Uo mV9cGk3nnC9sPfTtHdL5vrplor9enXWTUjMnXy8G/avnaevqo/wCWI9cXH /7mu1RR7 lLe63sD77UJ8fE4/7g7fXopbnX9ysrPb2su3NzT vTWG3bhOrLmB3aZh5TaOHmxYbO4hJ/0c /SoHdW54JDq293hO18pXH9Ph3RxRmpssZOMrMgX5yuxY 85Riaxb2/ulokLf3Z2/6Wz1FRzfQtA/WKmZ5si4bkDeJTV21TLHmj6naV/Q9Y mokdee9mNa/Nzjen7BYalqM/XqN1R1okzLDv6iuJlvKrVBX/1jQO6fqd7U33nG5fn9Nnv7M//f qGuv drHVXxvQAzXw34EQEEEEAAAQQQQMBCAYJYC3Ep2kqBvdq50/GPybpq0qQw0ZeU stczdtsigpuqY5tCv yq9Qt8/XmG2tNgY45Yk/pwJZ1WvdbgJoOvU1/ji4wRNFzpJDa6jwgZ4zvnkOaZoLYpFptNGBA53OUUUcjJr uW5pXV5jroJ6sq/X5vffr3RnTtfCaxzTUZf6ByMadNaCxo7h0ZS4q4iD2yHy98NJyxTcfrVeeG6vmZ0LOTF076ynd9fpsvTErWq Ny25j5oYZet2EsAHNx rlV0ervvNuZdeYTs/p1ilrztFmT1cHqlaHS1XLufkRHf3CEcRWU9sBl577ZV2/z9MbH 1UalRXPfzmRPWvnIM6vqeevdWMzvr0Hc0abKa2qOtpHQpu55P/LzsVfO8Len1EdTmJkntpyo1P64dli7Q8obcGn lyR7R4znol2Vrprtee1BWugVHGaR08EeJSIR985H1/Kyhwsdb40F5L 4MP9cml87Q/eHk9en1mvL1fWerpde0lj sTqDZtm0ox27Vta6au6m3mH3ez2Lft0Ha71KRtS V 12Tl9W7fNlOvmRBWjUbqhdeuV9Ocy3tM5yn60zMmeCzk4vX92cv Vi 6j5p88LFWx6xU0oB LlPwpGnlojgzFr2Wro52/mF1ZvHW8 jcN/WiCWGD2l6nV54dpUYuf5XIPL5RG066fDHrZf0df654fr8t5MlgdwQQQAABBBBAAIESJWDB8L8S1X4qW2IF4nX6lKPy5VXB9dHxQ7F679X/6l 5/322QQn52rhn3v yP3/pNT31t4m68a7PtN1WS/3v/4sur154kIy9qzTry2/Nf3M15/vlWrs/TdU69NXQwe1Us1ivuCg1aJEbwmYqNTFeJ0 c1ImT4WrexjQ0w4zgKtIRr e32zP3O21IC1fPq4eoRnq8Tp3K/S9JUb17qbXNrh2rN8h5Ws2yZUmsmQc3SF1HDssJYR1rbao68EpFn2vU2fmrUKhPjy2L1VaT/dcaOkr9ckNYR4nlu jaEfVNRrxXPy45WKhj LRz5Us1bnhOCOsoILyj nQ2qUvWr9pnRuCdXTKV6XyfWqCC8mdFQeVVq9qZocg VUPyr/7mYyM83q2k9wdvr0ePYXzc0N88valPpbYtTCyYrm3bHE8 OJYDmv2Pv quR83c4zlrfjVBbIIqmdDWx6lpcl09vN63xizT7 Za7zzqijMhrKOISv2uULTjXZKFXLy9P3vd32r3Uf WNjMLwTIti3epbEqcYmJTTMDcV9GNCtOIQ5o/e72ZrKW2Rt11VZ4Q1lFqYOV26tj47I3S6/qbp0p8vt8GhatipQqqZP6LZLhEYU4y yKAAAIIIIAAAn4pwF/x/PK0UKkLC9jN2MjsxXWwp05s14Jv5ptH nKWljV13dj2eR7P/n39QpmBgWeWoGqd9JcnJmhUs8KNrM0tMHLYo5o5wfGyLrvS4o/r4PY4ffbmh3ptYpx2PvGC7uuefyLUs3Up6t l7F hT9//RgvX7NThRGcKl2dJMnO0OsJN65cUE1Jkzz276OlbtehcBzye/RKyCkrUvr0nzFY11KhxPq ARmrq Ae4421lxbjsc6aaNjVu1qiAWIOmDU1kvM/U2bFN9jjbYqta3bqql 8UVqxY3hw WUnJrrWooR59G2nqzk16864ntKVfJ7Vv3VTNWzZVg0qFHwnuOJL/9Dfr9Ut2f/D2eix7nl6d38at1NaM8J9vwtbTaqzyR9dqwbJd2qEsrTpwhRrWTs2 /wV3U9uzc5/4hurR9Z6k3buPmfJrqFkzx73AZQlooMYNzc Oj31evL0/ 9Lfqqp/dAu9u22jYpbGa9AwM2eAWZKWL9NqM5V7s i 5nmYQiwZO/XzLrN/VGt1bHKhb0h9qX8h7rfNxuj1z13nKy9EO9kVAQQQQAABBBBAwO8ECGL97pRQIc8EzEhYx78vjyXo9Gnza 6o2FY36OP5N5inAufo3uve1zY3heW 0MqeGq99P83Rv6d8of/87WWVf OvGlD9bKJly5441k0JrqvOF2LaFBJVRQ06D9HESfHadctn u7tORrV/Q9qcIFSi Jj 8Ef9Pjdb2ldejV1GjpO17auqcrlw8wYKelozDt6ed5hM2LHMb1D/uGRRXH0/GUkKdE5NLmOhj9ys/rmeQGWy7ah1VXT WOKkp0hYjlFZf/722WjcEWVL446uxzS/DY52YzCMg8Vly/v5rZZvrwZm22yYVNpR9xdrLULD1P d9lkh smZM/9tsLZFJsaXfeYXiw/Q5/MXanFn32oec4cPlTVLhmgOx64Qb1q l5z/ pvzgZbupTs/uDt9WgppbNwf/P0qj62FmrT2qb5W3boZ/sQtYpbr 21u6hn8BrFxZ3SH678zQSx5l7bopUKPfuNR9d7spKTHKrm/pkvhzVD5ovg/unt/dm3/la1X1 1 882rY2J1elhg8w9NlnLF61Vmq2povtn/0nhc89MMnVy3P8qV9KFH7Dwpf7W3m99bjc7IoAAAggggAACCFx0ATeJwkWvExVAwAOB mZuWBOCHjuoXbvTpXrej izhZpHqXuO06T7D mWJ5fp9deWqMuTl57JdIODz3N55ARcIcGeHddWv6VamUBx976d sWM5mlQNINvz u0bfZMrUsMVbcHn9bkIS4TwZq91jse7SzWJUKRzrlKkxRavb2Zi/dCBw9XuHMO2QTFOx5LzTNlRLIJ3wuO7r1QiYX9PNwEII76nD6dYX7N1zfMtwGOaoaEhxdvCOtto2xRanXFTXrS/JeZdEy7N63V4q1MxV3 qfz1bTe6 MMGPofFv8q7/51gZv9irZ/cHb69EbGd 29TdP7 oTrjZtzPQkcWa6l73pSlmzRRW7PqKxIfv0oAllk7ud1DbzlsVaQ1qYyQmKY3G5fzq qMxz/0wx99TC3j 9vT/72N8q9VT/ju9pw9plWnJykIYHrdSiuHTZ2vRVP19vVLn8EaZOju9Rj51wDg6ud97T4mP9Lbzfnre6fIgAAggggAACCCDg1wIXeh7LrytP5cqyQJi69mpn4rB0xS1aWWAeWG9kyve9XuNaBSpxxaf6ZLMjZMteypfPHoqZPTIqb4mJZjSNY4kq7 HLt zmMXFH9mnPUPrZQ QttEh/Mm94PuyYoKGW2rXLG8JKB7V5c 5MrEVz0MhIx5jMNKWakNn9EqYWLeqYj04obtXuvAM13e4QoQYNHOOUjmnPbvN6bNclc7d27na7k48rAxTgHAiaO6ef 2Lq13c8CGvXrl/2FKj/XrPOfB2g g0K9bCs wNbtDYwooqadhuoW556SKNNtTO2bNFWt33TE5/C9bcL95 8CN5u7x2hJ 0157rY oNn9fGujd5ej96V7svWhfH0tj94sr239alvXsJV3txbt21ZozU/BaprtxZq2b2TItet0 qNO7RboWrbtqEvND7sE6FGjRwTwR7Vjh2uE6yaVfY92rXHhyLz7OLt/dnX/halvtGXKChri2IWn9DpJcu0NiNAHQb08mAU6wXaGNRELRzv krYrHXOF3 eb/G1/mfL9Px e7568BkCCCCAAAIIIIBAaRAgiC0NZ7GMtqHSwDG6vJZNScs 1EtzfzUv3Ti72NPTncGYZ0s1Dbr/lH9BHN d8PZ aXrdGmhRz/lN25aIF2uBaeuk/fL3S85SpKrVt7Mh9oun6d/b1WOZO65mpVLFPE2lS7tmMY1EFt2OCYazV3ydShue/riyJ SVfNOrUUYB4b3bZ5X4GQMvfIjYYOdT6Wu /L9zR9V/7ENl1HN8zTnDVnQ4PWl/VUVWVo1cxvdHZzu44tmK2FRTo/bJQqVnQMjTIvt9qb51l FzepSq8eamXumAe/ 0I//H52RJn9WKw mrPPPOLfQJf29aQ/5Cm2GH84oe1r9yk f aQcEgHHKPmIqLkfsYHT3wK19886T uUN5u7x2yJ 0tzv7gWX28a6N515GX16O35Xu7fWGuL2/7gyfbe12fVi3VJtCun7 eqTWp7dXtkkDZ2nZUF9t6fTZzhzJtzc2oWd n/vDWs1W/3mYgbKbWfPm1drr8YXhqyVwtOjOJurelnt3e2/uzr/0tqk9fdQmxa2PM95oVs1GZQW3V/9L8Xy760o6aGjSivULMn5FfvvaVduf7I8l aqs27Dl7n/e /r7eb01bdnymv1xzs8Zcc7/edze/ki/NZR8EEEAAAQQQQAABvxE4z7PXflNHKoKAe4HQlvrTP/5P x96X8temqgbv2qrDs2rKjj5qLb/tN68rdqmynVrmlk9L7yEdb9aVzf9Ue vn6lpP0Xrnk4h5vHHK/WnPsv1/NJZmnDTFnXtWN9MWxCvPWvXasuRdFXodovGdiz4D vUTXP1r1dXmYPalZ54Wkf3bdeGnSeVEVRLV94xvFjmh3W0uNnlI9Tuq3e1 tW/6oH1vdXOzP956pc1ionLVLuutbRy9cG8MMe3m8c D QE2BnafMTx8SltWxyjsNzwuEZrDb4kz3OuzjLC w7TkHfiNHfa03roqDlW1VCjX1XdxkSrRe4EpjXMXLkTNuvBF2L17p13a1mvrmpXp5zsCb9r5/r1Wr8vXq1u76zhnbOrFdDmGt0xIFaTF8zQg7f/ot5dGyrylGNk1DFVrB2spAN5q /7TyHq1KOdgmM3aMbk55U8uK1qRwWbYLmy2g7uogYhOSXXGKTbxy/WxA/j9OIdD2tFr7aqEXBUm1as0vbjwWp07Z80sjADYgvh71nbD i7p/6hecGN1bF9I9WpWVEhKb9r89JYbTodqhY3DdMlbqc89szH6/7mUmmP k8htvfMJ3crz9orq/vDmUp7WB/vGmne4 Td9eht8V5vXwhPS/qPt/UJbSXz7jut Hm3kroNVUfn9DNt1a1zihYsMd90NOivNq7zXVt8vdtaXq27hq7Q4999qYm3/6ZBfRsq/OTPWvTDUdVoHKx4x4uqCrF4fX/2tb9FdFX/7qGKNX8Of2rLVHC3vupTYN5b0xAfPKsOv10T1k/SlJhpuuvG1erVq5XMH0lKOLxLa2I3q8E9H6t9w5w/472uv6/3W9OWjFTFn443L34zX2 6fUqhECeOXRFAAAEEEEAAAQQuugBB7EU/BVSgMAKhjS/X02831dzPv9b8FVu18oeNSg8up5qNemrs5VfomkFNzetKPFlq6arre2nGE0v1/f05hOV5qH isretJLqjd/pqbOXKH1MTvNmM8wE 620cjxY3Td0Gaq4Ca4ytj/k bszz5mQFCYoqrWVPtBAzVk9BXq19g58WmxLLbaQ/WPl0P0wTvfKnblPM3ICFfNZh01/rnx6r7laRPE5qvGnhjz4rL5yjsRwEEteON1LcjdtO99boNYhbbXn//5F9lf/1JLf/haG9IdI0tbqsIIlyDWRLO1Bk7QG/VjNOPzRVqxcam Wp6uoKhKql6nlUbc0k3ReUY6Ran3g0/pyTpTNfX79YqZvVWRdVoq qFJah33kCYXWRBrRjdefpf ceJ9fTR/k Z8uEapGY76t9Y9fV2CWAWrxR//oVdqztBHs2O1ceFcrTT9oUqDTrrmJkd/aGwePi7EUhh/jw5bV9E3jlLG6s3aunm1Ni5Nlq1cJdWo30v/d dIjexd95zz23ri43V/c62zR/3HZQdvt/fI5 xGnrRXVvcHlzp7Vh8vG n19eht d5uX4jry9v 4NH23tanipl6wDxD8fMxtenWUdnfXYWoS/e2Cljyk8q1bZV3HlLLr/dIdb9vsibX FAffrdOcz7doHJ1W2vI3x5Vk8X36p 7ghWS yWTt6fKub2392dv7/ 5lQpVzwFdFb5kqZLtweoR3T3HNl lffG0VVX/R55X3W5fa8bcVdpg7unL00NUsUYdtb7iNl3d2fWvyN7W3/f7rU ng50QQAABBBBAAAEESoyAbeoQ53uzWRAoUoF2zxZ8D/GQQWOcx/h /vQiPRaFIYAAAggggIAnAqf11YRb9MbmzvrrVw8r2pNHRjwplm0QQAABBBBAAAGLBc6XJ R 5mkVXuj8lqebsh0CRS7AHLFFTkqBCCCAAAIIIIDAxRVIiU80s2znXbJ XaQftkhB7TqoIyHsxT1BHB0BBBBAAAEEEECgTAowNUGZPO00GgEEEEAAAQRKs8D29yfoiXV11aNzMzWoEan0Y7u0/Ltl iWwga7/U7QqlebG0zYEEEAAAQQQQAABBPxUgCDWT08M1UIAAQQQQAABBHwVqNHpUnXat1YbF83Vj/GpskVWUYP2w/XA NEa3LRQE8T6WiX2QwABBBBAAAEEEECgzAsQxJb5LgAAAggggAACCJQ2gRq9r9ej5j8WBBBAAAEEEEAAAQQQ8B8B5oj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEAAvHGYAACAASURBVECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9QEAQQQQAABBBBAAAEEEEAAAQQQQAABBEqpAEFsKT2xNAsBBBBAAAEEEEAAAQQQQAABBBBAAAEE/EeAINZ/zgU1QQABBBBAAAEEEEAAAQQQQAABBBBAAIFSKkAQW0pPLM1CAAEEEEAAAQQQQAABBBBAAAEEEEAAAf8RIIj1n3NBTRBAAAEEEEAAAQQQQAABBBBAAAEEEECglAoQxJbSE0uzEEAAAQQQQAABBBBAAAEEEEAAAQQQQMB/BAhi/edcUBMEEEAAAQQQQAABBBBAAAEEEEAAAQQQKKUCBLGl9MTSLAQQQAABBBBAAAEEEEAAAQQQQAABBBDwHwGCWP85F9TkIgqsnDJeQwbdq6l7LmIlODQCCCCAAAIIIIAAAggggAACCCCAQKkVCCq1LaNhZVggU1v/c6/u yJJg//5ph7oFlrCLEp6/c/HbdfJjXP1/tT5iv35sBIUoZrNOmrY Os0qkMlFfaboRNbYzRv6Vb9vG2nft6xX0eTsxTQ7wHNfbTH Srl8WdWl 9xRdgQAQQQQAABBBBAAAEEEEAAAQRKnEBhc48S12AqXAYETi3TtDmHZWsyXGNLXAhrzk9Jr/95ulh83Du678H/ae6WdDXqM0jDL20s /YY/fehR/XyilPn2dOzj/bM 1Dvfb5QK3bEK6pqedk8283jrawu3 OKsCECCCCAAAIIIIAAAggggAACCJQ4AUbElrhTRoXPL2DXzplfalVKuC67bpjqnn9jP/y0pNf/PKSZO/Txq/N00F5LVz/znP7cLty5cerwabrn3i8171 fa1CXW9UDxlXOCjBsPu0QtXNVCzBpUUtvJ1jXgsRpkX2Mebj60u35u6sC0CCCCAAAIIIIAAAggggAACCJQsAYLYknW qO2FBJJW6pOvfpXqXa1xfSMKbp1xRCunfaSP5q3XnuMZiqzdStHjb1LrglvmrLHr1LYF uTTBYrdtF9HEu2KqFJXbfsO0/jx/dQkMnfH/frg5gma9ns3PTJ9oi7LzhjPlpoep2fHPKdFkSP0r49uVItzDdU8X/2Pf6cJY9/V5u53avot0tS3ZmvJ1kNKsFVQ4 6X6467r1DLcr7WZ4NeHjlZ37W4Un8pv04fLz s4MaX6s6/Xa7T77 s/y0/opD6XfV/j96hQXUCXbQ89ZGyNsRowSEpsPOVui4nhHUUFNpylP7Q/Rs9v2KJ5q25Se175NyWvGpvdpUqNgyi61O 9vD8zS7Td rD397tP70fv15vsLtW5/ggIr1VOHgdfoT O7qVa UNir8s97cD5EAAEEEEAAAQQQQAABBBBAAIGyJsDUBGXtjJfy9u6fNVNLE0PVfdxwNS4Qdp7W0uf/rsenLteBiDYacvUwXdY0SQufe1LvbspyI2PX4QWv6M5739LsTZlq1GuArr46Wt3qJuunGa/rvvs/0paU3N3qKTq6gRneuVYxy5MLlJW6apliE6Xa0X3PHcKavc5f/5xijy3WPx94XxsCG6vPwN5qWyFePy/8UItMzMuVrI qydrx90iQb3qKHEbfP14t2TTLjcVIOHNlfAzh/1yhs/uhzDGx/Tts3bdNpUr1H71orKIxSuSzo2MWuStWnT3gJ28qi9BXfzdI19 2f665M/6Hj9nrry6gHqWP6Ilk17QROeXa4TnhbCdggggAACCCCAAAIIIIAAAggggMAFBBgRewEgPi5BAiYE/XTmbtlrXK5rB5QvUPHMDTP0 qLjCmg Vi /Olr1nb3frjGdntOtU9YU2F5H5uuFl5YrvvlovfLcWDU/M8A2U9fOekp3vT5bb8yK1mvjajv3rRfdR00FirY1YqaUA/8xqq3CVNKxfFmZjRPJIf3bjgcXLXXKD Z3b8ZaeC731Br4 oLmcTkntpyo1P64dli7Q8obcG54yK9ak NQfr/kfHq6m2KX3sY5p9vKFum3y7hkWlqN6BG/Tylp 1Q/3V0XFcL30OHTxsdrKpZq0a5td4bf5mjlZntteoq1qrSk1HW7bpsNnGriZ553b1sL1nfLz8jf3ACdW5/xU9dXmV7OPePFzTJ9yvd358Tx t6667O7iOAPaycDZHAAEEEEAAAQQQQAABBBBAAAEEcgQYEUtXKDUCh fM1KJTQeow9kq1cpOdbVkSq Mm7us6clhOCOtouk1VB16paDfPsZ 502pIWr59VDVCM9XqdO5f6XpKjevdTaZteO1Rt05hVTtfuof0ub0uOWaVm8C2tKnGJizdDZRn0V3ejc3Beq/5k9K1 qccNzQljHyvCO6tM5xDz7/6v2mVkZziy 1KdGddV0FlBV1aqZX8rVUC3n8NUw87OJlhNO6Hha9hG887ErKTHV7BikiAhzcrbN0jOvfqFPXpuiqevMWYiIcAbXWYlJOjPIOPswkqftzd3e218r9NbowTkhrGPfgJoaMbKLQs2Z/XHxFm9LY3sEEEAAAQQQQAABBBBAAAEEEEDArQAjYt2ysLLECWRs0WfTtymz8kBdO6SKm onat9ex4PmNdSo8ZmJXbO3C2ikpo6A9Ljrbinatm2/c8Wip2/VIjclOlcdN8Gk aWC84eq6h/dQu9u26iYpfEaNCz7Afyk5cu02mSQzcy0BOd8edgF6 9Sgbp1VS/ftAsVKzpGACcrKc sCD7UJyRY2dOiBivEZLsKDTGBZPYS4lyRpjRHnhrirY/djHR1WczcvF3qztdidVEnM6OD9ub73HVbj9vrupMXv2/QUI3z3QnDGzcwPSXW9Jn9Oql2quhFcWyKAAIIIIAAAggggAACCCCAAAIIuBMgiHWnwroSJ3D8 y8072iAWt52lTo48sICS4qSnSFlOUXlnaDUrAtXVPn8Q2iTlOiccLWOhj9ys/pmJ60FSlVo7gjS7I q9uurdv/ZprUxsTo9bJDKm3B0 aK1SrM1VXT/7LGmBQsxee4F6yV3iYqXH xZHMmqgzT9ppomFv62Oz5UwLEKAAR5Euga/NfGbGrCrLOZ2utz4Biox0RLppSkrKlMp30X3/ 1D35TTDvi3ZORLWFhlhxt7mW7xob/5dPfo5qpw5T/mW8lHZ60yy7eg2BLH5gfgZAQQQQAABBBBAAAEEEEAAAQS8FSCI9VaM7f1PIOsXzfhsg9Kj ujaEecKO8MV7py0NUHxjmkDqrs2I1mnT5twMM8SoUjnXKtJJmttr45t8n18rh8r9VT/ju9pw9plWnJykIYHrdSiuHTZ2vRVP8fUqO4Wj rvbkcP1vlSHw KlZlIwFuf7Llh9 nQod/NEWrlOcoxsy7dsdbMH5tvsK9HtSnURvEJzpeI5cnaT8c71yk8vGAwXKiDsTMCCCCAAAIIIIAAAggggAACCJRVAeaILatnvhS1 /SimZpz0KZGV49S94JDRXNaGqEGDRwTwR7Tnt2JeVufuVs7d cHCVOLFnXMyhOKW2VeAJb/43P HKW 0ZcoKGuLYhaf0Okly7Q2I0AdBvSSm2lonaV4Vv9zHvACH3hfnwsUmPOx9z712rR0jjLds2GLicNdl2StX7fLrAhXmzb1PTt8UW61d7d2ZeQtMHn3PjleLRbVoK4qFeWxKAsBBBBAAAEEEEAAAQQQQAABBMqsAEFsmT31paTh9n368pM4pUR01bVX1T/vaMrWl/U0s7hmaNXMb7TLMc pc7Hr2ILZWphnftjsTxoNHao2ZsLUfVp lnd8jZL11HN8zTnDWub XK/iiqT191CbFrY8z3mhWzUZlBbdX/0nM83O5F/XMO7PUvXtXHi9K99Qlof5mizajgjDVfa9rms6/kSt3 laavNG8Aq9Jbg7tkz1DrRTUKv mp5Zox79jZsD3tV82aGadUmRC7b vCl08JCCCAAAIIIIAAAggggAACCCCAgBFgagK6QYkWSFr2pWabFz3VGTtKlxaY zVv0wLaXKM7BsRq8oIZevD2X9S7a0NFnnKMXD2mirWDlXQgH0WNIZo4YbMefCFW7955t5b16qp2dcrJnvC7dq5fr/X74tXq9s4a3jnffiYU7t89VLFLZ lTW6aCu/VVnwKTkGbv4039fT5RXtTHq2N46xPYXNfdM1Cxj/2gLx5 UHsu66x6AYcUt/gn/ZpVRQPuHqdLCpnDZmz5Vq/MyRnefGSrid3NsvU7vTBlTXbTmg7SA6Oa5wnsbbUq6td//1X3ruutSyqnaO alVq5J12Vet u8Z3z3iJ9Kd8rUzZGAAEEEEAAAQQQQAABBBBAAIFSK0AQW2pPbVlo2CHNnrZcCSHtdds1Tc87GjZbI0q9H3xKT9aZqqnfr1fM7K2KrNNS0Q9NUuu4hzQ5fxBrSqw1cILeqB jGZ8v0oqNS/XV8nQFRVVS9TqtNOKWbop2O9I1VD0HdFX4kqVKtgerR3R3Rbo9Hd7W320hHqz0tD4eFJVnE 99KnS7Ta9MqaP/Tf1Bq36cp/VmrtmazS7Tn66/Tld3Otcb0TyvV9bBTZo/b3XeHQ5vNutyViW00/0miHV9NZutxVg9e sevf7hYs1ekqjASnXV 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 ggUgAAC3gnYVLFBS1X0bie2LmUC5VoM1f zdx/wUZT5H8e/Sxot9N4JCAQCSBcCCKE3DyyHBc9 nl2x11NRz4Kn3ome97cg2EEFPFpCr6EJoRMIXXoPBEIS9v9sSNlUdjZts/nM6xUxszPP/J7388xs9rfPPPPU4IEKa1ZRqYNfE/dO0ej7v9W2mTO05K/t1L cm5X2baYRTzdL2Xml3prjSMQ20XVPP3TlUfPHT qE2TOgamWSsG7ysxsCCCCAAAIIIIAAAgi4J0Ai1j039vJUAf/qCn3oYY1Y 7R 3DhFv64foAfbON//el675vysiVMjtWH3ccXZy6haoxYKHXajbh0QpGzvYnWprkf108MP6YvopvrbN29pRI3MO/2hCfc rm//CNHj3/9dg9IyVBbiOTFLo0d oU1dHtJvb/SSv9Mhtnz2oB6ffE5D3vlaj7bPfOwr/b5d/7n1Bf2qofrXd3eoeY6b79X4u5/U96f76t3J96ut7Zx2zI9QxNK1ioo aOZZPKOLPuVVo3Gwug0aoZGZPZ3in3SPNPGzaVq85ZDO2ioqqMtgPfjIMLVIa4ALmvn87fpwtXMwkXqj301OK1rq0cmvacjlIXE5Rp39C 6Wb6G9sj wC2vPKWbuNE2asUobdh7WqQQ/Va5ZX61Ce2vE9b3VopLzKG8L8RSC/ 4Jo3X/xH1OdcxljlhL8Zgi3er/dp3eOlff/zBXkRv36eg5u8pWraeQHoM0alQvNXE3CZhcw4Ls/1auJ7dqz4MFff5aiSf9 tZs0EilpkpTO4VvgxCFmDmDtx05q7NxZm2e2sCF0yl1k9T 47xL NsaEJ6 wv05Yt3zkdw7f/P3 u8EknhUK777Rt ER2n3iUSVqxOssFF3qWWOzBbiz7GM/HjBc/0P/PCs7vpip7q/8IOeqDNfX341Q8sd73um49cIaqObRz ifvXzYlAQ7xfr9cHwMZrV/Dr9rcI6fbvssPyCeuqh5wfrzPgP9NWyo/Jv0El3vvig tVN fvqwBQ9cMe32t3rcY0P26dPx8/Tun1n5VO5vq7ue4PuHdVZtZ1HqFu6nrv7fm39 l8w7eWGp6X3F3f7v4V Z/X9OrloV68P7ravhfiTN43X/qXT9d0vS7Rx71GdiLOpXKVqqh/cWmE3/lmDW6S GbkTj8W/B1JCd62/uROPRRtL56Mp2 r5bjEcd8t3zTM1GFf7p7v19ZTrTyFcH6y2L9sjgECyAIlYOoL3CZRqpB6htfTjD4e0evUeqU1QSh0TFT3xNT01IUaJVZqq58CuqmE7oQ2Ll rnsev0 x v6KO7W8i9qWWrq/ Qtvp62zrNDt vEaPqZXC1b5uvOSaU0mb 2l5pSdiCjMdKswYppFWAfl2wXVvNMLHmOT1Y6dwObdsv XRpoebJucB9mv3ptwr3a6o2Ldqqda1KCog/pZ1rV2rS2DVauf8V/fueFhkSxslRHV oN5/cpVPBHdW9bxPtX71ca dN0IsJVfT1K6EpyXA/XT3yET3T17FDrFaMH6 Fh5po HODnRI7ldTC7fua3Sm/ENrLflwL3/m73p17WKp2lbr1Gqi6gdKZgzu0 pdPFd wh17tk/pp1s14CtC/evfb9Ezdc6bNkrRx0ieaEZPc4rkvLsWTexHZv2rX4bkf6sl3l lEYGN16dZHPQIv6URMlJZMHqfVa/brnX NUku3n81UkP3fyvUkSGsK/Py1Ek/2rZG69szquVpyxPzxcVVnda6e 7b5 mr5NrrtuUeUPKva0RX6/IuVim09TE8MaZR2mOotc5rL4EqRuOPj5vl7pVDcfv2Mlrz7kt6Yf0LlGnfWgF515HNss a987qW17g8F3vGoj0pfs/3v7Rrip5//ycdqNFCrTvXl 30YW3fslIbD8n9RGxBv1 sjdCca/uq/zVR t iCL3/SKTK1e k/gMra9Fvi/ThJyHq mbvDF9g26N/1LNL4lShe6iu63RJB9Ys1ZLvxmrz/sf1ycvdVNmt/unO 3Xerv8F0l6WPK28v7jT/91qCBf/fnOUbeX64E77Wo//8Iz39MgHUUqsHqzuvTqoVtkknTr8h6LXhmtqgz5OiVh34rHSXlljz72/uRNP1mMUxJqCOd/TI3W3/Nw9rfZPd LxpOtPIV4fCqKTUSYCXixAItaLG7ckV61BA0ci9JAO7NqnBAUp eP1kXB98k2M4gM76blPn1bvKikjC0d11dv3vaP5P3yuKf3HamTGHKrLjJV69VHXT9dpcfh87bjtdjVNG7h4SevDF mw bgycHAXlUktsYDjcTlwc9Nwq5Cm0oJobd2SpD FZv8EHfvW7Yq2S01CWuhy7qquho4Zp3ua1VBp50Gal67XT489oS8mT9K8G17WwMz3pIkd9jYzVuaI3L3wSd76b37nhLc5bO17KzoeqfPCrWR7Wv7pkyrcRRHfvZkYitrpA Pa9827FLFXej/EJor2MzP9X7JgnrG3KrPnx7hBo7fSuQdGKD1p8qlV47d MpQP9yQR3UJ/l7jwQlzXcxEetSPC41asaNjkZo7D XKbbZjfrwHTMyMy1pn6Rbpryhh8dN0ydTwvTxzXXcKNyxS0H2f8n160nhnL ux5MTp10nVn6lF16foyPVOuupl66Tm5fanA6Q 3r/OurQJ6Wtdx/SdyYRG1e7lfr06ZD7fi6 atnH3fPXxXisbpa0frLGmSRsqWYj9cFHN6pB8l Hdt3U/h3d996arMV5WPye7r/ml9kKvv0fmjgyKG06jKSTO7UnMSutq2sK/P2iVn898eIoNdVWJYx8WdNONNJfxzygQYEXVP/AX/TB5m3art5q5xSw/cBJ1X3iQ70xuKqS/yy4e4gmjX5Cny/6Ut s66JHrs7 74vc6 zG 3Uer/8F0V6y5Gnt/cVy/88dPOdXXX2/tnR9cKN9c44wh1eOauH0KMXZgvXwx69rmPOAg8QzOnjS R4zd Kx1l6Zg8y9v7kTT YjFMzvBXO p8fqbvm5e5ryLfVPN LxsOtPoV0fCqabUSoCXivg9Knea tIxUqgQED5sslJPvvZc YWwMvL8aWR2mIG9tQeOEK9UpOwjpcqdNQtQxuYjfdo0eKD7muV6aRBvc198gcXafYGp4nTE6IUPv kVKOnBnZMH3FV4PFYqEnlkOYm6ZmgrVvNsN3k5YCmvfqsHn7xN 1OWbPfJGLPmvEsrUIuPwpHClTD5qlJ2CTFn4vVqZOndPJUGTVrZeZmSDQjbLMbEVmlp24ekpKEdZRdpp26dzB/BF/ar71mxK2nLgXfXocUMS3K3DxXRyMe/lOGJKzDxKdKa7ULSv8Q63Y8nuZfQPHsnjlL6y WUdfrB6hmQqxOn079iVNgaDe1tNm1fdV6nXa7wxVw/7dwPSmU89dCPNmRnl71uZ76 0ztq9pdL3wwWn3ruJOQya5kD1ln0cft87eAqrt5caSZN9dXnYYPSknCOg5kU7W 1yksm7skPC1 ebh/YsPBeswpCevQ9akcpCC3R4UXwvtFzRqqldzfqqm6I87yNVXb3KFh7u0xv5tvts6auZYvJm QvlQM1Y39U5KwjrXmoXpDh3c0dxqd1qKFmzNtXHC/5vX6n//tZepqydPi 4vF/u 2vIvv1x53fTB36SQl/1nuI9/Mbz2 FVS7utu3xqRQWmyvTA1QIP3N7Ua2sGNBn 9uln8lT7f7p4vxeNz1p7CuDxa6DpsigABTE9AHvFYgZYim3QzhTFn2Jmf5bAq6qvHlkRpOdW/YtJH5CLpXe/c4tnH38V4 aj 4l2rOmKr5s9bqr206Jo/EPb9svpbESg2H91Gw08jRgo/HQuMGBSvEfK6KMMnWM2YEcYVjazV36U4z2uWSVh4YpkZ14k2S1sz96ddZIU6TPl7YrPnX2wAAIABJREFUt1w/jP f5q2J0eFzWZ/aGWfm5HSYZ1jq1VP9TKsqVargkFLceQsxF/KmBd5eiTHattNUKrCl2jW58ndkbsfjaf4FEs Fy/3VcM5/6z7Nz6mvnLj80Ca3phk2ZRZs/7dwPSmU89dCPJm9L23WhLHh sO/rZ5471H1rJHpApB5 2L5uzUft8/fArE5Z977zJeFqqnGQZkm7S3VWE0bm5ccTzdzWjwrfkdgnu3foGtH8xVbPi6F8X7h73f5biLzX3/HgMEA/7Spm/yTV1zUxXjzj/NgwoaNFJTpXrsyQQ1Nz4o0fWyfmRqkdSE8xDHv1/98by9H01v0tPb Yq3/u90TXXy/9rzrQ01d06OxJsZs1KcPv6bNvdqrTcumataiqRpWdndKmoyK1tor474F0t/cbmQLOxb0 e5m VfydLt/uhSPJ15/Cun6YKHrsCkCCJCIpQ94qUC8GQnruOPPFlg bf6y8 cvmDWlVaFCNjNyVKggRyrwxPnz5ntzx0c69xZb8z4aGDRNXy ar UPd1TPsue0KHy1LtiaadBAM rWaSmMeFyuha25WrW0KWLzdm2zD1Dw6ihF1 morn5rzDy7p/Xn6/4wiS0znLh5sFql/M1qPzhHf3/kM61LqK72A2/WLS1rqUqF0sl2xxZ8rg/CD5sRCGafzJplSqdPz5AWoCMxY5K26Xlzl0MvrA0LvL3i4pSct65SWdkMQMtSTbfj8TT/AonHWCYPha rIS/crR45ZVoDUkd8ZeG94orC6P8uX08K6fx1OZ7MeoeitdmRyGvfRT28Mgl7ucJWfNw fzPb5svvF2Te sxSXoHJIx6dlzIKrJD1HdGz4r8cryf716zp9tDXzA1y ffCeL w2VK Ri2lUo63aKfvT2zmNXMbiy453uKdF/M3l NvqQxLhcDL68w3rY5ulnm2osyb5/33vF//8729HJWy4OnO 4uV/u 2sYvv1553fbCp8a0v6/0Kk/X9zBVa OMEhSePEwhQ9bZ99OCTf1G3Wlmvc646udNezmUXSH9zNfi8bFfQ57ub5V/J0 3 6VI8nnn9KZTrQ176EvsiUAIFsslIlUAFqux1Ape/7TRjWxvVTxnRYe6AN39AmnvpdOaMI0WbqeufOWMeCWUGLJQpkzltaNGmtgYMbqmJH6/R7IVn1LPLcoWvTpBfxz7qa 7Wd14sx5P6IciM8s2crzx/ VO0xVgzRKNWrUyieLWZTmBPgi6s2axKnV7QSP 9esokZc93PqWt5ik3tQc0T3vYxtZpv2jduQB1fuotjRmQ8aNVVKQj6e1di X2slr9smVVztHGx0/quPnnSg/SLvB4rMZf0Ntb6v/GMnmu4TgF1Gijdq3yP7jC6f uXk/KFNL562o8mbwvmpFzjlWlA1Lml87/9vCMEl33sXz Wur/VjXKqEzyHMpnFet4I8zwXnXevGdmvdvBcvxWQ3Jre8/19/XN5z 3PfX9Itb8jWXaLsN3X2dik9eZP8LSz/8C7c95v/7ne3tZ7M/uvb 43v8thmN5c4 8PtgCFTzsLr1ufpLijmvXxrVaOPVX/bJyht58u7q /HCoGbnt3uJee6Ufq6j7W9qXLFY/X7h6vrvHap7V6 L1JFP5V/J0u3 6FI nXn885/rgbndgPwS8TeDK9796W42pj/cLXNqtxUvNo4hNyrBTp4Zp9b38AC 7du7YnSWRucesSzBbNmiY98fHVO3bV50DkrRm9mKtj5ivjZdKK3RQNzOjasbFcjwmkZw8i9XpM5nmtTyjfXtTZ8J1v3kbmIdwVdBBbd28Rmt 91Gnzs3Vokt7lVu3Tqs2bNcuc1NiSEijlAOYJ4IePmb v7Zat848vuWgNm1yf bNrDUwo3GSByqkzvGVdYu8rXGtfMvtZTUo3yZq7njQ1dlNWheTeZhR1sIKPJ60Q7rmkzXCfF5jqf XVvPmdU0AJ7V65a4s53veIyu8/u/y9aSQzl9X48lgXDtMz38wRu/fc3Uev jKe8sVdAmu lg fy31f6u1LKuGDR3j8I9r965zGXdO2qWYXVnLsxx/1iIKZE3x9HeDwlPfL/bs0s5MDyA7v2uveVipmXXH/H1VObWqbvdnV96PCvr670Z7WdrF/fcXV/u/pXDc2Nj964Mr7etGQJl28SlbVU0799U9bzyjG82f/YmbN2tLtg/OcyUe99vLek1cicd6qXL3fHT1fHcjpORdCqh8t/unS/EU7vWnXDnHI6AvKt4xTcwVFk 5PlwhTF5GoMQIkIgtMU1dQip68aiWjftYv5rpTANC/qQRbdJvNara7RoFmx5/cNbPmnMkfYSP/Xikvpm 19yi1FA9e7g7P6yTb7kuGnxtoOybpuofv5inVVXspgFdsz4IwHI8peuqgePuxh0rteRQ pjYs t/1rQN dC wS3Uyseubb/9ojXxbdS5rY9sIe3U0RalH3/ZriQzvUKrVqmeNtWp4xg2dVDr1zvmFkxdknRo5nj9nN1DutwOMVCVKjmGz5iHee3JPBbY7UKddnStfMvtZTm0Wuo3tI2Zbu gfv14qnZl qPKfnqL1u9O77cFH09qBVzzsVxdqztY7P NBw5MnkZj769fatLOzH hJujY nBNX MY/ufOUoj938XriQrr/HU1HmfWM4e1LTpG2/eeSv7Cy6sXF30sn78W 79V45bXdjWPZErUyl/ p/TTxa7jc6dpXqb5YR1lW47fOaBzUZr45gd6y/z8vDHraFursWfYvpj6W6 zh75fnF6myeHH07/8urhfU35ZbR5CGagePVqmV9Pt/uza 1HBXv tt5a1PfLw/uJi/7cWj/Wt3b8 uNa 1iM6qei1exWb Tvus4d0wDFcu6yZPiPbmQlciScP7WW5Iq7EY7lQc7eKm58vXD3f3QgpeZcCKt/t/uliPIV5/alVt7ZKmUlftm7ae VBB 5cH7b/qL/dcLduuuEJjd/qbkOyHwIIZCeQz/dKZXcI1iFQsALRM/6rj8zt/3EnD2vHpmjtj01SQMMwPfvC4IyP3arZTw MWqinJ6zW w8 p XdQlSz1DFtXL5S0Sf81PiWezU87wNiTWX91GlwT1ULn65j5gNsjet7q112Z5rleJqqb796mvJdtP776PPaEnqVyp/drdUr4lT/6sravy5zssmie0CwzLMLtHzbLsV1Hqh2AY79Q9S5wwXNXWz Um3YW62chvVeNXioWk/9Qqs elZPRoWqtZlf6/SONVqwOkmtO9XWilUHLQaQ0 b an9Na/lFrtfkMe/qfP8Q1Qn0M394VFFI/45q6PygkJyKyHW9i Vbbq9cD5rti9WGPKDRUa/ovQXf6eE7Vqlbt2DVNbfYnz28U2siN6nho9 qTaOUTwuFEM/lIF30ORGt asPpCTaErXpqGPv09q6cIFKpz7/p2ZL9W baY6ObCWyW2mx/9ccoKdHb9JTYyP1xUOPaGm3TmptMO1njygmKkpRe2MV/EAHDemQ3bGuvK7w r L15NCO39djMeZ8ECkxn86S2fa3ad 3RukTRdzZeVctkiM1q8fROjydz7HtDX5O5oYTXtvnFYk71ZfAx69Tq2Tr2OFubjoY/n8tdj/LVa5VKsb9GCfSI2ZO1lPPbBDoZ0aqdzpzVqw8Lgq1fFT3IFMBVqO32n/ INau2CZNplVF695WDeEZJsBsViD1M2Lp787lfXE9wtb7Ura/ 9n9di6ULWtckF71qzQit0Jqhz6gEZ1cP5DyN3 7OL7UQFf/91pLyv7uP/ 4mL/txKMO9u6fX1wsX0tx3RAs954VeF QWrXprHq1qok/wtHtGlJpDaeCVDzuwaprdMcyOnFuxaP1ltSKuxWO1VMm989H18916RI49Cqx8N/uny/EU4vWnTI9BGvD5as387i09c8x8FqsWYGaaqKbON4WpuWOwbIbFjetDYrxik6eXMenebEeNZz4GvyOAgKsC2aWHXN2X7RDwCIGDayJ0yMdPZcpXVM0mXXR9aJiGD2qrmlk gPup e2v6sNak/XNtEhtmDfTfGAvraoN2 uGu27SrQOD0p4InNeKlWrVU71rT9ekg7XVb0AL52dcOBVtNR6bmt7 rJ4//7kmzNuiZRGHVb1pO1035g6FRD6vNXlNxKqqmXqgqrTtuFp1bqfLuTN/dewSolKLf1f5kOAM85ba6gzUqx/46 vPZyhyRbgmJ5ZRravaadQ7o9Rl81smEZtXxfT9qw5 WK eHK9vIjZq oQ1ik90ZF1a6tEe ZGINaO7XCrfanu5UX9bNfV 4V3V6/ybJs9cqfWmjy5L8FelmnXVcthfdX2GD7KFEE9KFVzy2b1A/34vQhlvbD6ouZ M09xUih6P5yERa7X/21S772h90mCBJv9kHp63YYmmLkuQb2Bl1agbrKH3dFZYz8zTarjeZoXZ/127nhTe etaPK5burXlpUP6PXyBVmbY ajWm3WXl9Zq9UBRJGIl13ysnr9W 79V1UCFPvWGXq87URNnR2nBtC0qV7eFwp55RS1XP6MxmROxJp3u9vvpuXMp14nKqlkj//8MLZ7 VtvLbO B7xe25iP19n27NW7CQk1bfE4 lesp9Jbrdd/t15i/MJwX9/uzS 9H5q ugrz u9FalnbJy/uLa/3fUjhubOz 9cG19rUaUj2F3TFCias2acumVdqw5Lxs5c31p0E33fnQcA0PrZfjtDmuxJOX9rJaE1fisVqm40l87ny cP18tx6RY4 CK9 9/ul6PIV4/Qloo/vf/Jvs437Vkjm/aX2C4/NRC1Ucml0i1tW/T9xrL/ZCAAFrAraJA5KfG8mCQL4KtH4763PfB/S7KfkYsyMm5euxPLKwU/P03C2fal3QbRo/brhqeWSQBIUAAsVCwNOuJ54Wj6c1Ij65tsjp/43RyI/Wy /qe/XVewPM2J18XvDPZ1AXijswRQ/c8a1293pSM1 8xoUd2KTABOj/BUZLwSkCBX2 F3T5VhvS0 KxGr/z9l5wfcgtn5D6mqtEYzt85uqmbIdAvgswR2y k1IgAkmKnjxNaxN91WFob5KwdAgEEMiDgKddTzwtnjzQFsiu OTOmqB1a7eauexqaNjdffM/CWse6sj7b 4twKveLED/9 bWpW4I5E2A60Pe/NgbgfwVyP97wvI3PkpDoPgInNis/4Vv0dE/1ml2 B y1RqkW/pULD7xEykCCHiOgKddTzwtHs9pqcuR4ONai9i3ae26iypzzZ81Mjgf54bF3zV/tvJOAfq/d7YrtUIgPwS4PuSHImUgkO8CJGLznZQCS6zAsbX68YspOupXXnXbDNIDj9 ukDw/SKrEalJxBEq2gKddTzwtHk/rHfi41iK2ED3 8yQ97trWrm Fv tWbOl9AvR/72tTaoRAfglwfcgvScpBIF8FmCM2XzkpLFWgxM8RS1dAAAEEEEAAAQQQQAABBBBAAIF8EWCO2HxhpBAPEGCOWA9oBEJAAAEEEEAAAQQQQAABBBBAAAEEEEAAAe8WIBHr3e1L7RBAAAEEEEAAAQQQQAABBBBAAAEEEEDAAwRIxHpAIxACAggggAACCCCAAAIIIIAAAggggAACCHi3AIlY725faocAAggggAACCCCAAAIIIIAAAggggAACHiBAItYDGoEQEEAAAQQQQAABBBBAAAEEEEAAAQQQQMC7BUjEenf7UjsEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8AABErEe0AiEgAACCCCAAAIIIIAAAggggAACCCCAAALeLUAi1rvbl9ohgAACCCCAAAIIIIAAAggggAACCCCAgAcIkIj1gEYgBAQQQAABBBBAAAEEEEAAAQQQQAABBBDwbgESsd7dvtQOAQQQQAABBBBAAAEEEEAAAQQQQAABBDxAgESsBzQCISCAAAIIIIAAAggggAACCCCAAAIIIICAdwuQiPXu9qV2CCCAAAIIIIAAAggggAACCCCAAAIIIOABAiRiPaARCAEBBBBAAAEEEEAAAQQQQAABBBBAAAEEvFuARKx3ty 1QwABBBBAAAEEEEAAAQQQQAABBBBAAAEPECAR6wGNQAgIIIAAAggggAACCCCAAAIIIIAAAggg4N0CJGK9u32pHQIIIIAAAggggAACCCCAAAIIIIAAAgh4gACJWA9oBEJAAAEEEEAAAQQQQAABBBBAAAEEEEAAAe8WIBHr3e1L7RBAAAEEEEAAAQQQQAABBBBAAAEEEEDAAwRIxHpAIxACAggggAACCCCAAAIIIIAAAggggAACCHi3AIlY725faocAAggggAACCCCAAAIIIIAAAggggAACHiBAItYDGoEQEEAAAQQQQAABBBBAAAEEEEAAAQQQQMC7BUjEenf7UjsEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8AABErEe0AiEgAACCCCAAAIIIIAAAggggAACCCCAAALeLUAi1rvbl9ohgAACCCCAAAIIIIAAAggggAACCCCAgAcIkIj1gEYgBAQQQAABBBBAAAEEEEAAAQQQQAABBBDwbgESsd7dvtQOAQQQQAABBBBAAAEEEEAAAQQQQAABBDxAgESsBzQCISCAAAIIIIAAAggggAACCCCAAAIIIICAdwuQiPXu9qV2CCCAAAIIIIAAAggggAACCCCAAAIIIOABAiRiPaARCKE4CCQo/KWbNKDfy5p2oiDiLejyCyJmyixSgaPT9Vg/0yf/vkhJRRpI0R98xXujzLn5mCbuLqpYiv/5m3R4rSaOeV53jvyLhjj6lfl5OfxCPoFe2efYLy8nHzP95159ujGfDn FYoq /1whQK97 cr9weuqTIUQQAABBBBAAAEEEEgR8EUCgeInsFEf3fCaZsSF6tUZj6urLacarNc/h4/R7MSeGvPbI qc43Y57e/u qP68cEH9eX2a/RSxJPq4W4xxWQ/ 5mdCv9pmiKWb9auw2d0oVR51WraSt36DdGNA5qpYsrXPav/eYdenBmXXiubr0oHVlKdJi3VbfCfdGOvBirjVOeNn9yvJ389oTYP/5/e 1OlDBrnw/ h4e/9rgpDX9akx9okv5a6zukAKuVXWhVr1Fdw5x664eb CqmSH989laz2td4N8bFuVtR7HNGUt97TN1vKqmW//upXr7x8zfWyzlV hRZYYPvhenz0qeTjHVgwUT/9XmiH5kB5EihB5/v5A4qcPkvhS6K0eddRxdrLqnrtRuo45EbdNqSFKvvkCZKdEUAAAQQQQAABBEqIAInYEtLQ3lXNuqpf39Ro0xEdOmb rZ5D7WKP6PA581qTOqqf5ySsrzrfN0bv31xWdSrkcLw8rS7o8vMUXI47J yJ0OvP/J9WnrCpQsNWat rpsolndG zVGa9M/fFVt9oh7vmHH3Gm3D1KmcSadEEnDu7UhnWL9M3a5Vqy7UV9eH rDMnYHA cywu 9dtrQNuqZgu7EuJidXjHRkXoUil0TrlU8fVdeKuezMSwi4JVA8z9 0qp5dr5WbE2TrcLPefLqvyrplkNtOV/YJaNRBgxpdLmPjrp9MIrakj/POzbO4v3bl/uCJNfz9sxf19 nxqhzUUm16Bsv/3AGtXxml3/5tzp Y5/WfJ9oVwLnjiRLEhAACCCCAAAIIIJAXARKxedFj3yISqGwSsSZV4EjEHjYh5JSIPXxUjpf96tdVzTxHalOlhi2UcVxmngt1KqCgy8/PWFPKurhdX732uUnCllOH 1/WSzcGOX0IjdeB5TO1OZukZ6P d nR/qVTCrHr7PqJGv3sb9r981eaNnSsRtbNW6wBIYP06GNXOxUSq/mvP6a3Fy/W97NHquuf894b8hYhe3ufQDE8f50b4fhJOWZcCahauYASScXcx/s6bBHXqHj2h/LNB qpwQMV1qyiUge/Ju6dotH3f6ttM2doyV/bqX 5Iqbl8AgggAACCCCAAAIeL0Ai1uObiACzE6hfv45ZvUOHD1 UQvylw7/pkVETFK2Gumv8WN1sknn2w0d01GxVr0FdOd QfuCHZ3XXFzvV/YUf9ESd fryqxlavuWQzqqcagS10c2jH1E/x4hbs yeMFr3T9znFEILPfTjGF1XJXNUFzTz dv14Wrn9ZF6w8x5mL601KOTX9MQp Sk6 WbUk7M0uiRX2hTl4c06R5p4mfTtNgRt62igroM1oOPDFOL8pniSjquVd9P0IRZUdp9Iknl6gar31/uVvPIpzQmvKpG/d9Hur1R5rq49vvpeZM0dd8lBXS6Xc9kSMI69g9Qna7D5Wil3BebyrcZoaGtftO4qD3avDleqhuQ y6WXw1U6xDTIRZv1YkTjluf3UnEute ZsIE7ZrzsyZOjdSG3ccVZy jao1aKHTYjbp1QJAyN5flqiXvcElHlv oz76ep3V7Y2WrVFdtw4br3ttDVS8LpdV4XN3eXR LNU48qhXffaNvwh39OVHl6gQrbNRdapljMXad3jpX3/8wV5Eb9 noObvKVq2nkB6DNGpULzVJS5rs09d3j9Z3RzrrhUlP61rnOTIcZSes1ts3vaP55YbqX9/coeYpI wtnb9pMZ5TzNxpmjRjlTbsPKxTCX6qXLO WoX21ojre6tFJefh 67GnyNAzi kXk ctwh/WwPC01d0fnqixqR9aXJOO ZHKGLpWkVFH9TRE2d00ae8ajQOVrdBIzQym/7snk/OIWd9xaKP5f6T9YhFv8ZK/3H1/DW1svT 4t75bqk/WIonY/y/vdFL5q CtGXLZw/q8cnnNOSdr/Voe cWtNZ/mg0aqWaZOoBvgxAz5Y207chZnXXMvEMiNpMQvyKAAAIIIIAAAghkFiARm1mE34uFQE2TiPU3idhDB4 YeOspMTpGu5Ij36fobZeTeccOHVWiScHWr1872zpd2jVFz7//kw7UaKHWnevLdvqwtm9ZqY2HlJaIrd79Nj1T1zG/QZI2TvpEM2KyLcqs9NPVIx/RM30dr8dqxfjxWnioiYY/N9jpg1sltch0z6/r5Tsd9/hCvfnkLp0K7qjufZto/ rlWjtvgl5MqKKvXwl1Su6d04oPX9bfZx1VaXO7ft8RZg7WU9Ga9483FFnrUk4VcXF9vFaYefISzbigLv1C8zhSuJRsybknm3x882MO10xVsJ/U6jV7zEp/NW3q7nBbd9o3UdETX9NTE2KUWKWpeg7sqhq2E9qweKl HrtOv//xij66u4VJWedxiflZL7x TuVCQ3VdJ5sOrlmqxT9 qE274jXuzTDVSCveajxWtnfHx2q9z2jJuy/pjfknVK5xZw3oVUc xzZr3juva3mN7PqzXYfnfqgn312mE4GN1aVbH/UIvKQTMVFaMnmc6RP79c6/Rqll8uDs goLa6jvvl6rBcvO69o GTOx8SuXKtJcBuoM65GWhHXsZfn8tR/Xwnf rnfnmrH61a5St14DVTdQOnNwh1b/8qniG/bQq31S52W1Er9VS7N9 Ta67blHlDwr69EV vyLlYptPUxPDGmUVlj1ls5zxO7T7E /VbhfU7Vp0Vata1VSQPwp7Vy7UpPGrtHK/a/o3/e0yJAAs xjqRpWfaz2H0vBFM7GlvqPlfPXKXyX3l/cO9/d6g8uxeMOv9X k/0xzqyeqyXmzxDfqzqrc05352S/K2sRQAABBBBAAAEESqgAidgS2vDFvdo2M92AI6V22Ew/4EjE7jKJ2IQqzRTsF63o6N1SWHMdOuRI0tZQ/QbZd/M1v8xW8O3/0MSR6bfUJ53cqT2J6TrlgjqoT5Dj9wQlzc8tEeuj2lf31OWU71Ed 9mRiK2ukD49c31Yl vlO7XYjhj5PTZW44bWUHLNznfTe3e8pTlL52vZ2VD1Txlmad/6iz42SVg1Hq6xH9 mpilDhG7q8J7u/Ydj0oa8LHsUE NIftVTkyZ5SyXG75ip8E2mKL8Watcq7w8Hit8coU8/WWsKdMwRe1oHNq/Tuj9KqenAv r MHfHoLrRvkfC9ck3MYoP7KTnPn1avaukjHQc1VVv32dGV/7wuab0N1Mx1MtLO5h9Dx9X9Yc/1Dt/qmFS2Wa5a6h fepx/WflBH29vLue7prS8FbjsbS9Gz4Wq520frLGmSRsqWYj9cFHN ryaW3XTe3f0X3vrcla2tEIjf3nMsU2u1EfvmNGsqV9CZKkW6a8oYfHTdMnU8L08c2Xx23XD uuJl9/q1ULViiuTy nW/QvasX81WZsc21dH5Z8MUhbrJ6/x2Z qvdNEtY35FZ9 PYINXY6dZJObND6U05fRFiMPyvAFdb411GHPilj1ncf0ncmERtXu5X69OmQw451NXTMON3TrIZKOw/avXS9fnrsCX0xeZLm3fCyBjrN32LVJ4cDZ7/aoo/l/pP9UYt0raX Y n8daqWS 8v7p3vbvUHl Jxo1ks9p sR7DrxMqvzJdgc3SkWmc99dJ15t2QBQEEEEAAAQQQQACBKwsUwPCzKx ULRDIs0Bt88Auk4WMM6NezyrOJF9NciO4n64L9tfRbTE6aRKnhw ZsV42s10OgyATGw7WY05JWEdMPpWDFOTpo1qq9NTNQ1KSsI6gy7RT9w4m2XZpv/buT5fdsmCpjpgRqx1GDEtLwjperdxrmMIcz7LK0xKrM6cdBVRQRed5YA9F6suP/qt/pf78uN60T8Zld/hXl1//58d64/mndcfDPyraVlu9n/ibBqcP33Q7usQ9KzXl1xnmZ6amz16mtfsuqvrVPTSwf2vVKsQr3vGlkdpictW1B45Qr9QkbDJZR90ytIHJE /RosUH3a5n2o7lu rGQSlJWMfKUjU0 IZrzEPPzmnp4vUmHX15sRqP1e3zXpHcS9i8ONLMY qrTsMHpSRhHdvbVK3vdQrLMlWImVZk5iytv1hGXa8foJoJsTp9OvUnToGh3dTSZtf2VeuV3I0dS53u6t3CZmYhWKqlsakrzb8XVmtB5AVuMaVxAAAgAElEQVTzhUYPhTV2Wm/5fw8pYlqU4s2EHSMe/lOGJKyjKJ8qrdUuKP2x65bjtxyP1R0C1bB5ahI2SfHnYnXq5CmdPFVGzVqZEzdxu7bmeMeA1WNdeXurPlb7z5UjKOwtrPUft89fF99fCq32BRSP1f6Tub6nV32up/4 U/uqdtcLH4xW3zrp527mbfkdAQQQQAABBBBAAAFngeyHCmKEgKcL NRRPcfwU/O0rkOK0fbtdgWNbKG2/mbE2pfmd/vVZrSsSUHVMInYHAZsNuja0YU5TD0Qol491XcekWZCrFSpgvnvecWdT403Trt2HTe/1NRVVzlec1pKNVRQI/O742W3F3tagi9DKCejNfd/ETqWWm6LWrp1ZJsMc6EeiZqn6VHpB/at3l5/e220RlyVQ0NZjLHcoBf1y2jHw7rsuhh7QgejV vHTyfo46dXK a1sXq8S FM4rc3OStuU9BVjS PVHWqR8OmjUxKca/27nFsk/3UGS5Xu55pT cJEc2OAU0amRHji7XDlH9EHZNnxbUaj9XtXY7XrQ3PGauTZs aahyUqf1KNVZTR4LU8bSptOWCtm69PLfz/Lfu0/ycjnni8kOqLn XUE29zUj6L7Zu0IIlseo3yMwZYJa4ZUu1ysx2clVYj7yNeEuM0badpsDAlmrX5ErfCLgTf06VzL/1F/Yt1w/j/6d5a2J0 FxSloLjzBy8jj5f8ItVH6v9x/0aHIv8WT uSp7wIW0pf/VQ3dHDnbmpnQqx1H sn 9pR3Lp/cV9H8t7Fkg8VvtPpqgvbdaEseH6w7 tnnjvUfWsURh93rIcOyCAAAIIIIAAAgh4qACJWA9tGMK6kkBtM WASWZEHtWh/TGKjq2gVsG1VNW/mapfWKPoPUdNItaU0apujsmTmjU9fehrDgZlSpvRjpkXxwdBkwRJHf5okrLnHQ8OMSnQwEx5WDOE1qzL6 gdMxLWUe7xszpzxvybOio2 C/6NuIvZs7J6Xrs1vHamjlM83vqA4Ds8bHa /t0/fu9n/Wf5z9QhU eVR nD7S2yxPHZlOC86rcPgDb5B9YVQ07DNDTr8Rq5z0/atb/TdeILn82j3Qr OX8eTOKUqVVoUI2l9kKFcxYYpM7PH/ezD5sRkPmJZwKpo0z72/WJTe7icERRfL/WozH6vaZQ8jf3y Y B0lmrpmqWx2/TlO55KHYtfVkBfuVg/nUdvOgQXUUC2n36v16qHW/9mqtQsidWZQP2N4Xsvmr9VFW1OF9Xbe0o3axZmYHOdnlcrKZgBvpgLdi9 NqFzexX5wjv7 yGdal1Bd7QferFta1lKVCqWT6xBZ/rg/DDSkpyTFeSp97sYjxWfaz2HxfDyGaz01sWadq0AxleqeYTmvdErKX Y/18TwvYpfeXbCpeUKsKJB6r/SdT5Q5Fa7Pji5/2XdSDJGxBtTzlIoAAAggggAACXiuQTYbAa tKxbxKwNc8hMvcDrv0iPYts2tPqat0o Nxxr5mnlj/37Rt9R5dMInIauahXlmTlpchfH29ufuXUZnkOTHPKtaRKM1wy/8FxcZmHc1mrXs0MHPDmiTo8YPauSvBPOvI tyutgBzq3PXm/XKE4d0z tLNe7jxer4es 0nK6fXy7tk5Jw9vdz7bi2Bi0UbBJ4u/bGaIcZ3dgwfwbf5kpWxiQQHP5nzjgmHc5UF5O9dtz97l mTN7TVmdMG5uyMlTJrHM0u8qVTZvr1Go8VrfPFSPPLzr1Z0dlM/Tn88Y4c38uq3LJ0wHHKaBGGzP3sIsBVO6q3u2 1Pq15oFnp/ppiO8KzV dIFurHuqVxwGNKmticnxvcPxk8mD0 rmG5Gb8uZaZtxe3TvtF684FqPNTb2nMAKeJYE2xUY6pGwp1sepjtf 4X5kmd32k2Xe5v3 Oe1rqP brtsK6/uQYcCG/kPqdnD39bo3UCM5f/hbHKSCr/SdTXS5e1EXHqtIB5qs2FgQQQAABBBBAAAEErAlc6f5Ia6WxNQKFKFAvefLXI1q2yDyVvvFVCnZ8IjKJ2BZNzdyPi1bIMSC2fk4TxBZonKVUKnlQWJIZIVagB8ql8LJq3NgxEewxM22D84SXZpV9t3buzmVXl14qrU7dWpv0YoJWz1 RZR5Yl4pI2ahCj9t0c7CPzi3/Qd9vSn9SWoUKl4c Xh6ZmbHEc2Z0mGMJNCM/XVrsZtoGR67InqgEp4exubRvlo1ca98GDRyPbrFr547d6QOVU8raY9aZ9LUaNMyHx7vs262Y5KxA hK/c4/ ML WNTFUS1ltNR6r26cf3TWfjBFf6beyatjQMY70uHbvOpdx46RditmVef/Sat7ccX04qdUrd2Xxz7x1 u B6hHWVr7m1uMFC0/qzOKlWptYSlf36ebCKNacS01 xbeJmpuZU3R2k9YlP gut8Xd HMrMy vmSfMH3ZMOFJbrVtnTMJKB7VpU9pMu3k5SNq 5co5vj67qHjzpUn2i1Ufq/0n 6MW6VpL/cdcWwrr qOCON/dkDaJ5 Sk6Okz6fM JxdzRvv2Zp6p3Gr/yRRP7TA9/8EYvX/P1Xn/Is2NqrILAggggAACCCCAQPEWIBFbvNuvREdfxox2rWbGAkZvO6qKwc1SZtqsrJYtq nk1u0mRRtopi/Ich9zIZgFmjlbHcNzzMOz9qTNFVAIx814iOBeoWbgYJLW/PqbYhxZv5Tl9OKZmp82iav7YVXue5MG17YpbukE/XPmfvMQovTFnpCQnGh0bamuIbf1MLeBH9X0r akzS9bs1VzOVLJMfPnartz4fF7NXue46lAgaatXZlfNUH7p83WyuTMpxkxnecpYl1r36rdrlGwucIenPWz5hxJz8jbj0fqm l7zVSaDdWzhyvxX0HxXKR nnkkPdmYcEBTJ0eam rLq/u1rdNm7LQaj9Xt06N0zecKtcrycstru5rzPVErf/mfdqb1B7uOz52meRnmh728a OBA9XKDJjeuXmpS Q0q5CTq2PlzT12T6ksLRq7r3UEd/uzYsmK0pCzYoyTdEvXtmTj5mCc FFbXUb2gb ZvE5a8fT9WuTElGktWr87vZ 4G78LgbixiU116jiGIR/U vWOuXpTlyQdmjlePztOx3xcatWtbdJ757V1094ck hWfaz2n3ysTj4VZa3/uH/ Wg23YM53q1GodF01cMw2tGOllhxKf989u/5nTduQtTSr/SdDCWcOa1u0mYt 7ykL73NZY2ANAggggAACCCCAQMkUyOXe35IJQq2LkYAZ7eq4vfeYSTW1CG6aFnhTk5T1tS8zKRvzeu73/ Ze2RPR5rbkAykftBK16ahj89PaunCBSqcm82q2VP 2Ge6TNtv4q/01reUXuV6Tx7yr8/1DVCfQzyQWqiikf0c1TH2wktvl5x526qu2Ftfr4YHL9fdZv rpB/5Qvx6NVObUNs2fc0w1g/wU63hwUF6WgBa699U7te Z8Vr6z6d1x9QQXd2smvzOH1P071HabdqlSr1aLt26WbrL9bq 6SKNj/pF3/0epkfb 5vbwa/Tvd2X6d0lUzT6rs3q1K6BmbYgVrvXrtXmowmq2PkejWyXdT7K I0z9a PVpqa2ZVw7oyO7Y3W phTSvStreseHJIP88O62L41mBUQv19ITVev/B57S8W4hqljqmjctXKvqEnxrfcq G58OAWNWsqqP/eU6Pbuyuq6td1L7fV2r5zouqeM19uqOz09QNVuOxun1aX3LRx2LfK9XqBj3YJ1Jj5k7WUw/sUGinRip32jFy9bgq1fFTXMZpOc1zvczcwKM36amxkfrioUe0tFsnta5bXvazRxQTFaWovbEKfqCDhnTIFEjZTurdJUCRpt/9YEuSX ce6p5lnmWzjxvnb7UhD2h01Ct6b8F3eviOVerWLVgmJJ09vFNrIjep4aPfqk2jlD7tbvwWXV3d/KrBQ9V66hda9dGzejIqVK1r ej0jjVasDpJrTvV1opVBzMW5YZPagFlegzSgM9Xa Z3b mZY ZY1QLM1aSaOt8Upuapc81Y9LHcf1yFKcTtrPWfQrr eMj7ndRUffvV05TvovXfR5/XltCrVP7sbq1eEaf6V1fW/nWZvvmw2H8yNPOBSI3/dJbOtLtP/bo3kGsT5BRiR FQCCCAAAIIIIAAAh4tQCLWo5uH4HIVKG8SrZWltSfrKzg4fSZYP5OIbapl2pryeq5l5Pbi7gXmQVIRyngj9EHN/WSc5qbu1 PxbBKxUtXBD vVk P1TcRGTZ wRvGJjhE6LfVoD6dEbB7Kzy3s9NfKqcvjYzSm5gRNmLVO039Yr/L1WmrA8y qycLH9OZOP/mnJoVdKzDLVgFBg/XW/zXVzJ9 U8TyLVoxZ4MS/MqrVuOuGjl4mG7o19SMy3Rlqa0/3dZNk19botlfzdJN7a8zI5yrKOyVf6p xC a MtyRS2IMWPkSpvkbisNH3WTbh14lSpm86yuxH2/a/q y8cs5VtagdVqqU2/vhpw4zD1CkqeODfPi0vtaz6eN7/9VX1Ya7K mRapDfNmaoWJv2rD9rrhLkf8QRnndXU3qiY36K2HDuo/4 frtyVnZatcV91G3qd7/ IYQeq8WI3H6vbpx3LNx2qFAxX61Bt6ve5ETZwdpQXTtqhc3RYKe YVtVz9jMZkTsSa1F3tvqP1SYMFmvzTfC3fsERTlyXIN7CyatQN1tB7Oiss25GuAerap5PKLF6i83Y/XRPWRdkOonbn/LVVU 8X3lW9zr9p8syVWm/6xLIEf1WqWVcth/1V13dwfkt2N36rrq5tb6szUK9 4K vP5 hyBXhmpxYRrWuaqdR74xSl81vmURspnLc8UktIqCN7n/zb7KP 1VL5vym9QmO62cLVRzqlIi13L5W 49rLoW6laX 4/75a7VOLp3veekPLgVkU9Pbn9Xz5z/XhHlbtCzisKo3bafrxtyhkMjntSZzItZy/3EpCDZCAAEEEEAAAQQQQOCKAraJA8KL7t7pK4bHBsVVoPXbWZ8LPqDfTcnVmR0xqbhWy0viPqOpo /RJ5s66NmpzymMp414SbtSDQQQQAABBBBAAAEEEEDAOwVyyyekvuZqzcd2 MzVTdkOgXwXYI7YfCelQAQ8R BC7DkzRUPG5dLZqz2Tw7qPXVakcS1nMai0gQQAABBBBAAAEEEEAAAQQQQMCrBZiawKubl8qVdIHo8aP12rp6uqbDVWpYs5wSju/UsllLtcOnoW67N0xmZgcWBBBAAAEEEEAAAQQQQAABBBBAAIFCECARWwjIHAKBohKo2b6n2u9dqw3zZ2pRbLxs5aqqYZshenLUjerfNI8TxBZVpTguAggggAACCCCAAAIIIIAAAgggUAwFSMQWw0YjZARcFagZepteND8sCCCAAAIIIIAAAggggAACCCCAAAJFK8AcsUXrz9ERQAABBBBAAAEEEEAAAQQQQAABBBBAoAQIkIgtAY1MFRFAAAEEEEAAAQQQQAABBBBAAAEEEECgaAVIxBatP0dHAAEEEEAAAQQQQAABBBBAAAEEEEAAgRIgQCK2BDQyVUQAAQQQQAABBBBAAAEEEEAAAQQQQACBohUgEVu0/hwdAQQQQAABBBBAAAEEEEAAAQQQQAABBEqAAInYEtDIVBEBBBBAAAEEEEAAAQQQQAABBBBAAAEEilaARGzR nN0BBBAAAEEEEAAAQQQQAABBBBAAAEEECgBAiRiS0AjU0UEEEAAAQQQQAABBBBAAAEEEEAAAQQQKFoBErFF68/REUAAAQQQQAABBBBAAAEEEEAAAQQQQKAECJCILQGNTBURQAABBBBAAAEEEEAAAQQQQAABBBBAoGgFSMQWrT9HRwABBBBAAAEEEEAAAQQQQAABBBBAAIESIEAitgQ0MlVEAAEEEEAAAQQQQAABBBBAAAEEEEAAgaIVIBFbtP4cHQEEEEAAAQQQQAABBBBAAAEEEEAAAQRKgACJ2BLQyFQRAQQQQAABBBBAAAEEEEAAAQQQQAABBIpWgERs0fpzdAQQQAABBBBAAAEEEEAAAQQQQAABBBAoAQIkYktAI1NFBBBAAAEEEEAAAQQQQAABBBBAAAEEEChaARKxRevP0RFAAAEEEEAAAQQQQAABBBBAAAEEEECgBAiQiC0BjUwVEUAAAQQQQAABBBBAAAEEEEAAAQQQQKBoBUjEFq0/R0cAAQQQQAABBBBAAAEEEEAAAQQQQACBEiBAIrYENDJVRAABBBBAAAEEEEAAAQQQQAABBBBAAIGiFSARW7T HB0BBBBAAAEEEEAAAQQQQAABBBBAAAEESoAAidgS0MhUEQEEEEAAAQQQQAABBBBAAAEEEEAAAQSKVoBEbNH6c3QEEEAAAQQQQAABBBBAAAEEEEAAAQQQKAECJGJLQCNTRQQQQAABBBBAAAEEEEAAAQQQQAABBBAoWgHfoj08R0cAAQQQQAABBBBAAAEECl/g1LBRhX/QfDxipdycfSKAoBBBBAAAEECkOAEbGFocwxEEAAAQQQQAABBBBAAAEEEEAAAQQQQKBEC5CILdHNT URQAABBBBAAAEEEEAAAQQQQAABBBBAoDAESMQWhjLHQAABBBBAAAEEEEAAAQQQQAABBBBAAIESLUAitkQ3P5VHAAEEEEAAAQQQQAABBBBAAAEEEEAAgcIQIBFbGMocAwEEEEDAawROL3hfN/S7Sdc9OVNHsq3VSc147nYN6He7Xpp9ItstWIkAAgggUDwF/J78So6HZFX69QX5V85Uh a3qoLjtZdCi2fliBoBBBBAAAEEClyARGyBE3MABBBAAAFvEqjY607d1S5A8et/0ueLzmap2rnl3 rrNRfk3 rPeqh/lSyvswIBBBBAwAsEfFsqYGA9L6gIVUAAAQQQQACBwhQgEVuY2hwLAQQQQMALBKpqyCM3qZnvWS3874/aeNGpSok79O1ni3SqVAONfHSwatu8oLpUAQEEEEAgk0CC7OcS5DOwv3x9wUEAAQQQQAABBFwX4E8H163YEgEEEECgJApcOqfdKxdr9qxNqnHnkxrRSLLVH6pHbpivR3 M0H8mD9C/b60nR871jylfaeofUp3r79PIIJ9MWnad3jpX3/8wV5Eb9 noObvKVq2nkB6DNGpULzUplxk3XvuXTtd3vyzRxr1HdSLOpnKVqql cGuF3fhnDW6RssOhCL398V41G9RHfa5ppIqZD5u5WH5HAAEEEHBNoFQ5 XToJv/ LXVp4keK35u6W4IS5qyW35 6KyD0RyUuPHeF8krLp/dwlR7aWb4Nqshmu6BLe7cpYcavujBnt ype9cMU9n76yspfIEurtoje9IViuVlBBBAAAEEECh2AiRii12TETACCCCAQMEL2HX wEYtmDVPs8JXaOvxBMmvif56T qRfdRs1L0aNO81zfhhvCIGvqT Pkv032 ilVillx66o4X8MgRp1 G5H rJd5fpRGBjdenWRz0CL lETJSWTB6n1Wv2651/jVLL0uk7HZ7xnh75IEqJ1YPVvVcH1SqbpFOH/1D02nBNbdAnPRHrY9fxdbP02YpZ qJyY3Xt10cDB3ZXh/rlkpPDLAgggAACVgRsstVuKbvRTQt6N8qpirecIunR fqYw14brYuacChl2rUgtn6FKOh/CVzy0vqvytjWU7GaOLESt0yV5FvqHXKOCxNvKt8w dnRB9ORmbZFOptv3k36mfypzarYR5CxQfsUyJNyLJ0XEEAAAQQQQKB4CZCILV7tRbQIIIAAAgUpEH9cm5bM16yZ87Ro/VFdsPupWnAnjTQjVvv1aqv65Z0OXjpEdz8QqiWvL9WXXyxTWb9vFHmunLo/drs6ls0U5NEIjf3nMsU2u1EfvjNSzdJeT9ItU97Qw Om6ZMpYfr45jopOx7VwulRirMF6 GPX9cw56lmE8/o4En/9ANU7693f2qttQsXKiJ8kZb 9LkW/zRB1Vtdo/6DwjTg2paqWZqUbEF2G8pGAAEvEPB3JEd7yr/ftfILqW5GrSbo0rY1uvDDYl1ctEHm5oiMi3234qdvV8C9/RTQdKbO70gb15pxu p9VOZmk4SNXaO4xz7UxZMp2/2wQmU/Hi3/GU/9wXFG/uptCxuTp7 yb5du8u/z7d5Xf9nebnVl3askoXHaNkl2zVpQs5HMcLmoAqIIAAAgggUBIESMSWhFamjggggAACuQgk6eT2VZpjkq z5q3TfjNlQECNFgq95Xr169dN7eqVzXFkaWCPO3R3x9/1YcS/9JaSVLrdffpb7wpZjrV75iytv1hGva8foJoJsTp9On2TwNBuavnJRq1ZtV6nTSK2YvJLSUpKviXVR76ZpxrwraDa1TMewla2ttoPutn8jDQjeTdpUYRJys6J1HdjF m7T2rq6l5hGjiot0JbVM40UjdLqKxAAAEESpCAj2xN25vkqxn9em0blSpnk/1otBImTdPFeSuU EfuI1EvRYQrYdRD8h92tS58sDZ9igEnwVLXmOkIzFM5Ls0xZaYmYR2vx/6u Fn75X9rA/l3q6X4SYcu7xV3SInhk83Pz2ZkbrD8wnrIv3cnlX4sVKX/eliJixaaUbKLlbDtZAlqJ6qKAAIIIICA9wiQiPWetqQmCCCAAALuCBz4TS8K1ibOV1VdgNenLgterRtpbKuDSItLIGPny9/nfXt9phb6jbH mnTDlSE9EFbd26Lzmy W/dp/k5xXjipE6Y1y4nYmvqmh6NNTFmoz59 DVt7tVebVo2VbMWTdWwcsZJDzIWZ1OZOiEacIf5 cu9OrQhUnNmz9a0md/rHzPm69bP/q07gnIKgPUIIIBACROoPUjlP7hZPvazSlo4VXGOBOeGw7K7Oug0bqXi590qv34D5PflWjk/uzFVslSDuuZ/7UrasScLbtLO3WZdPZWq79gmJRGbtpVd9oObdfFb8/PdeJVq1Un fc3o2/5/VrkB1 rCo09mKY8VCCCAAAIIIOD5AiRiPb NiBABBBBAoCAFStdQgxoBijlyVnvWrtWqKhVUoUJ3dQoKNONRr7zY6tZRXZO03WGvrXr1s8vexuncWUc5dTXkhbvV43KmNWvBATVUK22tTY1vfVnvV5is72eu0MIfJyjckRiwBah62z568Mm/qFut3KJLUuyeTVq1cq1Wr92j02Zf/2r1VDvLA8GyhsEaBBBAoMQIXDimpKMX5VO9vEq1aSO/k2dkP7NcCbtjXSRIUuL/5ipp8I0KGFhHF9dl3c1WOsCsjJc9NjHri2dik eWLVXWaYLwLFuZUbv1zcjYDm3l27a mTLBpHWP/5F1qoQs 7ECAQQQQAABBDxRgESsJ7YKMSGAAAIIFJ5AlW567pt2GrVmiWbPnKuIX7/Uoklfq2JQO/Xq11N9wzqqmeNhLW4vZVUueW7ZODPlQRu1a ViQbZABQ 7S6 bn6S449q1ca0WTv1Vv6ycoTffrq4vPxyqmpmKSjy1SyvmLdKcOYu1cvtpJfoGqkmX/nrosTCFdaqv8ub2WBYEEEAAgRSBk5GKuydKF9p1VYCZnsB/2F/kN I22XdHmakJluriwjVKOpFNAtUZcN88xUcNV9lB/eW7IeuYWPuFeLO1eXhioONjV6ayKgQmT31jj7uQtUkqNpRfLzNXbO9u5lmR5hu8xFglrZ6r858s1EXzgEe7yeBmno48ayGsQQABBBBAAAFPEyAR62ktQjwIIIAAAoUvYCujeh376R7zc eZPVoxx8wXO3ORfvtstab XznVNx/S 5gP6f2vba6qlt85S6t5c3Pb6ao/tHrlLv21lXloi8Ua pStqqad 6ppp6tU6u6n9MPmzdqSaBKxjliSTit68QLNjlikhWv2KtY8dbt8/bYadF8fDezfUU0rWQ7YYnRsjgACCBRjAft5Xfp9ns47fgIbmDlZrzVzxoYq4O72CrgzTklRK5RgvuC6uGS7LmWbkz2jhN9WyP5SdwV0i8wCcWmv4ylczeXTpKG0KCbD6z5BDZPfD5L2ObYxi09F XQzc8KGmQRsu3qy ZjpCfZvUPxX5kFdc383l/tsA8hyTFYggAACCCCAgOcK8OnMc9uGyBBAAAEEikDAp0JDdbv LvMzSse3rlKEGSU7e8FcjV9jPgw3 lh3NrEeVOOBA9Xqxy 0yYy2nXTtS/pzkONW1dQlQcfWz9eKhK4a0iEwZeVJRa NVe22DRToPIr17CEdOGM2KRuoCqkzExyerw/e/Fa7SldX675/Ng/lClP3VlXlfATrEbMHAgggUAIFYvcqYepE8/O9SjXrKP/ ZpRsz17mQYwtpb1P6sLO7E3sK2fr4mGTvO3bOcsDuy6tWKnEe5vLt9 f5P /j3TxaPKTGKUqnVV6YH0zHHavLi5LmR 2Rk VfWakfC4cVeL8n3UxfJESthzPUmb2UbAWAQQQQAABBIqDAInY4tBKxIgAAgggUAQCfqraoptudvw8cFTrF5kHsVRwM4yaA/T06E16amykvnjoES3t1kmt65aX/ewRxURFKWpvrIIf6GASsanlH9CsN15VuF Q2rVprLq1Ksn/whFtWhKpjWcC1PyuQWqbOqy2bFNd98TLurpXa9Uua3WsrZv1YTcEEEDAqwUSdSk6UhccP59Xk29oW8nxJVhOi32n4qfHmFG0TbLe8XDETCfwQ3eVv7W9yn7wuvxWbNalS1Xl26WjfConKGnSeF1MGRCruBjFf/y2Ehdt0qXzrj4xLKegWI8AAggggAACnihAItYTW4WYEEAAAQQ8S8CMNm3Tv38eYrKpdt/R qTBAk3 ab6Wb1iiqcsS5BtYWTXqBmvoPZ0V1rOSU/n1FHbHCCWu2qQtm1Zpw5LzspWvrJoNuunOh4ZreGi99AeJVQrRoMF5CI1dEUAAAQRyFjAP9EqcOzfn11NeuRQxWwm3PSi/LLcjJCrp 7d09twHB28AABbSSURBVPBwlR7SWb69 ptk7QVd2rNO8RN/0YWI3ekjXk9v1sXZVzwUGyCAAAIIIIBAMRawTRyQ/BxmFgTyVaD121WylDeg303J62ZHTMryGisQQAABBBBAAAEEEChMgVPDRhXm4fL9WJVybfy6RABBBAwFMFcssnpL7mauxjO3zm6qZsh0C C/D85HwnpUAEEEAAAQQQQAABBBBAAAEEEEAAAQQQQCCjAIlYegQCCCCAAAIIIIAAAggggAACCCCAAAIIIFDAAiRiCxiY4hFAAAEEEEAAAQQQQAABBBBAAAEEEEAAARKx9AEEEEAAAQQQQAABBBBAAAEEEEAAAQQQQKCABXwLuHyKRwABBBBAAAEEEEAAAQQ8ToCHXXlckxAQAggggAACXi/AiFivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wuQiPX6JqaCCCCAAAIIIIAAAggggAACCCCAAAIIIFDUAiRii7oFOD4CCCCAAAIIIIAAAggggAACCCCAAAIIeL0AiVivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wuQiPX6JqaCCCCAAAIIIIAAAggggAACCCCAAAIIIFDUAiRii7oFOD4CCCCAAAIIIIAAAggggAACCCCAAAIIeL0AiVivb2IqiAACCCCAAAIIIIAAAggggAACCCCAAAJFLUAitqhbgOMjgAACCCCAAAIIIIAAAggggAACCCCAgNcLkIj1 iamgggggAACCCCAAAIIIIAAAggggAACCCBQ1AIkYou6BTg AggggAACCCCAAAIIIIAAAggggAACCHi9AIlYr29iKogAAggggAACCCCAAAIIIIAAAggggAACRS1AIraoW4DjI4AAAggggAACCCCAAAIIIIAAAggggIDXC5CI9fompoIIIIAAAggggAACCCCAAAIIIIAAAgggUNQCJGKLugU4PgIIIIAAAggggAACCCCAAAIIIIAAAgh4vQCJWK9vYiqIAAIIIIAAAggggAACCCCAAAIIIIAAAkUtQCK2qFuA4yOAAAIIIIAAAggggAACCCCAAAIIIICA1wv4en0NqaDHCQzod5PHxURACCCAAAIIIIAAAggggAACCCCAAAIIFKQAI2ILUpeyEUAAAQQQQAABBBBAAAEEEEAAAQQQQAABI8CIWLpBoQnMjphUaMfiQAgggAACCCCAAAIIIIAAAggggAACCHiSACNiPak1iAUBBBBAAAEEEEAAAQQQQAABBBBAAAEEvFKARKxXNiuVQgABBBBAAAEEEEAAAQQQQAABBBBAAAFPEiAR60mtQSwIIIAAAggggAACCCCAAAIIIIAAAggg4JUCJGK9slmpFAIIIIAAAggggAACCCCAAAIIIIAAAgh4kgCJWE9qDWJBAAEEEEAAAQQQQAABBBBAAAEEEEAAAa8UIBHrlc1KpRBAAAEEEEAAAQQQQAABBBBAAAEEEEDAkwRIxHpSaxALAggggAACCCCAAAIIIIAAAggggAACCHilAIlYr2xWKoUAAggggAACCCCAAAIIIIAAAggggAACniRAItaTWoNYEEAAAQQQQAABBBBAAAEEEEAAAQQQQMArBUjEemWzUikEEEAAAQQQQAABBBBAAAEEEEAAAQQQ8CQBX08Khli8R2DDcycsVeapNfdb2p6NEUAAAQQQQAABBBBAAAEEEEAAAQQQKE4CjIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFCARWyybjaARQAABBBBAAAEEEEAAAQQQQAABBBBAoDgJkIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFCARWyybjaARQAABBBBAAAEEEEAAAQQQQAABBBBAoDgJkIgtTq1FrAgggAACCCCAAAIIIIAAAggggAACCCBQLAVIxBbLZiNoBBBAAAEEEEAAAQQQQAABBBBAAAEEEChOAiRii1NrESsCCCCAAAIIIIAAAggggAACCCCAAAIIFEsBErHFstkIGgEEEEAAAQQQQAABBBBAAAEEEEAAAQSKkwCJ2OLUWsSKAAIIIIAAAggggAACCCCAAAIIIIAAAsVSgERssWw2gkYAAQQQQAABBBBAAAEEEEAAAQQQQACB4iRAIrY4tRaxIoAAAggggAACCCCAAAIIIIAAAggggECxFLBNHBBuL5aREzQCCCCAAAIIIIAAAggggAACCCCAAAIIIFBMBBgRW0waijARQAABBBBAAAEEEEAAAQQQQAABBBBAoPgKkIgtvm1H5AgggAACCCCAAAIIIIAAAggggAACCCBQTARIxBaThiJMBBBAAAEEEEAAAQQQQAABBBBAAAEEECi AiRii2/bETkCCCCAAAIIIIAAAggggMD/t2PHJAAAAAzD/LuujkIcjOwrAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXQIj9fmc5AQIECBAgQIAAAQIECBAgQIAAAQITASF2cpSZBAgQIECAAAECBAgQIECAAAECBAh8BYTY73eWEyBAgAABAgQIECBAgAABAgQIECAwERBiJ0eZSYAAAQIECBAgQIAAAQIECBAgQIDAV0CI/X5nOQECBAgQIECAAAECBAgQIECAAAECEwEhdnKUmQQIECBAgAABAgQIECBAgAABAgQIfAWE2O93lhMgQIAAAQIECBAgQIAAAQIECBAgMBEQYidHmUmAAAECBAgQIECAAAECBAgQIECAwFdAiP1 ZzkBAgQIECBAgAABAgQIECBAgAABAhMBIXZylJkECBAgQIAAAQIECBAgQIAAAQIECHwFhNjvd5YTIECAAAECBAgQIECAAAECBAgQIDAREGInR5lJgAABAgQIECBAgAABAgQIECBAgMBXIO/QVLi8NHo8AAAAAElFTkSuQmCC[/IMG]

---

### Post by richardth on 2022-03-26
I tried this - or, specifically this section:
```

sudo apt-get purge grub-pc grub-common
sudo rm -r /etc/grub.d/
sudo apt-get install grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub

```
changing 
```

sudo grub-install /dev/nvme0n

```
and various other `grub-install` parameters... but to no avail:
```

$ sudo grub-install /dev/nvme0n1

Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.

```

---

### Post by richardth on 2022-03-26
I tried
```

sudo mount -t vfat /dev/nvme0n1p1 /boot/efi
sudo grub-install --efi-directory /boot/efi /dev/nvme0n1

```
but just got:
```

Installing for x86_64-efi platform.
grub-install: error: unknown filesystem.

```

---

### Post by oldfred on 2022-03-26
To boot in UEFI mode you should have gpt patitioning & must have an ESP.
The ESP - efi system partition is FAT32 and can be anywhere from 100 to 600MB with the esp,boot flags.
You showed the install of grub-pc which is the BIOS boot version. If drive is gpt, you then also must have a bios_grub partition for grub to install correctly.

Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012.
Only if a user installed in the now very old BIOS/MBR mode or have a very old PC may you have BIOS boot.

It is important to have Windows and Ubuntu in same boot mode if one one drive, and even if multiple drives best if all installs in same boot mode.
Or all UEFI/gpt or all BIOS.
While Windows requires MBR with BIOS boot, if Ubuntu on separate drive often better to use gpt whether BIOS or UEFI.

---

### Post by richardth on 2022-03-26
Hi @oldred - thanks again for the info.

I don't properly understand though.
You mention:
1) "you should have gpt patitioning": that is the case, which I know because under the `grub>` prompt, `ls` shows me only `(hd0,gpt1)` etc up to `(hd0,gpt8)` - with `(hd0,gpt5)` being the one I set as root when I choose my Linux kernel.
2) "must have an ESP": 
```
$blkid|grep nvme
```
gives me
```

/dev/nvme0n1p5: UUID="1cd02c5d-3cc5-40d1-9c5d-684cb656b610" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="a6eb290d-1112-4a1f-8225-ef6fbdf102cf"
/dev/nvme0n1p7: LABEL="Image" BLOCK_SIZE="512" UUID="D42C7E1D2C7DFAB6" TYPE="ntfs" PARTUUID="e59237f5-5f8a-4404-8ded-7e12a26be286"
/dev/nvme0n1p3: LABEL="OS" BLOCK_SIZE="512" UUID="D098B08398B06A1C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="f9b0fcb3-408b-4be2-b511-94963cf801d4"
/dev/nvme0n1p1: LABEL_FATBOOT="ESP" LABEL="ESP" UUID="586F-E85D" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6f936066-cf41-490f-bd8e-a58df0b36feb"
/dev/nvme0n1p8: LABEL="DELLSUPPORT" BLOCK_SIZE="512" UUID="7A9A8E2F9A8DE7C9" TYPE="ntfs" PARTUUID="26ba0434-8725-4423-821f-355c576335e0"
/dev/nvme0n1p6: LABEL="WINRETOOLS" BLOCK_SIZE="512" UUID="6EC67DF0C67DB943" TYPE="ntfs" PARTUUID="a6653ce2-2686-4a9a-b18e-f0c76ea4beae"
/dev/nvme0n1p4: BLOCK_SIZE="512" UUID="7C9A0B479A0AFD80" TYPE="ntfs" PARTUUID="ddcd477e-03ee-45f5-82db-c95e1d936fef"

```
So `/dev/nvme0n1p1: LABEL_FATBOOT="ESP" LABEL="ESP"` looks good from that point of view **I suppose**?
3) "You showed the install of grub-pc which is the BIOS boot version" <== I don't really know what you mean by this.  What specifically did I show?
4) "If drive is gpt, you then also must have a bios_grub partition for grub to install correctly." Could this be my problem then?  I don't see any partition that looks like that.  They're all either ESP, Llinux (ext4) or what look like Windows partitions including my actual Windows boot partition.
```
$ efibootmgr -v
```
gives
```

BootCurrent: 0004
Timeout: 5 seconds
BootOrder: 0004,0007,0006,0000,0001,0002
Boot0000* UEFI BC511 NVMe SK hynix 512GB CY07N032510807I3Q 1	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-00-00-00-00-00-00-00)/HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* ONBOARD NIC (IPV4)	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(8c47be48ab79,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.
Boot0002* ONBOARD NIC (IPV6)	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(8c47be48ab79,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot0003  ubuntu	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* ubuntu	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* Windows Boot Manager	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0006* Ubuntu 22.04	HD(5,GPT,a6eb290d-1112-4a1f-8225-ef6fbdf102cf,0x1c25c000,0x1cb83800)/File(\EFI\ubuntu\shimx64.efi)
Boot0007* Windows Boot Manager	HD(1,GPT,6f936066-cf41-490f-bd8e-a58df0b36feb,0x800,0x4b000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................

```
5) "Only if a user installed in the now very old BIOS/MBR mode or have a very old PC may you have BIOS boot." <== I really don't know if this is what I've got or how it happened.  It was a standard Dell that I installed Ubuntu on a couple of years ago.  I may have bought it with Ubuntu installed and later installed Windows - I really can't recall right now.
6) "It is important to have Windows and Ubuntu in same boot mode if one one drive, and even if multiple drives best if all installs in same boot mode."  Very happy to correct this if that's what I should do!  I don't want anything unusual. "Or all UEFI/gpt or all BIOS." Fine with whatever is best or easiest to get to!
7) "While Windows requires MBR with BIOS boot, if Ubuntu on separate drive often better to use gpt whether BIOS or UEFI."  <== I don't quite get what you mean!  Sorry!

Thanks for your help!

---

### Post by richardth on 2022-03-26
Could [this answer]("https://askubuntu.com/a/930305/496773") be right for me?

---

### Post by oldfred on 2022-03-26
You have UEFI and gpt drive.

While I like labels & use them, just labeling a FAT32 partition as ESP does not make it an ESP.

You have to use gparted or other partitioning tools and make sure the flag is esp,boot on your p1. Other tools may use different codes to make a partition as ESP as it actually is a very long GUID in the partition structure (somewhere).

---

### Post by richardth on 2022-03-26
```

(parted) print all
Model: BC511 NVMe SK hynix 512GB (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  158MB  157MB   fat32        EFI system partition          boot, esp
 2      158MB   293MB  134MB                Microsoft reserved partition  msftres
 3      293MB   241GB  241GB   ntfs         Basic data partition          msftdata
 4      241GB   242GB  797MB   ntfs                                       hidden, diag
 5      242GB   488GB  247GB   ext4
 6      488GB   490GB  1038MB  ntfs                                       hidden, diag
 7      490GB   511GB  21.1GB  ntfs                                       hidden, diag
 8      511GB   512GB  1495MB  ntfs                                       hidden, diag

```

---

### Post by oldfred on 2022-03-26
Your ESP partition has correct flags. Should be fine.

---

### Post by richardth on 2022-03-27
Okay well: still I go to the `grub>` prompt on reboot and after manually selecting the kernel I do:
```

$ sudo grub-install /dev/nvme0n1
[sudo] password for richard: 
Installing for x86_64-efi platform.
grub-install: error: unknown filesystem.

```

So... don't know.  But probably some combination of using 22.04 with grub 2.06 and Windows etc etc.

I've backed up the data so I guess I'll re-install from scratch.

---

### Post by oldfred on 2022-03-27
Check ESP.
Either run dosfsck or Windows chkdsk (you have to manually mount ESP in Windows).

man dosfsck
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.
sudo fsck.vfat -t -a /dev/nvme0n1pY # where Y is ESP partition.


Check that you do not have an UEFI setting that locks ESP.

A few have had to totally delete ESP and then recreate it, but then you have to totally reinstall Windows boot loaders with a Windows repair flash drive and reinstall grub with Ubuntu live installer. And good backups of everything on drive(s).

---

### Post by richardth on 2022-03-28
```

$ sudo fsck.vfat -t -a /dev/nvme0n1p1
[sudo] password for richard: 
fsck.fat 4.2 (2021-01-31)
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.


*** Filesystem was changed ***
Writing changes.
/dev/nvme0n1p1: 539 files, 53053/74752 clusters

```

Rebooted... but still boots to `grub>` prompt!

Ahhhggg... :confused:

---

### Post by richardth on 2022-03-28
In my `dmesg` I see:
```

[    1.108987] nvme 0000:3a:00.0: platform quirk: setting simple suspend
[    1.110048] nvme nvme0: pci function 0000:3a:00.0
[    1.115088] nvme nvme0: **missing or invalid SUBNQN field**.
[    1.118760] nvme nvme0: 12/0/0 default/read/poll queues
[    1.121329]  nvme0n1: p1 p2 p3 p4 p5 p6 p7 p8

```

Doesn't seem to be problematic according to [this]("https://forums.gentoo.org/viewtopic-t-1106388-start-0.html") though.

---

### Post by richardth on 2022-03-28
"Check that you do not have an UEFI setting that locks ESP."

How do I check UEFI settings actually?

---

### Post by tea for one on 2022-03-28
> **richardth said:**
> How do I check UEFI settings actually?

For your son's Dell PC, you have to use the dedicated F2 key.
Press the F2 key several times at the Dell logo screen during startup.

---

### Post by oldfred on 2022-03-28
The dosfsck said it cleared the dirty bit.
That would not change grub booting, but should allow grub to be reinstalled.
Try the install of grub again.

---

### Post by richardth on 2022-03-28
I've tried
```

sudo grub-install /dev/nvme0n1

```
and various other combinations but it's always:
```

Installing for x86_64-efi platform.
grub-install: error: unknown filesystem.

```

I did
```

$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.17.0-051700rc4-generic
Found initrd image: /boot/initrd.img-5.17.0-051700rc4-generic
Found linux image: /boot/vmlinuz-5.16.12-051612-generic
Found initrd image: /boot/initrd.img-5.16.12-051612-generic
Found linux image: /boot/vmlinuz-5.15.0-23-generic
Found initrd image: /boot/initrd.img-5.15.0-23-generic
Found linux image: /boot/vmlinuz-5.15.0-22-generic
Found initrd image: /boot/initrd.img-5.15.0-22-generic
Found linux image: /boot/vmlinuz-5.8.0-33-generic
Found initrd image: /boot/initrd.img-5.8.0-33-generic
Found linux image: /boot/vmlinuz-5.8.0-31-generic
Found initrd image: /boot/initrd.img-5.8.0-31-generic
Found linux image: /boot/vmlinuz-5.8.0-28-generic
Found initrd image: /boot/initrd.img-5.8.0-28-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
**/usr/sbin/grub-probe: error: unknown filesystem.**
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
**/usr/sbin/grub-probe: error: unknown filesystem.**
Adding boot menu entry for UEFI Firmware Settings ...
done

```
but I get those `unknown filesystem` lines.  I'll try another reboot later and have a look at the UEFI settings.

---

### Post by #&amp;thj^% on 2022-03-28
When an ext4 filesystem has the metadata_csum_seed feature enabled, then grub-install will not work and report this grub-install: error: unknown filesystem error.
use this with the right device
```
grub-probe --target=fs --device /dev/sda1
```
to check if enabled
Mine is:
```
me on Mon Mar 28 at 02:50 PM in ~ branch: (HEAD) 
>> df -h
Filesystem     Type      Size  Used Avail Use% Mounted on
dev            devtmpfs  3.6G     0  3.6G   0% /dev
run            tmpfs     3.7G  2.1M  3.7G   1% /run
/dev/sdb2      ext4      234G  106G  116G  48% /
tmpfs          tmpfs     3.7G     0  3.7G   0% /dev/shm
tmpfs          tmpfs     3.7G   55M  3.6G   2% /tmp
/dev/sdb1      vfat      511M  296K  511M   1% /boot/efi
/dev/sda3      ext4      429G  100G  307G  25% /media/data
tmpfs          tmpfs     738M  104K  738M   1% /run/user/1000
/dev/sdc1      fuseblk   4.6T  4.3T  259G  95% /run/media/me/My Passport


me on Mon Mar 28 at 02:50 PM in ~ branch: (HEAD) 
>> grub-probe --target=fs --device /dev/sdb2  
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb2.
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb2.
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb2.
grub-probe: error: disk `hostdisk//dev/sdb2' not found.


me on Mon Mar 28 at 02:51 PM in ~ branch: (HEAD) 
>> grub-probe --target=fs --device /dev/sdb1  
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb1.
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb1.
grub-probe: warning: disk does not exist, so falling back to partition device /dev/sdb1.
grub-probe: error: disk `hostdisk//dev/sdb1' not found.


```
and you can disable the feature with
```

tune2fs -O ^metadata_csum_seed /dev/sda1
```
Please use the proper /dev/

---

### Post by richardth on 2022-03-29
Thanks for your help @1fallen.

I have an NVME drive.  The disk is /dev/nvme0n1:
```

$grub-probe --target=fs --device /dev/nvme0n1p1

grub-probe: error: disk `hostdisk//dev/nvme0n1' not found.

```

```

$ df -h


Filesystem      Size  Used Avail Use% Mounted on
tmpfs           772M  2.5M  769M   1% /run
/dev/nvme0n1p5  226G  196G   19G  92% /
tmpfs           3.8G     0  3.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /run/qemu
/dev/nvme0n1p1  146M  104M   43M  71% /boot/efi
/dev/sda2       932G  351G  582G  38% /media/richard/Extra
tmpfs           772M   92K  771M   1% /run/user/126
tmpfs           772M   80K  771M   1% /run/user/1001

```

So I run
```

$ sudo tune2fs -O ^metadata_csum_seed /dev/nvme0n1p1


tune2fs 1.46.5 (30-Dec-2021)
tune2fs: Bad magic number in super-block while trying to open /dev/nvme0n1p1
/dev/nvme0n1p1 contains a vfat filesystem labelled 'ESP'

```

From [what I've read]("https://unix.stackexchange.com/questions/680318/tune2fs-bad-magic-number-in-super-block-while-trying-to-open-dev-sda1") tune2fs is for ext filesystems whereas /dev/nvme0n1p1 is vfat.


For reference:
```

$ sudo fdisk -l

Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: BC511 NVMe SK hynix 512GB               
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4CE4C964-FE6E-4495-BC81-8F483C0528D5


Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     309247    307200   150M EFI System
/dev/nvme0n1p2    309248     571391    262144   128M Microsoft reserved
/dev/nvme0n1p3    571392  470677503 470106112 224.2G Microsoft basic data
/dev/nvme0n1p4 470677504  472233983   1556480   760M Windows recovery environment
/dev/nvme0n1p5 472236032  954071039 481835008 229.8G Linux filesystem
/dev/nvme0n1p6 954071040  956098559   2027520   990M Windows recovery environment
/dev/nvme0n1p7 956098560  997265407  41166848  19.6G Windows recovery environment
/dev/nvme0n1p8 997267456 1000187903   2920448   1.4G Windows recovery environment

```

and

```

$ lsblk

nvme0n1     259:0    0 476.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   150M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0   128M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 224.2G  0 part 
&#9500;&#9472;nvme0n1p4 259:4    0   760M  0 part 
&#9500;&#9472;nvme0n1p5 259:5    0 229.8G  0 part /
&#9500;&#9472;nvme0n1p6 259:6    0   990M  0 part 
&#9500;&#9472;nvme0n1p7 259:7    0  19.6G  0 part 
&#9492;&#9472;nvme0n1p8 259:8    0   1.4G  0 part 

```

---

### Post by oldfred on 2022-03-29
I think tune2fs is for the ext family of file systems, like ext4. See:
man tune2fs

Did you run dosfsck as in post 24?
And check for any UEFI settings that may lock ESP?
You may have to download manual to get better description on all settings.

---

### Post by richardth on 2022-03-29
> **oldfred said:**
> I think tune2fs is for the ext family of file systems, like ext4. See:
man tune2fs

Did you run dosfsck as in post 24?
And check for any UEFI settings that may lock ESP?
You may have to download manual to get better description on all settings.

Yeah, you see post #25.

Right now
```

$ sudo dosfsck /dev/nvme0n1p1
fsck.fat 4.2 (2021-01-31)
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
[12?q]? 1


*** Filesystem was changed ***
The changes have not yet been written, you can still choose to leave the
filesystem unmodified:
1) Write changes
2) Leave filesystem unchanged
[12?q]? 1
/dev/nvme0n1p1: 539 files, 53053/74752 clusters

```

Rebooted - but... same `grub>` prompt...

I went through all the settings in the BIOS looking for anthing that might inhibit writing to the ESP partition or anything like that and turned them off but no effect.

---

### Post by #&amp;thj^% on 2022-03-29
> **richardth said:**
> what I've read[/URL] tune2fs is for ext filesystems whereas /dev/nvme0n1p1 is vfat.



I clearly stated that "When an**_ ext4 _**filesystem has the metadata_csum_seed"
Your in good hands with oldfred.

---

### Post by richardth on 2022-03-30
For those interested, I'll try to recap the situation here.


[LIST]
[*]As I stated at the [beginning]("https://ubuntuforums.org/showthread.php?t=2473061&p=14087015#post14087015") I have some general Linux and IT knowledge (not DevOps/hardware etc).
[*] The machine is a [Dell G3 P89F002]("https://dl.dell.com/topicspdf/g-series-15-3500-laptop_setup-guide_en-us.pdf").  It's my son's machine.
[*]I upgraded it to Ubuntu 22.04 Jammy Jellyfish.  I followed [this process]("https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish") to do so.  It worked quite well.  Obviously I rebooted into 22.04 and it worked fine.
[*]At some point, after a restart, it dropped to the `grub>` prompt.  The only thing I noticed at the time that was any different prior to this was that I had a 1TB USB drive plugged in.  Prior to reboot I removed it.  I was slightly concerned at the time that I did so slightly late in the reboot process.  Nevertheless, that drive had since worked flawlessly.  Could it have somehow messed up the main NVME drive?  Doubt it.
[*]With @oldfred and `efibootmgr`s help from [reply #5]("https://ubuntuforums.org/showthread.php?t=2473061&p=14087056#post14087056") I seem to have repaired I suppose the EFI partition to the extent that when I put the main Windows partition first in boot order I can boot into Windows (this was not possible before that).  BTW:
[LIST]
[*]I had tried various configurations on the use of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), including installing it.  This gave [good information]("https://paste.ubuntu.com/p/nJ2DPx6Npr/") but I couldn't use it for an actual repair, since you have to do that from a live USB but that uses a Ubuntu Bionic instance which itself uses grub 2.04 which is likely incompatible.  I couldn't find a Jammy version.
[*]FYI, this is my [most recent Boot-Repair]("https://paste.ubuntu.com/p/Q9v8VNhqGJ/") just performed then.
[*]@oldfred mentioned "Better to just copy a standard Windows boot stanza into 40_custom" but I don't really understand this. You're referring to `/etc/grub.d/40_custom` surely, but I'm not sure what a Windows boot stanza is nor where I'd get it from.
[/LIST]

[*]I have made many (many...) attempts to get things back in order - you can read through the currently 4 pages, but after all changes:
[LIST]
[*]I never seem to be able to run `grub-install` to correct the problem - it's always `grub-install: error: unknown filesystem.`
[*]With boot order selecting anything but the Windows partition, I'm back to the `grub>` prompt, and have to manually set things up in order to boot into Ubuntu 22.04 (which does then work fine)
[/LIST]
[/LIST]

---

### Post by tea for one on 2022-03-30
> **richardth said:**
> I never seem to be able to run `grub-install` to correct the problem - it's always `grub-install: error: unknown filesystem.

Hopefully, you can still boot into Ubuntu the long-winded way mentioned in an earlier post.
If you can,  then try this change to the comand in post 17 - to re-install Grub from a running session
```
sudo grub-install --efi-directory /boot/efi /dev/nvme0n1
[COLOR="#0000FF"]sudo grub-install --efi-directory=/boot/efi /dev/nvme0n1[/COLOR] #Try with = sign

```

If boot repair does not work with a Jammy Daily ISO, there are other commands to re-install Grub from a live session.
I can post them here but I have not verified them with Jammy 22.04.

If you wish to try them, please confirm.

---

### Post by tea for one on 2022-03-30
> **richardth said:**
> since you have to do that from a live USB but that uses a Ubuntu Bionic instance which itself uses grub 2.04 which is likely incompatible.  I couldn't find a Jammy version.

You can download a Jammy ISO here [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)
After you have created a USB with Jammy, boot via UEFI mode and add the boot-repair software.

I've just checked that boot-repair works with Jammy and it installed and ran in a 22.04 live session.

Hopefully, it will install the version of Grub that you need - fingers crossed.

---

### Post by oldfred on 2022-03-30
The dosfsck on the ESP does not fix grub but then lets you reinstall grub to the ESP.
After rebooting so update to FAT32 partition is completed, use live installer and run the reinstall of grub.
Often easier then just to use Boot-Repair.
If you can manually boot then you can reinstall grub from your install.

---

### Post by richardth on 2022-03-31
Okay, tried again:
[LIST=1]
[*]Rebooted
[*]Inserted my Jammy USB
[*]F2 to change boot order to USB
[*]Jammy live
[*]Wasn't sure what the process would be for `grub-install` from the live USB
[*]Followed [2nd option]("https://help.ubuntu.com/community/Boot-Repair") to install Boot-Repair
[*]Clicked "Recommended repair" and let it do its work.  It produced [this pastebin]("https://paste.ubuntu.com/p/mX5pkFTxqc/") (attached)
[LIST=1]
[*]Rebooted.
[*]Changed boot order to the NVME EFI partition
[*]grub> prompt again :(
[/LIST]

[*]Repeated to 4. above
[*]Followed [this process]("https://support.system76.com/articles/bootloader/") since Pop!_OS is an Ubuntu derivative.  It all completed fine
[LIST=1]
[*]Rebooted... grub> prompt again
[/LIST]
[/LIST]

Hmmm.

---

### Post by oldfred on 2022-03-31
Pop!OS's default is to use SystemD boot not grub. Do not know about it.

You should be able to run a Jammy live installer to make repairs. Always best to have current version live installer just for that purpose.

Grub 2.06 (and maybe older version) is turning off os-prober. Something about security and it opening every partition looking for bootable files.
You can manually turn it back on when installing, but should turn it  off again. And then copy the Windows boot stanza to 40_custom so further updates do not erase the Windows boot stanza.

This is a Windows boot stanza. Seen slightly different versions with different insmod. Not sure if 2.06 then is exactly same or not.
sudo nano /etc/grub.d/40_custom
```
#UEFI ESP on first drive hd0 & first partition gpt1
menuentry "Windows UEFI" {
    insmod part_gpt
    insmod chain
    set root='(hd0,gpt1)'
    chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}



```

Then:
sudo update-grub

---

### Post by richardth on 2022-04-03
Okay, thanks @oldfred

They state on the [Pop!OS bootloader page]("https://support.system76.com/articles/bootloader/") that it's for GRUB, *not* systemd: "On a fresh install of Pop!_OS 18.04, systemd-boot is used rather than the GRUB boot-loader, and the following instructions do not apply please refer to the systemd-boot section on this page."

I'll do the Windows boot stanza thing.  First I have to get a boot menu at all.  I used a Jammy live when following those instructions, specifically:
```

sudo mount /dev/nvme0n1p5 /mnt	
sudo mount /dev/nvme0n1p1 /mnt/boot/efi	
for i in dev dev/pts proc sys run; do sudo mount -B /$i /mnt/$i; done
sudo cp -n /etc/resolv.conf /mnt/etc/
sudo chroot /mnt
apt install --reinstall grub-efi-amd64 linux-generic linux-headers-generic
update-initramfs -c -k all
update-grub

```
and reboot
but... no joy.

---

### Post by oldfred on 2022-04-03
On that page it says it only uses grub for BIOS boot. And uses SystemD-boot for UEFI boot since 18.04.

Does installing the grub-efi-amd64 package install grub?
sudo grub-install # and see man grub for additional boot parameters. If reinstalling from working system, that is all you need. 
But you probably need to specify ESP, id, drive and perhaps others. But if ESP is mounted it may use it?
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub --recheck --debug

---


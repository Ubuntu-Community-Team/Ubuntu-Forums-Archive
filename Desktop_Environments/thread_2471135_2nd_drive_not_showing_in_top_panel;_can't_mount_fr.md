---
title: "2nd drive not showing in top panel; can't mount from there"
date: 2022-01-21
forum: Desktop Environments
---

### Post by watchpocket on 2022-01-21
[EDIT:  Not solved after all.  See post #7 below.]

I've recently noticed, on the desktop in my main (nvme0) OS/drive, in the top panel where I see my other drives, that my 2nd system (/dev/sda, on an SSD) is not shown, which makes me unable to mount the 2nd OS/drive from the main system.

When I open the desktop's computer icon, and click on "SanDisk Ultra II 960GB" I get an error message that says "Unable to mount location, Can't mount file."

What might be causing this?  

How can I get the disk icon to appear in the panel for my second OS/drive?

---

### Post by Bashing-om on 2022-01-21
watchpocket; Hummmmm ...

I would expect gvfs (Gnome virtual file systems) to pick up sda and display by default.
What release are you on ?
what is the Desktop Environment ( Gnome, Mate, xfce4, ext ) ?
Have you made changes in the /etc/fstab file such that file manager now expects the user to make the mount ?
Please also post back your present "mount directive " file:
```

less /etc/fstab

```

[INDENT]maybe here
[INDENT][INDENT]could be elsewhere
[/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2022-01-21
> **Bashing-om said:**
> What release are you on ?

Ubuntu-MATE 20.04.3, kernel 5.4.0-96, same OS version and same kernel version on both my nvme0 drive and my SSD /dev/sda drive.  

When I'm logged into sda, I can see the nvme0 drive fine.
  
But when I'm logged into nvme0, (my primary system) I can't see the sda drive ( I ***can*** see my non-OS data drive.)

> what is the Desktop Environment ( Gnome, Mate, xfce4, ext ) ?

MATE desktop environment v. 1.24.0

> Have you made changes in the /etc/fstab file such that file manager now expects the user to make the mount ?

I don't think so.

Please also post back your present "mount directive " file:
```

less /etc/fstab

```[INDENT]
[/INDENT]
[/QUOTE]

 ```
  1 # /etc/fstab: static file system information.                                                                                                                                        
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  8 # / was on /dev/sdb2 during installation
  9 UUID=21697ef7-83e3-4414-a859-91841f61dce8 /               ext4    errors=remount-ro 0       1
 10 # /boot/efi was on /dev/sdb1 during installation
 11 #UUID=6DE5-0FF8  /boot/efi       vfat    umask=0077      0       1
 12 /swapfile                                 none            swap    sw              0       0
 13 #UUID=2BD2-4199  /boot/efi       vfat    defaults      0       1
 14 UUID=2BD2-4199  /boot/efi       vfat    defaults      0       1
```

Also:

```
--> lsblk -o NAME,FSTYPE,LABEL,PARTLABEL,PARTUUID,UUID                                                             pts/2  Friday  2022-01-21  20:26:13 
NAME        FSTYPE   LABEL          PARTLABEL                  PARTUUID                             UUID
loop0       squashfs  
                                                                              
[snip]    
                                                                 
loop19      squashfs                                                                                
sda                                                                                                 
&#9500;&#9472;sda1      vfat     SSD_ESP        ssd_EFI-system-partition   684141f2-20c3-41be-b2c4-7058d9488896 6DE5-0FF8
&#9492;&#9472;sda2      ext4     MATE-20.04.3   UbuntuMATE-20.04.3         7cc6f822-eb23-4829-9039-6d09e6e0ca55 21697ef7-83e3-4414-a859-91841f61dce8
sdb                                                                                                 
&#9492;&#9472;sdb1      ext4     WeirdBeard     WeirdBeard                 5ab70820-78e7-466e-9c0f-101054d5df9b 70e15e24-a75c-4115-9c83-29cb585676f6
nvme1n1                                                                                             
&#9500;&#9472;nvme1n1p1 vfat     NVME1_ESP      nvme1_EFI-system-partition 90af4214-eca8-4265-8e5f-9c2e3301bba9 E23B-29C2
&#9492;&#9472;nvme1n1p2 ext4     No-OS-here-yet The-next-LTS-UbuntuMATE    77706804-715d-4276-9824-a184ed00df4f a3cb2757-686f-4c5c-92ca-a43b3a223207
nvme0n1                                                                                             
&#9500;&#9472;nvme0n1p1 vfat     NVME0_ESP      nvme0_EFI-system-partition 337ce8d2-65a0-4051-8c12-55cc22666e7e 2BD2-4199
&#9492;&#9472;nvme0n1p2 ext4     MATE-20.04.3   UbuntuMATE-20.04.3         0657b873-53c2-4a40-9e60-3b26c891fd1b 07041e0f-1cde-4caf-9b1d-86851e9601ed
```

---

### Post by Bashing-om on 2022-01-21
watchpocket;

I see nothing amiss -

As I have no familiarity with Mate - will take another to come up with another approach to see what is not taking place.

[INDENT]a know-it-all I am not
[/INDENT]

---

### Post by watchpocket on 2022-01-22
The cause of this problem -- I'm 99% certain -- is that a few days ago I  restored my internal SSD (/dev/sda) -- my secondary install -- from a  Timeshift snapshot.

Timeshift apparently then mounts the sda2 ext4 partition at ***/run/timeshift/backup*** and keeps it mounted there.

After that happened is when I noticed -- while I was logged into my main  (nvme0) install -- that /dev/sda's icon was missing from mountable  drives in my top panel.

That was also when I began to get the error message *"Unable to mount location  Can't mount file"* whenever I opened the desktop's computer icon and clicked on "SanDisk Ultra II 960GB" (my /dev/sda SSD).

(I also tried right-clicking on the SanDisk icon and chose "mount", but the same error message appeared.)

So I did a *`sudo umount /dev/sda2`  *but I still got the error message after I did that.

Then I took a closer look at my /etc/fstab file, and, actually, I do think I see something amiss there:

Here is my main install's ***/etc/fstab (on nvme0):***

```
  1 # /etc/fstab: static file system information.                                                                                                                                          
  2 #
  3 # Use 'blkid' to print the universally unique identifier for a
  4 # device; this may be used with UUID= as a more robust way to name devices
  5 # that works even if disks are added and removed. See fstab(5).
  6 #
  7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  8 # / was on /dev/sdb2 during installation
  9 UUID=[COLOR=#0000ff]21697ef7-83e3-4414-a859-91841f61dce8[/COLOR] /              [COLOR=#0000ff] ext4[/COLOR]    errors=remount-ro 0       1
 10 # /boot/efi was on /dev/sdb1 during installation
 11 #UUID=6DE5-0FF8  /boot/efi       vfat    umask=0077      0       1
 12 /swapfile                                 none            swap    sw              0       0
 13 #UUID=2BD2-4199  /boot/efi       vfat    defaults      0       1
 14 UUID=[COLOR=#0000ff]2BD2-4199  /boot/efi       vfat[/COLOR]    defaults      0       1
```

At line 9, the UUID (21697.....ce8) mounted at root is the ext4 partition [B][I]of /dev/sda.
[/I][/B]At line 14***, ***the UUID mounted at /boot/efi is the EFI partition ***of nvme0np1***.

In other words, if I'm correct, the mounted partitions appear to be mixed (wrongly) between my two installs.
This is borne out when you look below:

```
--> lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

NAME        FSTYPE   SIZE FSUSED LABEL          PARTLABEL                   MOUNTPOINT            UUID                                 PARTUUID
sda                894.3G                                                                                                              
&#9500;&#9472;sda1      vfat   550.3M        SSD_ESP        ssd_EFI-system-partition                          6DE5-0FF8                             684141f2-20c3-41be-b2c4-7058d9488896
&#9492;&#9472;[COLOR=#0000FF]sda2[/COLOR]      [COLOR=#0000FF]ext4[/COLOR]   893.7G  95.4G MATE-20.04.3   UbuntuMATE-20.04.3         /run/timeshift/backup [COLOR=#0000ff]21697ef7-83e3-4414-a859-91841f61dce8[/COLOR] 7cc6f822-eb23-4829-9039-6d09e6e0ca55
sdb                894.3G                                                                                                              
&#9492;&#9472;sdb1      ext4   894.3G        WeirdBeard     WeirdBeard                                        70e15e24-a75c-4115-9c83-29cb585676f6  5ab70820-78e7-466e-9c0f-101054d5df9b
nvme0n1            931.5G                                                                                                              
&#9500;&#9472;[COLOR=#0000ff]nvme0n1p1 vfat[/COLOR]     402M   9.7M NVME0_ESP      [COLOR=#0000FF]nvme0_EFI-system-partition /boot/efi [/COLOR]            [COLOR=#0000ff]2BD2-4199 [/COLOR]                           337ce8d2-65a0-4051-8c12-55cc22666e7e
&#9492;&#9472;nvme0n1p2 ext4   931.1G  39.8G MATE-20.04.3   UbuntuMATE-20.04.3          /                     07041e0f-1cde-4caf-9b1d-86851e9601ed  0657b873-53c2-4a40-9e60-3b26c891fd1b
nvme1n1            931.5G                                                                                                              
&#9500;&#9472;nvme1n1p1 vfat     402M        NVME1_ESP       nvme1_EFI-system-partition                       E23B-29C2                             90af4214-eca8-4265-8e5f-9c2e3301bba9
&#9492;&#9472;nvme1n1p2 ext4   931.1G        No-OS-here-yet The-next-LTS-UbuntuMATE                           a3cb2757-686f-4c5c-92ca-a43b3a223207  77706804-715d-4276-9824-a184ed00df4f
```

And below is the ***/etc/fstab file on /dev/sda***:```

  1  # <file system> <mount point> <type> <options>  <dump>  <pass>                                                                                                                          
  2  
  3 UUID=21697ef7-83e3-4414-a859-91841f61dce8*....../*......ext4*...errors=remount-ro*......0*......1
  4 /swapfile*......none*...swap*...sw*.....0*......0
  5 UUID=6DE5-0FF8*./boot/efi*......vfat*...defaults*.......0*......1

```

This /etc/fstab looks to be correct.  That is, both partitions are of /dev/sda.

[I][B]My  Question:  Should I change the /etc/fstab file in my main (nvme0)  install by removing the UUID for sda's ext4 partition (21697...)
and replace it with nvme0's ext4 partition (a3cb...) ???
[/B][/I]
I'd  like to get a bit of input on this before I go messing around with my  fstab.  I want to make sure I know what I'm doing if I make any changes  there.

---

### Post by watchpocket on 2022-01-23
I did go ahead and make that change (from the question in my previous post), but it was only a partial solution:

Now when I login to my main install (nvme0), /dev/sda is already mounted on the desktop, and its disk-icon in the top panel is larger than the other two disk-icons.

Now I just need to figure out how to have /dev/sda still appear in the top panel (though at normal size), and for it not to  auto-mount on the desktop when I log in to nvme.

I do not have this problem when I log into /dev/sda.

---

### Post by watchpocket on 2022-01-25
At first I thought he solution presented [on this page at AskUbuntu]("https://askubuntu.com/questions/367417/problems-auto-mounting-2nd-hard-drive") worked, but it didn't.

It made it so /dev/sda wasn't auto-mounted, but I also couldn't mount it from its panel icon.

---

### Post by watchpocket on 2022-01-26
I've discovered that [I][B]/dev/sda2 is always either:
[/B][/I]

 ***(a)*** automatically mounted upon login at ***/media/<myusername>/20.04.3-ssd*** <-- (the label I gave this partition), until I un-mount it;


 ***(b)*** mounted at ***/run/timeshift/backup*** (during which time its icon does not appear in the top panel); or


 ***(c)*** not mounted.


 But I'm not sure how to stop it from auto-mounting at login, or how to stop it from mounting on /***run/timeshift/backup*** when it is not auto-mounted in /media.

---

### Post by watchpocket on 2022-01-26
I now believe the problem I'm having with this comes down to a  bug in Timeshift, 
which doesn't seem to want to let go of its target  after doing a backup, [as discussed here]("https://github.com/teejee2008/timeshift/issues/653").

[https://github.com/teejee2008/timeshift/issues/653](https://github.com/teejee2008/timeshift/issues/653)

---


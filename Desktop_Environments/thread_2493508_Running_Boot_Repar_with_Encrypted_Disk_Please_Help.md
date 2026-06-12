---
title: "Running Boot Repar with Encrypted Disk Please Help"
date: 2023-12-17
forum: Desktop Environments
---

### Post by sdsurfer on 2023-12-17
MSI B560M Pro-VDH
Intel 17-11700K
64GB T-Force 3200 mhz RAM
Ubuntu 22.04
Currently monitors connected to integrated HDMI and VGA ports, no card, the card was actually a huge part of my problem
Skill level: moderate but apparently enough to get me in huge trouble
[B]
The problem:[/B] I need to run boot repair but the HD in question is LUKS encrypted and none of the suggested methods work or throw errors. Boot repair won't work on locked encrypted disks.

Attempts to unlock from the GUI fail, the icon just goes back to having the lock icon, Boot Repair fails on those disks.

Posting results will be difficult because the computer in question is down, won't boot, I have to type them. 

I** am seven days in** without getting my system running, and that's sitting here, going nuts, no solutions.

**How I got here:** 20.04 was running fine on the encrypted disk.[ Another problem]("http://ttps://ubuntuforums.org/showthread.php?t=2493379") prompted me to upgrade to 22.04, and it really hit the fan at that point.

To upgrade to 22.04  from within 20.04 from the terminal I did sudo do-release-upgrade. On restart it wouldn't boot, no grub menu, I am guessing grub got hosed up. I have tons of other issues but let's stick with just the one, **getting the encrypted disk open so I can run boot repair, which will fix grub.**
 
- startup USB Ubuntu 22.04
- open terminal

- ```
sudo fdisk-l
```

shows all my disks/drives (remember I'm typing) of note is

```

Disk /dev/sda: 931.51 GiB
......
Device        Boot    Start        End             Sectors          Size      ID      Type
/dev/sda1      *       2048        999423        997376         484M     83     Linux
/dev/sda2              1001470  195352711   1952522242 931G    5        Extended
/dev/sda5              1001470  195352711   1952522240 931G    83      Linux

```

Also having mount issues (see below) so my first attempt to unlock the volume was
```

sudo cryptsetup open --type=luks /media/ubuntu/sda1 system
Device /media/ubuntu/sda1 is not compatible.

```

**Compatible with what????** Not finding any helpful resources to find out. Repeated for sda, sda2, sda5, same.

```

sudo cryptsetup luksOpen /media/ubuntu/sda1 system
Device /media/ubuntu/sda1 is not compatible.

```

**Edit:** luksDump response with the same error.

**Bonus problem **(ignore if irrelevant) can't mount. Hopefully it's a false error and it's due to being encrypted.

Shooting in the dark I attempted to mount sda2 (which is where system files and all my apps are actually stored,)
```

sudo mount /dev/sda2 /media/ubuntu/sda2
mount: mount(2) system call failed: Cannot allocate memory.

```

One of the suggestions to fix that (though it shouldn't be happening, 64GB RAM) is to create a swapfile and enable it.
```

sudo fallocate -l 8G /swapfile
ls -lah /swapfile
-rw-r--r-- 1 root root 8.0G Dec 17 16:11 /swapfile

```

.... and so on, successfully created, enabled, and activate swap but still get memory error trying to mount this disk.

I've been to dozens of resources, none of them fit my case or don't work on my system. Please, I just need to get Boot Repair working with encrypted disks so this system will start up.

Like I said folks, **been on this a full seven days, **trying to ease in to retirement and just need a point to browse, email, and fiddle with the Arduino, this is killing me. Any help anyone can offer would be greatly appreciated.

---

### Post by TheFu on 2023-12-17
Using encryption means accepting that a tiny issue can break access to the system.

If it were me, I'd boot into a Try Ubuntu environment, manually unlock the storage and backup all the data I could. 

If that doesn't work, I'd use my last backups to restore data.

If I didn't have backups, I'd be unhappy with myself, a little pissed that I knew better, then run all the disk tests I could looking for hardware problems. If none are found, I'd wipe it and perform a fresh install. If I used encryption, I'd setup automatic, daily, versioned, backups so I'm never in this position again.

When using encryption, backups aren't optional. They are mandatory.

For me, data is 1000x more important than hardware.  Hardware can be replaced. Data that doesn't get backed up at least weekly isn't very important, obviously.  For really important data, I'll have at least 3 copies - this is called the 3-2-1 Backup Strategy.

Unfortunately, I learned all this the hard way.  My notes on LUKS are a little old, but here they are:

```
$ more crypt-open-usb 
# How-to mount my old C720 Luks encrypted storage
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
# sudo cryptsetup luksOpen /dev/sdf5 c720
# sudo vgchange -ay   # activate LVM objects
# sudo mkdir /mnt/root /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-root /mnt/root

or

# sudo mount /dev/c720--vg/lv--Stuff /mnt/Stuff
# sudo mount /dev/c720--vg/root /mnt/root
```

Typically, if Whole drive encryption is used in Ubuntu, that means LVM will be used, so there's a logical layer between the LUKS container and the file systems.  I'd guess you forgot about LVM and the required commands, along with how to mount those logical volumes which hold the file systems.

---

### Post by sdsurfer on 2023-12-17
> **TheFu said:**
> If it were me, I'd boot into a Try Ubuntu environment, manually unlock the storage and backup all the data I could. 

@theFu thank you . . . I'm still in the Try environment at this moment. 

I just need to know how to unlock it via CLI in the Try environment. My commands are similar to yours, but can't get past this (sub my env for yours)

```

sudo cryptsetup luksOpen /dev/sdf5 c720

```

> Typically, if Whole drive encryption is used in Ubuntu, that means LVM will be used, so there's a logical layer between the LUKS container and the file systems.
This is one clue, I will look, but you're right . . . I created this crypted drive in 2017 and most likely used the easiest path, "encrypt drive/partition" while formatting it, probably in gParted.

---

### Post by TheFu on 2023-12-17
c720 was the name of my LUKS encryption container. Yours will be different. c720 was the hostname at install time of that system, so you could try your hostname on the system.  Until you guess the correct "name", nobody can help.

Those notes were for me, not you. You are expected to replace the machine specific parts to match what your system needs.

BTW, you can validate that LVM is used by using the **lsblk** command with the options that all the long-time gurus post in these forums.

---

### Post by sdsurfer on 2023-12-17
> **TheFu said:**
> c720 was the name of my LUKS encryption container. Yours will be different.

I know, thanks . . . looking at "patterns."

> you can validate that LVM is used by using the **lsblk** command 

Not sure what I'm looking at - run this many times, it's a tree structure similar to yours, output of lvdisplay shows nothing so guessing that's a clue.

[SIZE=4]**[s]PROGRESS!**[/SIZE]

When all else fails, [RTFM]("https://manpages.ubuntu.com/manpages/xenial/man8/cryptsetup.8.html"). In reviewing the docs doen't point out an error in my attempts but what I did find was tCryptOpen:
```
sudo cryptsetup tCryptOpen /dev/sda1/ sda1
```

Prompted a PW, so now let's see if Boot Disk will fix the grub.[/s]

Edit: Nope, doesn't work, reading up on tCrypt I don't even know why it's still in the docs. :-\

---

### Post by TheFu on 2023-12-17
You can't mount a disk partition device if LVM is used. You have to mount an LVM Logical Volume.  The lsblk output should show this, but since you haven't posted it with the common options, I can't help.

And don't forget to run run **sudo vgchange -ay** after the LUKS volume is open. If you do, none of the LVM objects will be available.

---

### Post by sdsurfer on 2023-12-17
> **TheFu said:**
> but since you haven't posted it with the common options

What options would you like? below is just lsblk.
In spite of my strikethrough, I'm making a little progress. Two of the volumes show "crypt" in the type column. On those partitions the luks decrypt works, but one says "volume busy" at the moment, trying to figure out how to "unbusy" it (when I umount, says already unmounted LOL.) Managed to mount another USB in the trial env, here's this:

```

                                 ubuntu@ubuntu:~$ lsblk
NAME                                          MAJ:MIN RM    SIZE RO TYPE  MOUNTPOINTS
loop0                                           7:0    0      3G  1 loop  /rofs
loop1                                           7:1    0   63.4M  1 loop  /snap/core20/1974
loop2                                           7:2    0      4K  1 loop  /snap/bare/5
loop3                                           7:3    0   73.9M  1 loop  /snap/core22/858
loop4                                           7:4    0  237.2M  1 loop  /snap/firefox/2987
loop5                                           7:5    0  349.7M  1 loop  /snap/gnome-3-38-2004/143
loop6                                           7:6    0  485.5M  1 loop  /snap/gnome-42-2204/120
loop7                                           7:7    0   91.7M  1 loop  /snap/gtk-common-themes/1535
loop8                                           7:8    0   12.3M  1 loop  /snap/snap-store/959
loop9                                           7:9    0   53.3M  1 loop  /snap/snapd/19457
loop10                                          7:10   0    452K  1 loop  /snap/snapd-desktop-integration/83
sda                                             8:0    0  931.5G  0 disk  
&#9500;&#9472;sda1                                          8:1    0    487M  0 part  /media/ubuntu/sda1
&#9500;&#9472;sda2                                          8:2    0      1K  0 part  
&#9492;&#9472;sda5                                          8:5    0    931G  0 part  
  &#9492;&#9472;luks-b2df4b95-5718-40be-b944-c4f5e653c73f 253:1    0    931G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root                         253:2    0    927G  0 lvm   
    &#9492;&#9472;ubuntu--vg-swap_1                       253:3    0      4G  0 lvm   
sdb                                             8:16   0    1.8T  0 disk  
&#9500;&#9472;sdb1                                          8:17   0 1015.9G  0 part  /media/ubuntu/sdb1
&#9500;&#9472;sdb2                                          8:18   0    513M  0 part  /media/ubuntu/sdb2
&#9500;&#9472;sdb3                                          8:19   0      1K  0 part  
&#9492;&#9472;sdb5                                          8:21   0  846.6G  0 part  
  &#9492;&#9472;sdb5                                      253:0    0  846.6G  0 crypt 
sdc                                             8:32   1   57.3G  0 disk  
&#9500;&#9472;sdc1                                          8:33   1    4.7G  0 part  /media/ubuntu/sdc1
&#9474;                                                                         /cdrom
&#9500;&#9472;sdc2                                          8:34   1    4.9M  0 part  
&#9500;&#9472;sdc3                                          8:35   1    300K  0 part  
&#9492;&#9472;sdc4                                          8:36   1   52.6G  0 part  /var/crash
                                                                          /var/log

```

So I'm able to unlock via CLI without error:
```
sudo cryptsetup luksOpen /dev/sda5 sda5
```

At first is threw the same error "cannot use device because it's already mounted or in use," umout says "already unmounted," used dmsetup to remove the map . . . . hey all looks good . . . . 

Boot repair still says I have an encrypted drive, and within the Try menu unlocking the volume just bounces back to locked. Man, I am about worn down to nothing.

---

### Post by sdsurfer on 2023-12-17
Quick update: on 2TB drive sdb->sdb5 was basically an empty partition (tried unity on it, failed.) Installed 22.04 on that partition, reboot, for the first time in a week I have a functioning operating system.

The 1 TB drive sda->sda5 is the original install with all my apps, also encrypted. It was initially present in the GUI, opened it, entered password, poof, gone. On reboot doesn't mount, but and I can log in to it using the cryptsetup command above but it says can't be used, it's busy.

More as I poke at it, thank you for your patience.

---

### Post by TheFu on 2023-12-17
This is the important stuff:
```
$ lsblk
NAME                                          MAJ:MIN RM    SIZE RO TYPE  MOUNTPOINTS
sda                                             8:0    0  931.5G  0 disk  
&#9500;&#9472;sda1                                          8:1    0    487M  0 part  /media/ubuntu/sda1
&#9500;&#9472;sda2                                          8:2    0      1K  0 part  
&#9492;&#9472;sda5                                          8:5    0    931G  0 part  
  &#9492;&#9472;luks-b2df4b95-5718-40be-b944-c4f5e653c73f 253:1    0    931G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root                         253:2    0    927G  0 lvm   
    &#9492;&#9472;ubuntu--vg-swap_1                       253:3    0      4G  0 lvm
```

Everything else is useless.

There's 1 encryption container - looks like you called it "crypt" for the name.  After you open it, run
```
sudo vgchange -ay
``` to tell LVM to scan for LVM objects (PVs, VGs, and LVs).
You have two LVs - one is for swap, which doesn't have any data.
The other "root", so you should use a mount command something like this:
```
sudo mkdir /mnt/old-root
sudo mount /dev/ubuntu-vg/root  /mnt/old-root
```

While I think the device name is correct, I could be off a few characters. Use tab completion to get it correct.

Then you can backup all the files you need from under /mnt/old-root.  At reboot, you'll have to do all this again to regain access, so if it were me, I'd get everything this one time.  

When you backup the data, get system settings, data, and config files for all the users too.  And be 100% you backup not just the data inside the files, but the owner, group, permissions, ACLs and xattrs as well.  That means you need to use special options and write the backups to native linux file systems, not NTFS or FAT32 or exFAT.  Native Linux matters.  Without that extra metadata, you have raw data, not useful to restore.

Disconnect the backed up stuff from the system.

Then I'd wipe the disk, do a fresh install, and restore the backup files and settings under that new install, again, retaining owner, group, permissions, et al stuff.

If you do backup system settings, beware that it is unlikely that blindly restoring those will work, so treat them as reference files to be manually merged on the new system.

---

### Post by sdsurfer on 2023-12-18
Thank you so much, at this point I'm just reporting because honestly, things appear to keep changing and I'm not sure what's happening (other than "Bill, it's probably something ***you*** did.")

> **TheFu said:**
> This is the important stuff:

Right, this experience has made me a lot more familiar with this stuff. This,

>  After you open it . . . 

I do this (luksOpen as above) and it responds with "Cannot use device /dev/sda5 which is in use (already mapped or mounted.") The mount commands appeared to have worked fine, but here's where it gets weird.

Last night I was fiddling with Disks, provided by 22.04, on this partition. To even open the options (edit partition, etc.) you have to enter the volume password. In the Disks screen, it shows as Unlocked. I go into Nautilus (or whatever they're calling the file manager these days) and there it is, 995GB volume, I opened /home/bill and there's the little bit of data I store in there (most of my data goes on the 2TB.) I copied all that to the 2TB volume and went to bed.

Today, from within both the GUI and command line /mnt/old-root/home/bill and all the stuff I copied last night is gone. contents of that dir is one directory and symbolic links that are broken (broken, because this is not a boot drive any more.)

```

Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
.cache
.ecryptfs -> /home/.ecryptfs/bill/.ecryptfs
.Private -> /home/.ecryptfs/bill/..ecryptfs/bill/.Private

```

I know (figured out) what those do and are supposed to do (another rabbit hole) . . . **The only important point here **is last night there was 24.9 GB of directories, some standalone apps (Arduino IDE for example) and files in this directory and today the above is all that's here.  It just blows my mind LOL . . . . maybe I'll figure out how to create a boot disk from this drive before nuking it and see if it even runs.

Other parts of this disk - for example /var/www/html where I do my local site testing - are still there and intact. As I said just reporting because I haven't the slightest clue WHT is going on here.

> beware that it is unlikely that blindly restoring those will work, so treat them as reference files to be manually merged on the new system.

I've been reading up on that, and definitely looks like a very bad idea. Time to clean house I guess, I'd love to send you screen shots but I haven't installed anything but boot repair at this point.

Thanks again for your time looking at this, as a web dev I know how difficult it is extracting what you need from someone to help and I appreciate your patience.

Where I'm at right now: I don't even know if this is solved or not, I think it is. Have a new graphics card in hand and plan on slamming in a little software today.

Edit: playing with this, note the symbolic links. When I run what the desktop link is pointing to,

```

sudo nano /mnt/old-root/usr/bin/ecryptfs-mount-private

```

I get 
```
ERROR: Encrypted private directory is not setup properly
```

I'm guessing I won't get anywhere unless this is a live boot disk.

---

### Post by TheFu on 2023-12-18
You mixed LUKS encryption AND encfs/encryptfs?  I know very little about those last two, since they broke my backups, I deemed them unusable, wiped the system and never touched them again.

I don't trust **Gnome Disks** nor any **file managers**.  I do everything from a shell, except partitioning if I have **gparted** available. Been burned too many times.  

When setting up new systems, I setup the partitions and LVM objects BEFORE the install, so I get exactly what I want.  I haven't done a LUKS install in a long time, but I remember checking the box and holding my nose for the defaults - stopped using laptops around 2020. Seems I wasn't traveling much anymore.  After the LUKS install finishes, I quickly reduce the root LV from whatever size they default down to 25-35G, create a swap LV if it wasn't already create, create a home LV and usually create /var LV.  All these go inside the LUKS container, so they will be encrypted.  

Long, long ago, I reduced all the things inside the LUKS container and reduced the partition where LUKS was just to get non-encrypted "Stuff" areas on the drive too.  The math is a bunch of accounting since there are headers for every object involved and only the developers know the exact number of bytes used for the headers .... plus different versions of the different object have differently sized headers. Some have trailers, so a buffer needed to be provided on both sides of those objects. Lots of accounting.

Anyway, don't mix encryption tools.
Always have excellent backups, if you use encryption.

Those are the main take-aways here.

If you had excellent backups, this would have been handled in 45 minutes.

---


---
title: "Ubuntu PRO"
date: 2024-01-23
forum: Desktop Environments
---

### Post by honzap00 on 2024-01-23
Hello,
I have Ubuntu PRO  LTS with ZFS and encryption. 

Approximately one day after a  clean installation, the system was no longer functional and remained  stuck at boot, as seen in the screen

[IMG]https://ibb.co/YBrN4Br[/IMG][https://ibb.co/YBrN4Br](https://ibb.co/YBrN4Br)

[IMG]https://ibb.co/YBrN4Br[/IMG]

Before this error occurred, I had to reinstall the system


[URL="https://askubuntu.com/questions/260353/segmentation-fault-when-using-su-or-sudo"]bash - segmentation fault when using su or sudo - Ask Ubuntu

[/URL]Is there an issue with ZFS in combination with encryption?

[URL="https://askubuntu.com/questions/260353/segmentation-fault-when-using-su-or-sudo"]
[/URL]

---

### Post by honzap00 on 2024-01-23
Memtest and nvme disk test was pass, hp probook g9

---

### Post by #&amp;thj^% on 2024-01-23
Your Thread Title is a bit misleading, You seem to be asking about ZFS.

Anywho please see the system-info link in my signature, it will give the information needed to help you.

Paste the link it gives you back here so we know where it is.

I have 3 zfs systems up and going ATM.

---

### Post by honzap00 on 2024-01-23
thanks [https://termbin.com/mu4r](https://termbin.com/mu4r)

---

### Post by #&amp;thj^% on 2024-01-24
Nothing is jumping out at me.
There is this "zsys" that can fill your boot pool but I see now you had to run the script from the Live installer.

If I would of taken the time to see you could not boot from your installed system  I would of advised to run that script a bit differently.
I'm going to out today life has me chasing a full day, I'm going to ask someone to jump  in here to see if we can help you.

If this is fresh new install and you had good back-ups I would now just reinstall. But wait a bit for the person I'm going to ask to jump in.

---

### Post by MAFoElffen on 2024-01-24
Could you please follow these instructions to unlock your pools, chroot into the installed system... DL the scipt again, except this time, while having it unocked and chrooted in, run it with this option:
```

./system-info --details

```

Then, while it is chrooted in, do
```

apt update
grub-probe /boot
apt install --reinstall --yes grub-efi-amd64 grub-efi-amd64-signed linux-image-generic linux-generic-hwe-22.04 shim-signed zfs-initramfs
# Re-configure Grub
#
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
update-grub
exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a
reboot

```
The comment 1falen made... Is becaseu Ubuntu Pro "is NOT a release"... Ubuntu is the release. Ubuntu Pro would be if you enrolled it into Ubuntu Pro "services", which you have 5 free subscriptions... So adds another  years of security updates.

RE: [https://ubuntuforums.org/showthread.php?t=2494693](https://ubuntuforums.org/showthread.php?t=2494693)

---

### Post by honzap00 on 2024-01-25
Hello, 
thank you very much for your help. 
I greatly appreciate it, but I  had to reinstall the notebook because I needed it for work. However,  there were still several errors with the ZFS and encryption connection.  
In the end, I performed a new installation using LVM and encryption. 
I  am sending a report to see if you find anything. It's possible that the  combination of ZFS and encryption on an HP ProBook G9 notebook may not  work correctly.

[https://termbin.com/eljk](https://termbin.com/eljk)

---

### Post by MAFoElffen on 2024-01-25
Unfortunately, now, since you could not wait, and before getting instruction on what your change of plans were, before you did it... Yes, you have a mess to clean up.

I wish you would haven given us some warnign or a heads up. We could have saved you some work with doing that.

Right now, I'm sorry, but this will just be temporary, let me explain what needs to happen.

You need to destroy the old pools to remove them. Yes, you blew away the partitions and vdevs, but the defines for ZFS and LVM exist outside of the partitions.

So to destroy the pools (rpool & bpool), you first need to temporarily reinstall zfsutils-linux. Then do
```

sudo zdb

```
Please post the output within Code Tags. The output will reveal what the PoolID is, so you can use that to delete the pools. Why? because you overwrote where the pools were written to, before properly destroying the pools, before doing that.

---

### Post by honzap00 on 2024-01-26
I'm very sorry, I must have explained it wrong. I have already done a new installation with LVM and encryption. I was wondering if ZFS and siphoning on my HP probook G9 laptop might be causing the problem.

---

### Post by honzap00 on 2024-01-26
However, even now after a new clean install, the graphics environment seems slow to me, and this is a new laptop about a year old, intel i5 12th Gen  i5-1235U, 16gb ram, nvme ssd 512GB

---

### Post by MAFoElffen on 2024-01-26
I tried to explain to you. You installed as ZFS, which created two ZFS pools: rpool and bpool.

Before doing another install on it, you should have destroyed the pools, via 
```

sudo zpool destroy rpool
sudo zpool destroy bpool

```
Then the ZFS pools and the defines for those pools would be gone.

Another way would be to zero the disks via (where $DISK is the disk device name):
```

blkdiscard -f $DISK
wipefs -a $DISK
sgdisk --zap-all $DISK

```
But you didn't do either of those, right? So the ZFS defines for those two pools are still there, even if the partions were erased and replaced by the new partitions.

The installer doesn't check if ZFS Pools are prexisting on a disk, so it does not get rid of them. This is something I filed a bug report on for DEV Mantic during that DEV Cycle, where I mentioned the solution I recommended for that should be backported to the other installers that install ZFS... Because on a ZFS-On-Root reinstall, if you try to reinstall ZFS, that was ZFS already it fails on "there are already pools with those names"...

Above was part of my recommendation on that.

Enter in added on top of that, what you did. You selected "Erase All > LVM with Encryption"... Which erased the two partitions that had rpool and bpool, which the installer then created more partitions to install to, overwriting where they were. But the ZFS Pool defines reside in another part of the disk, that is outside of those partitions, so are still there. 

This makes it a challenge to get rid of those. That is why I asked you to run 'zdb' to lisyt what is inside of the ZFS defines that "are still there" on your machine. Why because it is going to be a challenge to destroy those two pool defines when they are only partially there. Usually when that happens you have to use the ZFS PoolID or the ZFS vdev device name, instead of the PoolName.

It just like LVM. Even though you have an LVM installed on two different OS'es o two different disks, when you do vgscan, it see's all the LVM pieces from all disks, because the defines for those reside on disk, outside of the partitions. 

Another easier way to get rid of the fragments that are left, is to just zero out that disk, that it was installed on, and reinstall the OS you just installed>>> on a properly prepared, clean disk. You seemed to be confused and in need of the full description. You seem to need to know all of the details.

You understand that now?

Then we can look at what is going on with your graphics.

---

### Post by honzap00 on 2024-01-26
:~$ sudo zbd
sudo: zbd: command not found
:~$ sudo zpool
sudo: zpool: command not found
:~$ blkdiscard -f $DISK
blkdiscard: no device specified
:~$ wipefs -a $DISK
wipefs: no device specified
Try 'wipefs --help' for more information.
:~$ sgdisk --zap-all $DISK
:~$ lsblk 
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0                   7:0    0     4K  1 loop  /snap/bare/5
loop1                   7:1    0   9,6M  1 loop  /snap/canonical-livepatch/246
loop2                   7:2    0 105,8M  1 loop  /snap/core/16202
loop3                   7:3    0  55,7M  1 loop  /snap/core18/2812
loop4                   7:4    0  63,4M  1 loop  /snap/core20/1974
loop5                   7:5    0  63,9M  1 loop  /snap/core20/2105
loop6                   7:6    0  74,1M  1 loop  /snap/core22/1033
loop7                   7:7    0  73,9M  1 loop  /snap/core22/858
loop8                   7:8    0 237,2M  1 loop  /snap/firefox/2987
loop9                   7:9    0 262,5M  1 loop  /snap/firefox/3687
loop10                  7:10   0 164,8M  1 loop  /snap/gnome-3-28-1804/198
loop11                  7:11   0 349,7M  1 loop  /snap/gnome-3-38-2004/143
loop12                  7:12   0 485,5M  1 loop  /snap/gnome-42-2204/120
loop13                  7:13   0   497M  1 loop  /snap/gnome-42-2204/141
loop14                  7:14   0  91,7M  1 loop  /snap/gtk-common-themes/1535
loop15                  7:15   0 263,9M  1 loop  /snap/kate/171
loop16                  7:16   0 571,7M  1 loop  /snap/obs-studio/1294
loop17                  7:17   0 182,8M  1 loop  /snap/signal-desktop/612
loop18                  7:18   0  12,3M  1 loop  /snap/snap-store/959
loop19                  7:19   0  53,3M  1 loop  /snap/snapd/19457
loop20                  7:20   0  40,4M  1 loop  /snap/snapd/20671
loop21                  7:21   0   452K  1 loop  /snap/snapd-desktop-integration/83
loop22                  7:22   0  85,5M  1 loop  /snap/teams-for-linux/504
loop23                  7:23   0 321,1M  1 loop  /snap/vlc/3721
nvme0n1               259:0    0 476,9G  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2           259:2    0   1,7G  0 part  /boot
&#9492;&#9472;nvme0n1p3           259:3    0 474,8G  0 part  
  &#9492;&#9472;nvme0n1p3_crypt   252:0    0 474,8G  0 crypt 
    &#9500;&#9472;vgubuntu-root   252:1    0 472,8G  0 lvm   /var/snap/firefox/common/host-hunspell
    &#9474;                                            /
    &#9492;&#9472;vgubuntu-swap_1 252:2    0   1,9G  0 lvm   [SWAP]

---

### Post by honzap00 on 2024-01-26
lsblk -f
NAME            FSTYPE      FSVER    LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINTS
loop0           squashfs    4.0                                                         0   100% /snap/bare/5
loop1           squashfs    4.0                                                         0   100% /snap/canonical-livepatch/246
loop2           squashfs    4.0                                                         0   100% /snap/core/16202
loop3           squashfs    4.0                                                         0   100% /snap/core18/2812
loop4           squashfs    4.0                                                         0   100% /snap/core20/1974
loop5           squashfs    4.0                                                         0   100% /snap/core20/2105
loop6           squashfs    4.0                                                         0   100% /snap/core22/1033
loop7           squashfs    4.0                                                         0   100% /snap/core22/858
loop8           squashfs    4.0                                                         0   100% /snap/firefox/2987
loop9           squashfs    4.0                                                         0   100% /snap/firefox/3687
loop10          squashfs    4.0                                                         0   100% /snap/gnome-3-28-1804/198
loop11          squashfs    4.0                                                         0   100% /snap/gnome-3-38-2004/143
loop12          squashfs    4.0                                                         0   100% /snap/gnome-42-2204/120
loop13          squashfs    4.0                                                         0   100% /snap/gnome-42-2204/141
loop14          squashfs    4.0                                                         0   100% /snap/gtk-common-themes/1535
loop15          squashfs    4.0                                                         0   100% /snap/kate/171
loop16          squashfs    4.0                                                         0   100% /snap/obs-studio/1294
loop17          squashfs    4.0                                                         0   100% /snap/signal-desktop/612
loop18          squashfs    4.0                                                         0   100% /snap/snap-store/959
loop19          squashfs    4.0                                                         0   100% /snap/snapd/19457
loop20          squashfs    4.0                                                         0   100% /snap/snapd/20671
loop21          squashfs    4.0                                                         0   100% /snap/snapd-desktop-integration/83
loop22          squashfs    4.0                                                         0   100% /snap/teams-for-linux/504
loop23          squashfs    4.0                                                         0   100% /snap/vlc/3721
nvme0n1         zfs_member  5000     rpool 5441626908550946763                                   
&#9500;&#9472;nvme0n1p1     vfat        FAT32          FE5D-F3E9                               496,6M     3% /boot/efi
&#9500;&#9472;nvme0n1p2     ext4        1.0            a19c594c-f497-42f9-9626-be6bc809aaa7      1,2G    18% /boot
&#9492;&#9472;nvme0n1p3     crypto_LUKS 2              74256a2f-51c5-42fe-b24a-7724e4239196                  
  &#9492;&#9472;nvme0n1p3_crypt
                LVM2_member LVM2 001       9YuSmF-LhDb-FVp1-kpQB-v28j-C4qj-eGd91P                
    &#9500;&#9472;vgubuntu-root
    &#9474;           ext4        1.0            51a678eb-bb88-449e-8ed1-a7641d838dc8    423,3G     4% /var/snap/firefox/common/host-hunspell
    &#9474;                                                                                            /
    &#9492;&#9472;vgubuntu-swap_1
                swap        1              2bc3e10c-fd62-4328-b9a6-f32ce0fcc5fd                  [SWAP]

---

### Post by MAFoElffen on 2024-01-27
Please follow instructions carefully! Do you understad what I am sayig? If not ask first before trying commands.

Like I said, you would have to temporarily reinstall zfsutils-linux "first"...
```

sudo apt install --yes zfsutils-linux

```
If you look at Post #8, I said to do
```

sudo zdb

```
You got "command-not-found" as you mistyped that as "sudo zbd"... See how those are different?

Just for example sake, this is what 'zdb' output looks like:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ sudo zdb
[sudo] password for mafoelffen: 
backups:
    version: 5000
    name: 'backups'
    state: 0
    txg: 646037
    pool_guid: 9539864118717640029
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 9539864118717640029
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 10293634412784343986
            path: '/dev/disk/by-id/ata-Dogfish_SSD_2TB_AA000000000000001150-part1'
            whole_disk: 0
            metaslab_array: 131
            metaslab_shift: 33
            ashift: 12
            asize: 1610606968832
            is_log: 0
            DTL: 1225
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
bpool:
    version: 5000
    name: 'bpool'
    state: 0
    txg: 1205545
    pool_guid: 17122705133225367552
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 17122705133225367552
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 5518423130802567917
            path: '/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part7'
            whole_disk: 0
            metaslab_array: 131
            metaslab_shift: 27
            ashift: 12
            asize: 2142765056
            is_log: 0
            DTL: 519
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
dpool:
    version: 5000
    name: 'dpool'
    state: 0
    txg: 549301
    pool_guid: 6427288574932261272
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 6427288574932261272
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 2927894313761812317
            path: '/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part2'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 33
            ashift: 12
            asize: 926651252736
            is_log: 0
            DTL: 387
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
hpool:
    version: 5000
    name: 'hpool'
    state: 0
    txg: 5390182
    pool_guid: 13070673595765447931
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 13070673595765447931
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 4803899376542376242
            path: '/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part9'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 31
            ashift: 12
            asize: 426693361664
            is_log: 0
            DTL: 275
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
kpool:
    version: 5000
    name: 'kpool'
    state: 0
    txg: 1785252
    pool_guid: 11665695484168047513
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 11665695484168047513
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 13013341973632771814
            path: '/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N-part1'
            whole_disk: 0
            metaslab_array: 65
            metaslab_shift: 33
            ashift: 12
            asize: 1073737105408
            is_log: 0
            DTL: 118
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
rpool:
    version: 5000
    name: 'rpool'
    state: 0
    txg: 5079627
    pool_guid: 3227281937742995014
    errata: 0
    hostid: 1376597032
    hostname: 'Mikes-ThinkPad-T520'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 3227281937742995014
        create_txg: 4
        children[0]:
            type: 'disk'
            id: 0
            guid: 14835827942678115141
            path: '/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W-part8'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 32
            ashift: 12
            asize: 536866193408
            is_log: 0
            DTL: 714
            create_txg: 4
            com.delphix:vdev_zap_leaf: 129
            com.delphix:vdev_zap_top: 130
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data

```
The command 'zdb' is added when you install zfsutils-linux. So is 'zpool' and 'zfs'... If you go that route, to remove the pool definition fragments, you need those details, as explained in Post #11...

When I mentioned zeroing the disk, I mentioned that as "an additional, separate" method open to you to do that. Not to mix them together, which you did. When I mentioned zeroing your disk, in Post #11, right before the commands, I said:
> 
 Another way would be to zero the disks via (where $DISK is the disk device name):

By what you posted (without using CODE Tags, when you should have), that should have translated to either you substituting/replacing that word "$DISK" with "/dev/nvme0n1" or re-assigning that as a variable for it to use like this
```

DISK=/dev/nvme0n1

```
But only if you decided to that, and meant to wipe that disk of "everything"... meaning all traces and fragments of what is on there, including the partiton table, and your all presence of your fresh install. Don't you think it might be smarter to try to save that first, by just removing the definstions? 

Or do you just want to wipe it clean and start over fresh? That is your decision. But, please, do not mix things together as one, where there are two separate options, with different directions with each. They are not one option where you mix evrything together. That never works out well.

Before you do anything, tell me which of those two options you would like to try first...

---

### Post by #&amp;thj^% on 2024-01-27
It sounds to me like you don't quite understand what MAFoElffen is trying to help you with.

First if you have not already blew your system up by not following those steps:
Check:
```
apt policy zfsutils-linux
zfsutils-linux:
  Installed: 2.2.2-4
  Candidate: 2.2.2-4
  Version table:
 *** 2.2.2-4 650
        650 http://http.us.debian.org/debian testing/contrib amd64 Packages
        600 http://http.us.debian.org/debian unstable/contrib amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-3~bpo12+1 599
        599 https://deb.parrot.sh/parrot lory-backports/contrib amd64 Packages
     2.1.13-1~bpo12+1parrot1 600
        600 https://deb.parrot.sh/parrot lory/contrib amd64 Packages

```
That needs to be installed first if only temporay.

Also you still have this:
```
nvme0n1 zfs_member 5000 rpool 5441626908550946763 
```

That in time will hurt your new sytem if it is still up and working.

I use ZSF for storage only on Debian for now anyway:
You will only see "tank" on mine ie:
```
sudo zdb
[sudo] password for me: 
tank:
    version: 5000
    name: 'tank'
    state: 0
    txg: 22495
    pool_guid: 10926758658995060061
    errata: 0
    hostid: 2122146739
    hostname: 'parrot'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 10926758658995060061
        create_txg: 4
        com.klarasystems:vdev_zap_root: 129
        children[0]:
            type: 'disk'
            id: 0
            guid: 10795441740398861942
            path: '/dev/sda2'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 32
            ashift: 11
            asize: 499564150784
            is_log: 0
            DTL: 1548
            create_txg: 4
            com.delphix:vdev_zap_leaf: 130
            com.delphix:vdev_zap_top: 131
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
        com.klarasystems:vdev_zaps_v2

```

I'm going to suggest you use this option for next install:
> Another way would be to zero the disks via (where $DISK is the disk device name): 
Just as MAFoElffen also has suggested in post #14, but if it is not to late and be sure to have good back-ups first.

Also Please understand again MAFoElffen warning:
> But only if you decided to that, and meant to wipe that disk of "everything"... meaning all traces and fragments of what is on there, including the partiton table, and your all presence of your fresh install. Don't you think it might be smarter to try to save that first, by just removing the definstions? 

And If you do not fully understand, STOP and ask first, there is zero shame in not knowing.

---

### Post by honzap00 on 2024-01-27
First, I would like to thank you very much for your help. I truly have not encountered such an approach before. Hats off. Thank you.
I apologize again, but I didn't understand your earlier advice. It wasn't clear to me why I should destroy the zpool when I already have the new system reinstalled. I wasn't aware that something might still be remaining. Currently, my system is configured as needed, and I would prefer not to lose everything. However, I still need a 100% reliable system. If the issue is related to any remaining ZFS components, I will do what you advise. Thank you for your patience.

---

### Post by #&amp;thj^% on 2024-01-27
Well it's up to you, but you will be rolling the dice for a  reliable/stable system.

I'm glad to see you did not destroy your system, but it would not hurt to back up daily.

---

### Post by MAFoElffen on 2024-01-27
Please start a different thread to work on your graphics issue. This one started out as "about" not booting Encrypted ZFS, is past-due and evolved to getting solved by reinstallig as LVM Encrypted. Your graphics is a different issue that that.

I would suggest, that as a minimum, include the output of this:
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'
grep -m1 'model name' /proc/cpuinfo

```
And give a detailed explanation what is going on.

---

### Post by honzap00 on 2024-01-28
I don't know what you mean. I definitely want a stable system - I need it for work, even if it means reinstalling.

---

### Post by ajgreeny on 2024-01-28
To make it easier for us all to help you please use Code Tags when posting any terminal output as shown at [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

This formats the text in a way that makes it much easier to read and understand.

---

### Post by MAFoElffen on 2024-01-28
The easiest & fastest way to ensure everything is a clean install, for what you had, at this point... Is to wipe everything clean, start over and reinstall. The last install is only a few days old. You really aren't loosing anything, but have a lot to gain.

Boot from an installer LiveUSB > Select try > Open a terminal session and open Firefox. In Firefox, get back to this post to cut and paste the following commands, executing each by pressing <Enter>:
```

DISK=/dev/nvme0n1
blkdiscard -f $DISK
wipefs -a $DISK
sgdisk --zap-all $DISK

```
Make sure each is successful.

Start the installer and install (again) as you desire. Everything will install on a clean system, and should have no problems (with that).

---

### Post by honzap00 on 2024-01-29
Thank you, before I do that. How can I now display the ZFS that remained from the previous installation? I can't see it anywhere.




lsblk -a
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0                   7:0    0     4K  1 loop  /snap/bare/5
loop1                   7:1    0   9,6M  1 loop  /snap/canonical-livepatch/246
loop2                   7:2    0 105,8M  1 loop  /snap/core/16202
loop3                   7:3    0  55,7M  1 loop  /snap/core18/2812
loop4                   7:4    0  63,4M  1 loop  /snap/core20/1974
loop5                   7:5    0  63,9M  1 loop  /snap/core20/2105
loop6                   7:6    0  74,1M  1 loop  /snap/core22/1033
loop7                   7:7    0  73,9M  1 loop  /snap/core22/858
loop8                   7:8    0 237,2M  1 loop  /snap/firefox/2987
loop9                   7:9    0 262,5M  1 loop  /snap/firefox/3687
loop10                  7:10   0 164,8M  1 loop  /snap/gnome-3-28-1804/198
loop11                  7:11   0 349,7M  1 loop  /snap/gnome-3-38-2004/143
loop12                  7:12   0 485,5M  1 loop  /snap/gnome-42-2204/120
loop13                  7:13   0   497M  1 loop  /snap/gnome-42-2204/141
loop14                  7:14   0  91,7M  1 loop  /snap/gtk-common-themes/1535
loop15                  7:15   0 263,9M  1 loop  /snap/kate/171
loop16                  7:16   0 182,8M  1 loop  /snap/signal-desktop/612
loop17                  7:17   0 571,7M  1 loop  /snap/obs-studio/1294
loop18                  7:18   0  12,3M  1 loop  /snap/snap-store/959
loop19                  7:19   0 182,8M  1 loop  /snap/signal-desktop/614
loop20                  7:20   0  53,3M  1 loop  /snap/snapd/19457
loop21                  7:21   0  40,4M  1 loop  /snap/snapd/20671
loop22                  7:22   0   452K  1 loop  /snap/snapd-desktop-integration/83
loop23                  7:23   0 321,1M  1 loop  /snap/vlc/3721
loop24                  7:24   0  85,5M  1 loop  /snap/teams-for-linux/504
loop25                  7:25   0     0B  0 loop  
nvme0n1               259:0    0 476,9G  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2           259:2    0   1,7G  0 part  /boot
&#9492;&#9472;nvme0n1p3           259:3    0 474,8G  0 part  
  &#9492;&#9472;nvme0n1p3_crypt   252:0    0 474,8G  0 crypt 
    &#9500;&#9472;vgubuntu-root   252:1    0 472,8G  0 lvm   /var/snap/firefox/common/host-hunspell
    &#9474;                                            /
    &#9492;&#9472;vgubuntu-swap_1 252:2    0   1,9G  0 lvm   [SWAP]






sudo parted -l
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgubuntu-root: 508GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0,00B  508GB  508GB  ext4


Error: /dev/mapper/nvme0n1p3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/nvme0n1p3_crypt: 510GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgubuntu-swap_1: 2051MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  2051MB  2051MB  linux-swap(v1)


Model: SK hynix BC711 HFM512GD3JX013N (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   2330MB  1792MB  ext4
 3      2330MB  512GB   510GB

---

### Post by MAFoElffen on 2024-01-29
Via
```

sudo apt install --yes zfsutil-linux zfs-initramfs
sudo zdb

```
Then just for extra, if anything shows
```

sudo zpool import <Tab>

```
Meaning type the 3 words, then press the <Tab> Key...

---

### Post by honzap00 on 2024-01-29
:~$ sudo zdb
cannot open '/etc/zfs/zpool.cache': No such file or directory
:~$

---

### Post by #&amp;thj^% on 2024-01-29
Please Please PLEASE use Code Tags, you have been asked a few times now to comply.
It's just common courtesy and the proper thing to do.

Now I no  longer see your "rpool" listed, but give us this wrapped in Code Tags
```
lsblk -f |grep rpool

```
See my signature for Code Tags

---

### Post by honzap00 on 2024-01-29
```
lsblk -f |grep rpool
nvme0n1               zfs_member  5000     rpool                          5441626908550946763
```

---

### Post by #&amp;thj^% on 2024-01-29
Yes there it is....And Thank you for the Tags

Eventualy  that will come in to play if not already.

Post #21 will give you a clean install/reinstall

---

### Post by honzap00 on 2024-01-29
I thank you :-)  Should I perform a new installation with ZFS and encryption? or choose another combination? The only condition is encryption.

---

### Post by #&amp;thj^% on 2024-01-29
> **honzap00 said:**
> I thank you :-)  Should I perform a new installation with ZFS and encryption? or choose another combination? The only condition is encryption.

Yikes that's kind of personal choice and one I can't decide for you. I will say zfs has a learning curve to it though.
Is that the right choice for a stable work system?

Your LVM on ext4 is very stable and proven with encryption. 

And if you want to learn about "zfs" just install :
```
sudo apt install zfsutils-linux
```
After your new install, then if you mess up your system will/should remain intact

Some light reading: [http://jenpeterson.net/zfs-blog/](http://jenpeterson.net/zfs-blog/)

Good Luck :)

---

### Post by honzap00 on 2024-01-30
I have an idea, but I need advice on whether it's possible.
Can I create a disk backup (image) - for example, using Acronis True - and then restore that backup onto a previously properly erased disk?

---

### Post by MAFoElffen on 2024-01-30
You only have a few days on a fresh install, right? That is not much to start over fresh... 

And you want to do a full clone image backup on a system that is going to carry over whatever low-level problems it had to the wiped / new / clean disk...

See what that "sounds like" when it is read back to you? That would not pass the common sense litmus test right?

Maybe if you were talking rsync or rdiff-backup based backups... I just posted a tar backup script on the Forum a few weeks ago.

---

### Post by #&amp;thj^% on 2024-01-30
LOL I agree with MAFoElffen's post above 100%

---

### Post by honzap00 on 2024-02-07
> **MAFoElffen said:**
> You only have a few days on a fresh install, right? That is not much to start over fresh... 

And you want to do a full clone image backup on a system that is going to carry over whatever low-level problems it had to the wiped / new / clean disk...

See what that "sounds like" when it is read back to you? That would not pass the common sense litmus test right?

Maybe if you were talking rsync or rdiff-backup based backups... I just posted a tar backup script on the Forum a few weeks ago.

I've done everything according to point 21
Then reinstalled the system

---

### Post by MAFoElffen on 2024-02-08
You should have no problem with that going forward now. Congratulations and enjoy.

You can now decide to visit the "Thread Tools" link at the top right of the first page of the link to then mark your thread as "Solved". That will hep others find what your solution was with their similar problems.

---

### Post by Paddy Landau on 2024-02-13
I know that I'm a little late to this, but there have been [some corruption problems]("https://www.phoronix.com/news/OpenZFS-Encrypt-Corrupt") found with ZFS and encryption. That's not to say that this was your problem, but you should be aware.

---

### Post by MAFoElffen on 2024-02-13
@Paddy Landau ---
The has been addressed and is taken care of (fixes released). Check this thread in our DEV section and all the LaunchPad Bugs...
RE:
[https://ubuntuforums.org/showthread.php?t=2492927](https://ubuntuforums.org/showthread.php?t=2492927)
[https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2044969)
[https://bugs.launchpad.net/ubuntu/jammy/+source/zfs-linux/+bug/2044657](https://bugs.launchpad.net/ubuntu/jammy/+source/zfs-linux/+bug/2044657)

There is also another recent bug related to Grub2 & snapshots on bpool... 
RE: 
[https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999)

That one is current, a fix found with patches for Dev Noble, but requires backports before it will be resolved for Focal and Jammy. I currently have 4 work-arounds to help with that one... 1fallen and I 'keep busy' behind the curtains trying to work out issues related to ZFS for Ubuntu. But neither of those bugs are related to what was happening with this OP.

---

### Post by Paddy Landau on 2024-02-13
Thank you for the information, MAFoElffen. That was quick work.

---


---
title: "Ubuntu 19.10 died after extending lvm root volume"
date: 2019-12-07
forum: Desktop Environments
---

### Post by Wojciech_Marusiak on 2019-12-07
Hi. I was running out of disk space on lvm with one disk so I added another one to my setup, I extended all nicely and it worked until first reboot.

Here is my setup
```
lsblk
NAME                     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0                      7:0    0  1.4G  1 loop /rofs
sr0                       11:0    1  1.5G  0 rom  /cdrom
vda                      252:0    0    4T  0 disk
&#9500;&#9472;vda1                   252:1    0    1M  0 part
&#9492;&#9472;vda2                   252:2    0    4T  0 part
  &#9500;&#9472;vgubuntu--tor-root   253:0    0    5T  0 lvm
  &#9492;&#9472;vgubuntu--tor-swap_1 253:1    0  976M  0 lvm
vdb                      252:16   0    1T  0 disk
&#9492;&#9472;vdb1                   252:17   0 1024G  0 part
  &#9492;&#9472;vgubuntu--tor-root   253:0    0    5T  0 lvm

```
```
pvs
  PV         VG           Fmt  Attr PSize     PFree
  /dev/vda2  vgubuntu-tor lvm2 a--     <4.00t    0
  /dev/vdb1  vgubuntu-tor lvm2 a--  <1024.00g    0

```
```
vgs
  VG           #PV #LV #SN Attr   VSize  VFree
  vgubuntu-tor   2   2   0 wz--n- <5.00t    0

```
```
 lvs
  LV     VG           Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu-tor -wi-a-----  <5.00t
  swap_1 vgubuntu-tor -wi-a----- 976.00m

```

Now when the system boots I've got following error
```
[COLOR=#242729][FONT=Arial]grub error: disk 'lvid/caoMWu-o417-GMgh-6vFj-1qrw-iJMi-ypwm0f/Z2eotR-N0HN-nrol-3hUd-odMB-GzHy-4PrsnL' not found. Entering rescue mode..[/FONT][/COLOR]
```

This is my fstab
```
/dev/mapper/vgubuntu--tor-root /               ext4    errors=remount-ro 0       1
/dev/mapper/vgubuntu--tor-swap_1 none            swap    sw              0       0

```

```
blkid
/dev/mapper/vgubuntu--tor-root: UUID="170035e0-ef7e-45f3-8e1d-b20951974996" TYPE="ext4"
/dev/sr0: UUID="2019-10-17-12-50-28-00" LABEL="Xubuntu 19.10 amd64" TYPE="iso9660" PTUUID="6e460c94" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/vda1: PARTUUID="9659d071-b1fc-4f63-8699-83f3096e23a3"
/dev/vda2: UUID="7yQAwO-Ciqb-ZsfN-xHcc-4wvV-4d1s-VviIha" TYPE="LVM2_member" PARTUUID="bcf28fec-73f6-49a8-95b5-8733c2e59793"
/dev/vdb1: UUID="BhwH1e-E1xm-fxa9-jM7W-FrwJ-SC6U-U8cRpG" TYPE="LVM2_member" PARTUUID="6c4a93ad-01"
/dev/mapper/vgubuntu--tor-swap_1: UUID="feb67f36-7d7e-4ae1-be16-60b9eb0463d0" TYPE="swap"

```

```
ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Dec  7 21:36 170035e0-ef7e-45f3-8e1d-b20951974996 -> ../../dm-0
lrwxrwxrwx 1 root root  9 Dec  7 21:36 2019-10-17-12-50-28-00 -> ../../sr0
lrwxrwxrwx 1 root root 10 Dec  7 21:36 feb67f36-7d7e-4ae1-be16-60b9eb0463d0 -> ../../dm-1



```

I've tried chrooting to ubuntu and updating initramfs without success.
[IMG]https://i.imgur.com/gFWqG1x.png[/IMG]
[IMG]https://imgur.com/gFWqG1x[/IMG]

---

### Post by Dennis N on 2019-12-07
The first thing that comes to mind is to check the lvmid string with vgs and lvs to be sure the lvmid that grub is looking for in order to boot still exists.
```
run
sudo vgs -o vg_name,vg_uuid
sudo lvs -o lv_name,lv_uuid
construct the lvmid string of the root lv using the outputs like this:
vg_uuid/lv_uuid

```Compare this lvmid value to the error message. if different, fix the lvmid string in grub.cfg in EFI system partition. if not different, no further suggestions come to mind at the moment.

---

### Post by TheFu on 2019-12-07
It won't help, but this is an example why I keep the OS in a separate LV from anything else.  10TB for / seems excessive.
/ should probably be 25GB
/home 50GB, perhaps
Then put huge data somewhere else.

Am I reading that correctly? 10TB for a VM?  

BTW, this is a really handy command:```

lsblk -o name,size,type,fstype,mountpoint
```

Long ago, I lost all my data by using LVM to concatenate storage from 2 different disks.  Please be very careful and have excellent backups.

---


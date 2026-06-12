---
title: "dual boot dilemna"
date: 2009-01-31
forum: General Help
---

### Post by tjksn on 2009-01-31
Ok, here's the story.  I'll try to keep it short.  After installing ubuntu ultimate to a second partition on a second SATA drive I could not boot into anything except the live cd.  Grub always gave an error 22.  I installed a copy of 7.10 that I had used before and still got the same error.  I've searched for solutions and tried repairing Grub to no avail.  I've also tried using ms-sys to restore the windows mbr, but got errors about no sda in /dev so this didn't work.  The reason I have not tried my windows setup cd is two fold: 1) I need a floppy that has the SATA drivers so setup can recognize the drives, 2) I don't remember the administrator password (apparently made a really good one) so I cannot get into recovery console.

I next thought I'd try the following: switch the drive cables on the motherboard, install ubuntu on the first drive (partitioned into an NTFS, ext3 boot, ext3 root, linux swap), install Grub on this drive since it is now hd0.  The intention was this would allow me to load up windows using the Grub bootloader.  The windows portion of menu.lst is below.

title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

the map lines were originally (hd0) (hd1) then (hd1) (hd0).  I tried switching them based on a post on another forum.  What I get now when I try to load windows is NTLDR is missing.  I have looked on the windows drive and NTLDR and NTdetect.com are both there.  Is the fact that the MBR on the windows drive got messed up the problem?  Or is there some other workaround I can try?

---

### Post by 73ckn797 on 2009-01-31
What is the result in terminal of:

```
sudo fdisk -l
``` ?

---

### Post by tjksn on 2009-01-31
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13f1e9b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31981   256887351    7  HPFS/NTFS
/dev/sda2   *       31982       35094    25005172+  83  Linux
/dev/sda3           35095       59464   195752025   83  Linux
/dev/sda4           59465       60801    10739452+  82  Linux swap / Solaris

Fdisk output below.

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39c9b696

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e395

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4864    39070048+   7  HPFS/NTFS

---

### Post by Boomhauer on 2009-01-31
run these commands from a terminal 
```
sudo mount /dev/sda2 /mnt

cat /mnt/boot/grub/menu.lst
``` and then paste here what the last command returns.

---

### Post by tjksn on 2009-01-31
dad@dad-desktop:~$ cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory

---

### Post by Boomhauer on 2009-01-31
was /dev/sda2 your /boot partition?

---

### Post by tjksn on 2009-01-31
Yes.  SDA3 is the / or root partition.

SDB is where windows resides.

---

### Post by Boomhauer on 2009-01-31
if you still have /dev/sda2 mounted at /mnt, what does ```
cd /mnt

ls

```return

---

### Post by tjksn on 2009-01-31
abi-2.6.27-11-generic         memtest86+.bin
abi-2.6.27-7-generic          System.map-2.6.27-11-generic
config-2.6.27-11-generic      System.map-2.6.27-7-generic
config-2.6.27-7-generic       vmcoreinfo-2.6.27-11-generic
grub                          vmcoreinfo-2.6.27-7-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.27-11-generic
initrd.img-2.6.27-7-generic   vmlinuz-2.6.27-7-generic
lost+found

---

### Post by tjksn on 2009-01-31
How come I cannot see the boot partition in nautilus browser?

---

### Post by tjksn on 2009-01-31
Never mind, I think I figured it out.  Sda2 is shown as the boot folder under filesystem.

---

### Post by Boomhauer on 2009-01-31
can you find your menu.lst in there?

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tjksn on 2009-01-31
I'll get that in a few moments.  I did manage to repair the MBR using ms-sys, which I could not do with the live DVD, and after unplugging the new drive with Linux on it my windows drive booted fine.  Makes me wonder if it might be something with how this older bios handles SATA.

Tom

---

### Post by tjksn on 2009-01-31
The script for getting the boot_info_script did not work with the live DVD.  Below is the script in menu.lst.

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ed81e007-715c-465c-90a2-04336b676861
kernel		/vmlinuz-2.6.27-11-generic root=UUID=700cc873-9b01-4eb9-82da-8fbfdf7ac635 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ed81e007-715c-465c-90a2-04336b676861
kernel		/vmlinuz-2.6.27-11-generic root=UUID=700cc873-9b01-4eb9-82da-8fbfdf7ac635 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ed81e007-715c-465c-90a2-04336b676861
kernel		/vmlinuz-2.6.27-7-generic root=UUID=700cc873-9b01-4eb9-82da-8fbfdf7ac635 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ed81e007-715c-465c-90a2-04336b676861
kernel		/vmlinuz-2.6.27-7-generic root=UUID=700cc873-9b01-4eb9-82da-8fbfdf7ac635 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ed81e007-715c-465c-90a2-04336b676861
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

I've tried changing the mapping, but that didn't work.  I've also tried making changes in the boot.ini file for windows where it denotes the drives and partions, but that didn't work either.

---

### Post by caljohnsmith on 2009-01-31
Since you can't post the script output, there are probably three different possible entries to use for Windows, and you've all ready tried one of them, so how about trying the other two:
```
title       Windows XP (hd0)
root       (hd0,0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
If you need help editing your menu.lst, try:
```
sudo mount /dev/[COLOR="Blue"]sda2[/COLOR] /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
You have two linux partitions, so if your menu.lst is actually on sda3, just change it in the command above. Let me know how that goes or if you run into problems.

---

### Post by tjksn on 2009-01-31
I changed the root and maps as suggested and it boots fine.  Thanks for the help.  I would have figured that hd2 would point to the IDE drive since it shows up as sdc.  Just glad to have it sorted out.

---

### Post by caljohnsmith on 2009-01-31
Glad that worked OK; cheers and enjoy Windows and Ubuntu. :)

---

### Post by Rebelli0us on 2009-01-31
How do you edit menu.lst? 

How do you make a backup copy of menu.lst before you make changes?

How do you restore the backup copy to your original menu.lst?

---


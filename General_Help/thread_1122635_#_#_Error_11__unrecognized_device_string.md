---
title: "# # Error 11 : unrecognized device string"
date: 2009-04-11
forum: General Help
---

### Post by cmagan on 2009-04-11
hi
i got a new computer
first i installed ubuntu and than vista ultimate
i used the live cd to recover the grub and than qgrubeditor to add vista entry, than i got error 11.

please help me to solve the error 11 first and than to add vista entry to menu.lst 

thanks

plzzz help

---

### Post by coffeecat on 2009-04-11
Do you get error 11 trying to boot into Ubuntu? Which version number of Ubuntu are you using? And Ubuntu or Kubuntu? Your thread tag and personal profile say different things.

Anyway, from the grub manual:

> 
11 : Unrecognized device string

This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the [Filesystem]("http://www.gnu.org/software/grub/manual/grub.html#Filesystem").Post the whole of your present /boot/grub/menu.lst and someone will help you with the error(s) in your Ubuntu stanza and with how to set up a Vista entry.

---

### Post by cmagan on 2009-04-11
i use ubuntu 8.10

my menu.lst:
default 0
timeout 3
hiddenmenu

title Ubuntu 8.10, kernel 2.6.27-11-generic
root 
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=aafdc463-541e-4994-8618-ab3d2713dad1 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=aafdc463-541e-4994-8618-ab3d2713dad1 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
root 
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=aafdc463-541e-4994-8618-ab3d2713dad1 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=aafdc463-541e-4994-8618-ab3d2713dad1 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
root 
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows Vista
root (hd0,3)
chainloader +1

---

### Post by cmagan on 2009-04-11
someone?

---

### Post by coffeecat on 2009-04-11
The most obvious mistake is that the root lines for each Ubuntu stanza are empty. They need a grub-style device number. It has to be wherever your /boot files are kept, so the root partition if you keep /boot there, or the boot partition, if you have a separate one.

For each of those Ubuntu stanzas you need:

```
root    (hdx,y)
```But you'll have to fill in the values for x and y. Do you know your partition layout? If not, post the output of:

```
sudo fdisk -l
```As far as the Vista entry is concerned, are you sure that Vista is on sda4 - partition 4, which is what (hd0,3) means?

If it doesn't work, try:

```
title Microsoft Windows Vista
root (hd0,3)
savedefault
makeactive
chainloader +1
```

---

### Post by coffeecat on 2009-04-11
> **cmagan said:**
> someone?

cmagan, do not be impatient. Waiting only half an hour before bumping is considered bad forum etiquette.

---

### Post by cmagan on 2009-04-11
here's fdisk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefce01ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2554      979965    5  Extended
/dev/sda3            2555        8928    51197952    7  HPFS/NTFS
/dev/sda4            8929       30401   172481872+   b  W95 FAT32
/dev/sda5            2433        2554      979933+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38d5cc49

   Device Boot      Start         End      Blocks   Id  System


how can i change the menu.lst?
im using now live CD

im sorry for being inpatient
its just the fact that im stuck now, but you are right

---

### Post by coffeecat on 2009-04-11
If you're using the live CD, go to the places menu, and see where you can mount the root partition of your Linux install - what appears as sda1 from fdisk. Let a nautilus window open showing your root partition and click the little pencil and paper icon on the left of the address bar. The path to your root partition will show as /media/*mountpoint*. Make a note of mountpoint. It might be as simple as 'disk'.

Now open a terminal and:

```
gksudo gedit /media/mountpoint/boot/grub/menu.lst
```Obviously, change 'mountpoint' to whatever it should be. Now you can edit menu.lst

Each root line for Ubuntu should be:

```
root    (hd0,0)
```And for Vista, should be either:

```
title Microsoft Windows Vista
root (hd0,2)
chainloader +1
```or

```
title Microsoft Windows Vista
root (hd0,2)[FONT=monospace]
[/FONT]savedefault[FONT=monospace]
[/FONT]makeactive[FONT=monospace]
[/FONT]chainloader +1
```Your (hd0,3) was wrong - grub numbering is a little peculiar. It starts from zero. And, to be honest, I don't know whether the savedefault[FONT=monospace] and [/FONT]makeactive lines are necessary. You'll need to experiment.

One other thing I noticed. Your sda1 (Linux root) has the boot flag set. This doesn't do any harm but is unnecessary - Linux doesn't need a boot flag. However, sda3, your Vista partition (I am assuming) does not have the boot flag set. It's possible that when booting from grub you don't need a boot flag, but Windows can be very fussy about this. If Vista won't boot, use the live CD System > Administration > Partition Editor to set the boot flag.

---

### Post by cmagan on 2009-04-11
thanks
helped me alot!!!!!!!!!

---


---
title: "Help!!!"
date: 2006-04-11
forum: Desktop Environments
---

### Post by arcasa on 2006-04-11
Hi,
    I have an Acer Aspire 1350 with windows and breezy as os. (i use GRUB to choose between them)

Windows has had a problem (cough cough) and wont load anymore, so i tried to use bootable disks from both ubuntu and windows to whitewash over the lot. Failed.

my computer wont boot from disks, i tried telling it straight from a multiboot selection to load from disk, nothing.

So i ask of you clever people if ubuntu has some program or feature that can completely wipe everything off my HD, i really dont want to have to pay out £60.00 to get it wiped by a sweaty man with glasses and more spots than me over a counter.

please help, 
                   your loyal Arcasa

---

### Post by taurus on 2006-04-11
You want to erase everything on your harddrive!  Well, you can do that with a LiveCD.  If you don't have one, download it and boot from it.  When you see Gnome, click Applications -> Accessories -> Terminal.  Then type
```

sudo fdisk /dev/hda  <-- assuming you want to wipe out the first harddrive

```
Use d to delete partitions and save the changes with w...

---


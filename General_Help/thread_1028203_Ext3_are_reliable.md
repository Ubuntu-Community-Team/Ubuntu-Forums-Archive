---
title: "Ext3 are reliable?"
date: 2009-01-02
forum: General Help
---

### Post by psychok9 on 2009-01-02
Today, I power-up my pc... and I get this message:
```
ACPI: Aborted because bad gzip magic numbers.
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-bloc(0,0).
```

I must select 2.6.27-9-generic for boot up correctly.
Previous kernel is 2.6.27-11, used without problems for some weeks.

Linux is safe on Ext3 partition? How can I protect my data from filesystem loss?

---

### Post by Nepherte on 2009-01-02
ext3 is a very reliable journaling filesystem but that doesn't mean you can't have problems with it. A failing hard drive will eventually mess up the filesystem too so sometimes you *think* it's the filesystem, but in reality it's the disk itself.

The only way to really protect your data is to backup, preferable multiple times. RAID setups might help too (especially RAID1 and RAID5).

---

### Post by Copernicus1234 on 2009-01-02
Have you compiled the kernel yourself? Maybe you have not compiled in support for the file system.

---

### Post by Arenlor on 2009-01-02
If you press esc as grub goes to load and press e to edit the line it'll give some info like:
```
title           Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid            9a7be6fd-e532-488a-a9d3-714937a3921b
kernel          /vmlinuz-2.6.28-4-generic root=UUID=ae5c62e1-2d30-4f59-af88-381$
initrd          /initrd.img-2.6.28-4-generic
quiet
```
Can you post it here?

---

### Post by albinootje on 2009-01-02
> **psychok9 said:**
> Today, I power-up my pc... and I get this message:
```
ACPI: Aborted because bad gzip magic numbers.
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-bloc(0,0).
```

I must select 2.6.27-9-generic for boot up correctly.
Previous kernel is 2.6.27-11, used without problems for some weeks.


Are you using Intrepid/8.10 ?
Then you probably mean 2.6.27-9-generic is not working, and you're using 2.6.27-7-generic as a fall-back now, is it not ?

Can you post your /boot/grub/menu.lst please ?

Try :
```

sudo touch /forcefsck

```
And reboot to do a forced filesystem check.

If all is fine do a :
```

sudo apt-get install --reinstall linux-image-2.6.27-9-generic
sudo rm /forcefsck

```

---

### Post by psychok9 on 2009-01-02
> **Copernicus1234 said:**
> Have you compiled the kernel yourself? Maybe you have not compiled in support for the file system.

I've installed from Ubuntu proposed repistory with synaptic... and I use only ext3 fs.

> **Arenlor said:**
> If you press esc as grub goes to load and press e to edit the line it'll give some info like:
```
title           Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid            9a7be6fd-e532-488a-a9d3-714937a3921b
kernel          /vmlinuz-2.6.28-4-generic root=UUID=ae5c62e1-2d30-4f59-af88-381$
initrd          /initrd.img-2.6.28-4-generic
quiet
```
Can you post it here?
I've removed the 2.6.27-11 kernel with apt-get... this is my actual launcher:
(Before I've tried 2.6.27-11 recovery mode without success).
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		bd8359a2-56fa-4d64-afa6-e72a4a875658
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=bd8359a2-56fa-4d64-afa6-e72a4a875658 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```

> **albinootje said:**
> Are you using Intrepid/8.10 ?
Then you probably mean 2.6.27-9-generic is not working, and you're using 2.6.27-7-generic as a fall-back now, is it not ?

Can you post your /boot/grub/menu.lst please ?

Try :
```

sudo touch /forcefsck

```
And reboot to do a forced filesystem check.

If all is fine do a :
```

sudo apt-get install --reinstall linux-image-2.6.27-9-generic
sudo rm /forcefsck

```

Ok I'll try!

---

### Post by psychok9 on 2009-01-02
**albinootje**
Filesystem check is done, but how can I see the log?

---

### Post by albinootje on 2009-01-02
> **psychok9 said:**
>  Filesystem check is done, but how can I see the log?

Afaik there's no log for fsck by default. 
You can see output as text if you boot in text-mode.

And you can check /lost+found to see whether some filesystem check saved file-parts ended up there.

Can try booting with this boot option : acpi=off
See here for instructions how to use that : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by psychok9 on 2009-01-02
> **albinootje said:**
> Afaik there's no log for fsck by default. 
You can see output as text if you boot in text-mode.
And you can check /lost+found to see whether some filesystem check saved file-parts ended up there.
I've rebooted in normal mode... and lost+found are empty (I can access it only with sudo -s).
> Can try booting with this boot option : acpi=off
See here for instructions how to use that : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

With kernel 2.6.27.9 boot correctly (and in the past with 2.6.27.11), i don't think it's a problem with ACPI.

I've attached the results of *sudo smartctl -A /dev/sdb* command.

---

### Post by Nepherte on 2009-01-02
> **psychok9 said:**
> I've installed from Ubuntu proposed repistory with synaptic... and I use only ext3 fs.
May I remind you that the proposed repository is for testing purposes only and isn't considered stable?  Unless you are a developper or you'd like to help developpers out (i.e. provide information about your experiences), you shouldn't install from the proposed repository.

---


---
title: "Ubuntu working with windows"
date: 2009-02-06
forum: General Help
---

### Post by ubntoo on 2009-02-06
I installed ubuntu yesterday and I made a partition for it because I want to keep windows vista basically for photoshop but now when I put on the pc there's the boot OS menu (it has 3 choises of Ubuntu) and I can't use Windows but it's still on my HDD.

What can I do??

---

### Post by lykwydchykyn on 2009-02-06
Basically, you need to add an entry for it in the bootloader configuration.  

First we need to figure out where Vista is on your system, so post the output of this command:
```

sudo fdisk -l

```

---

### Post by 73ckn797 on 2009-02-06
> **ubntoo said:**
> I installed ubuntu yesterday and I made a partition for it because I want to keep windows vista basically for photoshop but now when I put on the pc there's the boot OS menu (it has 3 choises of Ubuntu) and I can't use Windows but it's still on my HDD.

What can I do??

If you are not afraid to use terminal go to Applications/Accessories/Terminal. Once there enter the following:

```
gksudo gedit /boot/grub/menu.lst
```

That will display the grub boot menu. At the end of the file does it list Windows at all? Post that info in a reply.

The graphical way to at least view the info without being able to edit it or save it would be to go to Places/My Computer/File System/boot/grub and open "menu.lst". You can copy the last section and paste it into your reply.

Also, in terminal, enter the following:

```
sudo fdisk -l
```

Paste that info in a reply.

---

### Post by ubntoo on 2009-02-06
mmmkay I did it and the response was this:
> josh@Josh:~$ sudo fdisk -l
[sudo] password for josh: 

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3e7bce35

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *       22134       24321    17575110   83  Linux
josh@Josh:~$ 
josh@Josh:~$ 





by the way my ubuntu is in spanish

---

### Post by ubntoo on 2009-02-06
Ok I did the other thing with boot/grub and here it is:
> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		02e6ca2d-a1a6-4f25-b004-d13020a53425
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=02e6ca2d-a1a6-4f25-b004-d13020a53425 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		02e6ca2d-a1a6-4f25-b004-d13020a53425
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=02e6ca2d-a1a6-4f25-b004-d13020a53425 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		02e6ca2d-a1a6-4f25-b004-d13020a53425
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



help me plz...I love Ubuntu but I'll miss a lot of files if I can't do anything :S now I'm kinda scared

---

### Post by 73ckn797 on 2009-02-06
> **ubntoo said:**
> mmmkay I did it and the response was this:


by the way my ubuntu is in spanish

By the looks of things Windows is not there. It is a completely Ubuntu/Linux drive. That is why there is no grub menu listing for Windows.

I cannot read Spanish but there is only the Linux info showing up in the "fdisk" info.

---

### Post by ubntoo on 2009-02-06
mmmm kinda strange because my hd is a 200gb one an ubuntu only show 13gb on the device (i did a 18gig partition)

---

### Post by caljohnsmith on 2009-02-06
As 73ckn797 all ready pointed out, your drive doesn't list any NTFS partitions where Windows could be. But the good news is that the only partition on the drive (your Ubuntu partition) is near the end of the drive, so it may be possible to recover your lost Windows partition. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and which one looks like it has your Vista root directory. We can work from there if you want.

---


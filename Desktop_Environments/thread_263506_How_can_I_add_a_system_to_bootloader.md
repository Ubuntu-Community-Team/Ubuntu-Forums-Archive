---
title: "How can I add a system to bootloader ?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Matodo on 2006-09-23
Hello

I just installed Backtrack 1.0 (a Slax based distribution), I thought it will install GRUB and my Ubuntu and Windows XP will appear in the boot menu, but it didn't happened. My boot menu's gone and it automatically enters to Backtrack without asking me. So I reinstalled GRUB using Ubuntu's Live-CD, but Backtrack didn't appear in boot menu. I just had the same boot menu before installing Backtrack.

What should I do to add it ?

[I]Useful informations :
Ubuntu is installed in hda6, Windows XP in hda1, Backtrack in hda7.
Should I post the GRUB menu file ?[/I]

Thanks

---

### Post by Ramses de Norre on 2006-09-23
This might work: ```
title    BackTrack
root    (hd0,6)
kernel    /boot/vmlinuz root=/dev/hda7 ro
initrd    /boot/initrd.img
savedefault
boot
```

You'll need to edit the vmlinuz and initrd.img path according to what is installed in backtrack's /boot/ folder. If there is no initrd you can just remove that line from the section.
Add the section below the "### END DEBIAN AUTOMAGIC KERNELS LIST" part so it will remain on ubuntu kernel upgrades.

---

### Post by bernied on 2006-09-23
You need to add an entry at the end of the file /boot/grub/menu.lst It should look something like this:
```
title Backtrack
root (hd0,6)
chainloader +1
boot
```The doubtful bit in that entry is the 'root (hd0,6)'. Grub has a different way of numbering disks and partitions - for disks it starts counting at 0, so hd0 is instead of hda, and partitions also start at 0, so (hd0,0) is hda1. But it isn't always an exact match. So try that (hd0,6) first, and let us know what happens.

---

### Post by bernied on 2006-09-23
The difference between the two solutions above is that Ramses loads the specific kernel and initrd for Backtrack, where mine loads the bootloader that's included in the Backtrack install. Ramses is more direct, but you will have to get the names of the kernel and initrd correct. There might also be some kernel options needed, like setting the ramdisk sizes, but see if either of these work first.

---

### Post by Matodo on 2006-09-23
Thanks for your answers
I tried to add this

```

# This entry was added by Matodo
# on /dev/hda7
title		BackTrack v.1.0
root		(hd0,5)
chainloader	+1
boot

```

I got the root-value by typing this commands
```

sudo grub
find /boot/grub/stage1

```

I rebooted my PC, and I chose "BackTrack v.1.0" from the boot menu to find this message
> 
       Booting BackTrack v.1.0
root (hd0,6)
  Filesystem type is ext2fs, partition type 0x83
chainloader +1
Error 13: Invalid or unsupported executable format
Press Any key to continue

Pressing any key returns me to the boot menu.

Any idea ?

---

### Post by Ramses de Norre on 2006-09-23
(hd0,5) is ubuntu, backtrack is on (hd0,6), and it has to have grub installed on its own partition in order to be able to chainload it.

---

### Post by Matodo on 2006-09-24
I tried (hd0,6), but I got the same error message :(

---

### Post by bernied on 2006-09-24
OK, I was wrong. You should try the method in Ramses first post, but the parameters probably need to change a bit. I found a grub entry for an old slax install on a usb stick - this worked for me, but that's no guarantee that it will work for you. Try this:
```
title 		BackTrack
root 		(hd0,6)
kernel 		/vmlinuz max_loop=255 initrd=initrd.gz init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=4444 root=/dev/ram0 rw
initrd		/initrd.gz
boot
```Failing this you may need to find the boot parameters off the live-cd

---

### Post by Ramses de Norre on 2006-09-24
Are you sure about the stuff like "root=/dev/ram0" ??

---

### Post by bernied on 2006-09-24
I got these boot parameters from the /boot/DOS/config file on my slax live-cd install. I'm not sure if this was straight off the cd, or from the filesystem when slax was running. Hopefully for you, slax won't have changed their boot setup much in the last year or so. See if you can find that file, then map the parameters into grub's format. Especially look out for changes in the size of the ramdisk.

---

### Post by bernied on 2006-09-24
This usb slax works, booting from grub. I'm pretty sure that the slax method gets all it needs to startup from the ramdisk, then once that's loaded and running it goes looking for itself (for the rest of it's files) on removable media. But this may not work for a hard-drive install - as I recall they recommended that you boot the live-cd, then copy most of the live filesystem straight onto your partition, then setup fstab for proc etc. It was all magic to me at the time. I think the method for usb stick was different - you copied the live-cd onto the stick. It will depend on how Matodo has done the install.

Can you point us to the installation instructions Matodo?

---

### Post by Ramses de Norre on 2006-09-24
```
title    backtrack
root    (hd0,6)
kernel    /boot/vmlinuz root=/dev/hda7 rw
boot
```

What about this?
Check the path for vmlinuz, there could be version numbering in the file name.

---

### Post by Matodo on 2006-09-24
> **Ramses de Norre said:**
> ```
title    backtrack
root    (hd0,6)
kernel    /boot/vmlinuz root=/dev/hda7 rw
boot
```

What about this?
Check the path for vmlinuz, there could be version numbering in the file name.

Thank you very much, it works now

---

### Post by SRX on 2007-07-13
On the kernel entry why do you have to write

root=/dev/hda7

---

### Post by bernied on 2007-07-13
This is to tell the kernel where the root filesystem is located.

---


---
title: "Ubuntu listed twice in bootmenu"
date: 2009-01-25
forum: General Help
---

### Post by johndoe20081026 on 2009-01-25
hello,
i have installed ubuntu (32 bit ver.) on my notebook, which had windows xp before on it

well everything seems to be fine but on boot i have exactly the same options from ubuntu listed twice. it looks like this: (without the colored highlights:)
> [COLOR="RoyalBlue"]ubuntu 8.10, kernel 2.6.6-27-9-generic
ubuntu 8.10, kernel 2.6.6-27-9-generic (recovery mode)[/COLOR]
[COLOR="Lime"]ubuntu 8.10, kernel 2.6.6-27-9-generic
ubuntu 8.10, kernel 2.6.6-27-9-generic (recovery mode)[/COLOR]
ubuntu 8.10, memtest86+
Other operating systems: 
win xp..

when i enter sudo fdisk -l, it shows this
> device	boot	start	end	Blocks		Id	System
dev/sda1	*	1	1912	15358108+	7	HPFS/NTFS
dev/sda2	 	1913	21034	153597465	7	HPFS/NTFS
dev/sda3	 	21035	38055	136721182+	83	Linux
dev/sda4	 	38056	38913	6891885		82	Linux swap / Solaris
so i don't know, i'm just a beginner but it doesn't seem that i have installed it twice. or is this "swap partition" listing like second ubuntu? 

can someone tell me what should i do without screwing up the current installation of ubuntu/xp?

[size=1]also, excuse me if this forum account made lame posts before, this is a public account accessed via bugmenot[/size]

---

### Post by JamieKitson on 2009-01-25
Have you had a look in /boot/grub/menu.list? It's probably safe to comment out the two duplicate lines.

---

### Post by johndoe20081026 on 2009-01-25
thanks for your answer

my humble apologies but it seems that i mislooked the last number on the boot menu. i could have sworn there was 9 instead of 7 befiore [img]http://files.abandonia.com/extras/Forum%20Emoticons/One%20World%20Syndicate/doh.gif[/img]
> 
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d5f48e31-0721-451d-80b8-eceb9df5b5fa
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d5f48e31-0721-451d-80b8-eceb9df5b5fa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d5f48e31-0721-451d-80b8-eceb9df5b5fa
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d5f48e31-0721-451d-80b8-eceb9df5b5fa ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-**[COLOR="Red"]7[/COLOR]**-generic
uuid		d5f48e31-0721-451d-80b8-eceb9df5b5fa
kernel		/boot/vmlinuz-2.6.27-**[COLOR="Red"]7[/COLOR]**-generic root=UUID=d5f48e31-0721-451d-80b8-eceb9df5b5fa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-**[COLOR="Red"]7[/COLOR]**-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-**[COLOR="Red"]7[/COLOR]**-generic (recovery mode)
uuid		d5f48e31-0721-451d-80b8-eceb9df5b5fa
kernel		/boot/vmlinuz-2.6.27-**[COLOR="Red"]7[/COLOR]**-generic root=UUID=d5f48e31-0721-451d-80b8-eceb9df5b5fa ro  single
initrd		/boot/initrd.img-2.6.27-**[COLOR="Red"]7[/COLOR]**-generic

title		Ubuntu 8.10, memtest86+
uuid		d5f48e31-0721-451d-80b8-eceb9df5b5fa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


although, this is still strange, because i have installed ubuntu only once. or is this "swap partition" listing? why does it have different version then? can i simply remove it from the list?

also, what does the "quiet" under some of the options mean?

---

### Post by 73ckn797 on 2009-01-25
It appears to have been a kernel upgrade. Probably happened on a typical update. Nothing to worry about and you can simply add "#" at the first of the lines with the ".7" kernel listed or completely remove those lines.

---

### Post by johndoe20081026 on 2009-01-25
ok thanks a bunch!

---

### Post by nubnux on 2009-01-25
Same thing here. Only that I cannot remove or change those lines. I keep getting a **"You do not have the permissions necessary to save the file."** error.

---

### Post by diablo75 on 2009-01-25
> **nubnux said:**
> Same thing here. Only that I cannot remove or change those lines. I keep getting a **"You do not have the permissions necessary to save the file."** error.

You have to edit the menu.lst file with root privilages.  So, for instance, type:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by golusweet on 2009-01-25
It's just cause of Kernel upgrade.

1. sudo gedit /boot/grub/menu.lst
 
Now remove the old entry,and save it.:p

---

### Post by nubnux on 2009-01-25
Well, thx. That seemed to work.

---

### Post by mb_webguy on 2009-01-25
Actually, if you just remove the current extra entry, you'll still see another the next time there's a kernel update.  If you want to make sure you only ever see one entry for Ubuntu in the GRUB menu, open the GRUB menu.lst in gedit (using "gksudo gedit /boot/grub/menu.lst", since you should always use gksu or gksudo when starting GUI applications as root), and look for the line "# howmany=all".  Change that to "# howmany=1", then save and exit.  Now enter the command "sudo update-grub" to update the GRUB menu.

---

### Post by arepaking on 2009-01-28
> **mb_webguy said:**
> Actually, if you just remove the current extra entry, you'll still see another the next time there's a kernel update.  If you want to make sure you only ever see one entry for Ubuntu in the GRUB menu, open the GRUB menu.lst in gedit (using "gksudo gedit /boot/grub/menu.lst", since you should always use gksu or gksudo when starting GUI applications as root), and look for the line "# howmany=all".  Change that to "# howmany=1", then save and exit.  Now enter the command "sudo update-grub" to update the GRUB menu.

Webguy,
By doing this. The last kernel will be removed from the system? I think the best way to get rid of the old kernel version is by uninstalling them instead of commenting them.

Right now, my Grub shows 3 kernel version but I do not know how to PROPERLY uninstall the old one.

Any guidance will be highly appreciate it.

Kind Regards,
Arepaking

---

### Post by mb_webguy on 2009-01-28
No, the old kernel will no be removed from the system, but unless you're extremely short on storage space on your root partition (and linux kernels are only about 100KB), it's not imperative that you do remove old kernels.  The reason old kernels are added to the GRUB menu is so that you have the option to boot using the old kernel in case you encounter errors with the newer kernel.  For that reason, it's usually a good idea to set the howmany variable to 2.

However, if you've been using a particular kernel for a while and haven't encountered any problems, you can remove the old kernel using Synaptic.  Search for "linux-image", and look for packages that start with that text.  Look for the one with the kernel version you want to remove, and uninstall it.  It's VERY IMPORTANT that don't remove your current kernel or anything that isn't a linux-image.  You can break Ubuntu if you remove the wrong kernel.

But as I said, it's safe to leave old kernels on your system, and they really don't take up much space on your hard drive.

---

### Post by arepaking on 2009-01-28
Understood. Thank you very much for this useful information about kernels.

Kind Regards,
AK

---


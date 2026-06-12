---
title: "GRUB freeze"
date: 2005-05-29
forum: Desktop Environments
---

### Post by FunkieDunkie on 2005-05-29
I have a problem with grub - everything was working fine until I rebooted... and now all I get is the word "GRUB" and the machine sits beeping at me.

Last night, before rebooting, I installed VMWare 5. To get it to install I needed to have gcc, so following instructions elsewhere I did:

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

VMWare then properly installed, and everything was OK.

But now I can't reboot into Linux. Could either of the things I have done above cause this problem?

My machine is dual boot with Windows XP, using XP's bootloader to boot my Linux install at /dev/hda5. This has been working fine for a long time.

I have tried reinstalling GRUB from a rescue system (grub-install /dev/hda5) which gives the appearance of working, but then when I reboot, just the same GRUB message.

Please help!

---

### Post by cudaman73 on 2005-05-29
[QUOTE=FunkieDunkie]
My machine is dual boot with Windows XP, using XP's bootloader to boot my Linux install at /dev/hda5. This has been working fine for a long time.

I have tried reinstalling GRUB from a rescue system (grub-install /dev/hda5) which gives the appearance of working, but then when I reboot, just the same GRUB message.[/QUOTE]

I didn't know you could use NTLDR to boot linux partitions. I think what you mean to say is that you have a dual boot with XP, using grub to boot either install. in case you want to compare your entry to mine, i'll give you what my menu.lst looks like (well, the relevant parts anyways)

```
title           Ubuntu, kernel 2.6.10-5-386 
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot
```

and that's using the default kernel

---

### Post by FunkieDunkie on 2005-05-29
Yes, am using NTLDR to boot Linux (quite easy to set up, has served me well for a long time).

When it comes to Grub I don't really know what I'm doing. Where can I find my menu.lst file?

(I have no idea what format this will have, am resorting to links on system rescue cd. Am hoping this reads normally ;-)

---

### Post by cudaman73 on 2005-05-29
[QUOTE=FunkieDunkie]Yes, am using NTLDR to boot Linux (quite easy to set up, has served me well for a long time).

When it comes to Grub I don't really know what I'm doing. Where can I find my menu.lst file?

(I have no idea what format this will have, am resorting to links on system rescue cd. Am hoping this reads normally ;-)[/QUOTE]

menu.lst is... 

```
m3r1k@m3r1kb0x:~$ locate menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/doc/grub/examples/menu.lst
/boot/grub/menu.lst
```

so there you go. /boot/grub/menu.lst is where it is. It might be a syntax error in your menu.lst (i can paste mine in phpfi if you wish), or it could be an internal bug with grub. Perhaps you should try reinstalling grub. Personally, I know more about grub than i do ntldr, so if you want, i can help you set up grub on the mbr and get it booting both windows and linux.

---

### Post by BootySlap on 2005-06-06
I have the same problem after installing Ubuntu with GRUB and then using NTLDR to boot the GRUB bootsector, grub just freezes on me. 

NTLDR works fine when booting LILO but grub doesnt seem to want to boot ?

---


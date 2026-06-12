---
title: "GRUB Menu error 17 after deleting ubuntu partition"
date: 2009-05-03
forum: General Help
---

### Post by pedramslhr on 2009-05-03
I have a Dell Vostro 1510 laptop with Win Vista Home Basic and ubuntu 8.04
I needed to install windows XP so I simply deleted my root partition via windows vista to make another drive for installing Win XP (because it was not possible to have more than 4 primary drives!). But after restarting my laptop following message was displayed:

GRUB loading stage 1.5.
GRUB loading, please wait ....
Error 17

(I tried start up repair available in Win vista disk, but it didn't work)now what can I do to load Windows vista?I really need it know

thanks in advance!

---

### Post by Melk79 on 2009-05-03
By editing your partitions in Windows, grub didn't catch the updates to your partitions and is throwing this error because it thinks you should still have ubuntu.  Download Supergrub [disk]("http://www.supergrubdisk.org/") and it can restore you boot record to the current partitions. If you reinstalled Windows, the Windows boot manager would replace grub and handle it as before.

---

### Post by pedramslhr on 2009-05-03
I think I should install Win Xp and after that I'll edit bootloader menu to be able to log in to Vista. At the present I'm using ubuntu live disk, so I cannot burn a disk!

---

### Post by dragonbeast25 on 2009-05-03
Need flash drive, Iso already on c: or whatever and internet access





You have 2 options here. You can go to pendrivelinux.com and look for a tutorial how to put ubuntu on flashdrive you can get the iso from ubuntu.com or maby its already still on your partition. ive done this before just look. Then you can boot via flashdrive from boot menu and then burn disk using ubnutu live usb.

B: Easy one.
Find access to adnother computer and burn it through imgburn or achol 120

---

### Post by hexanol on 2009-05-03
You could just try installing Windows XP and see what happens. Nothing can go really wrong except if you somehow install XP in your Vista partition (or some stuff like that). I don't know how smart is Windows bootloader (but from what I heard and my past experience, it ain't the best to work with; maybe it's just a lack of knowledge from myself) but if it's smart enough, during setup, it'll see that there's another Microsoft OS installed in another partition and you'll then be able to pick between Vista and XP when you'll boot your computer.

If it doesn't work, well, guess you'll have to do some editing, I know it's doable, I just don't know how actually.

---

### Post by pedramslhr on 2009-05-12
Today I booted my laptop using ubuntu live cd and changed part of /var/boot/grub/menu.lst contents as follows-according to my partitions- and every thing is working:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4) [COLOR="Red"]this was (hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ece79854-d1c9-4a2d-bcdd-e095f35222bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4) [COLOR="Red"]this was (hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ece79854-d1c9-4a2d-bcdd-e095f35222bb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)[COLOR="Red"]this was (hd0,5)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
[ATTACH]113459[/ATTACH]

---


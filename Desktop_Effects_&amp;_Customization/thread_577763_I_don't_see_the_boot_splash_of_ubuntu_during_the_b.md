---
title: "I don't see the boot splash of ubuntu during the boot."
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by unixlike on 2007-10-16
Hi!

After Grub my monitor (asus a6va laptop) become black until appears the login manager.
I have this problem in feisty and now in gusty gibbon rc.

My menu.lst:

```
title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=901a8b68-7d10-4551-b709-01718a62cd61 ro quiet splash locale=it_IT
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=901a8b68-7d10-4551-b709-01718a62cd61 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=901a8b68-7d10-4551-b709-01718a62cd61 ro quiet splash locale=it_IT
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=901a8b68-7d10-4551-b709-01718a62cd61 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```

Also if i don't push alt+F1 or F2 or others the boot when i have my monitor black is more slow.
If i push alt+F1 or F2 ecc. the laptop shows me the boot in text mode and it isn't slow.
 
What can i do?

Thanks.

---

### Post by floke on 2007-10-16
It's a known issue - lets hope they fix it!
Delete 'quiet' and 'splash' from your grub stanza for a faster boot in the meantime.

---

### Post by unixlike on 2007-10-16
I have done it but i don't visualize the traditional picture of ubuntu during the boot.
What i have to do to visualize it?

Thanks,

---

### Post by floke on 2007-10-16
Wait for a fix!

---

### Post by unixlike on 2007-10-17
Ok.

---

### Post by zniavre on 2007-10-18
hello/bonjour
is it boot splash or Usplash  ?

if in case it's Usplash try this in gconf-editor >/apps/gnome-session/options/show_splash_screen and select it

bye/au revoir

---

### Post by unixlike on 2007-10-18
I have selected gconf-editor >/apps/gnome-session/options/show_splash_screen
but i don't show the splash.

If i search the image ubuntu-splash.png that is typed in  /apps/gnome-session/options/splash_image ubuntu tell me that it isn't memorized in the system.

So i think i haven't this image...is it possible?

I have this problem in feisty and now in gusty.

---

### Post by ConfidentiaL on 2007-11-09
You could try this, it worked for me:
( [http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html](http://mytechxp.blogspot.com/2007/11/fixing-long-boot-time-with-black-screen.html) )

Hope it helps :)

---


---
title: "error 15 in grub"
date: 2007-03-31
forum: Desktop Environments
---

### Post by joseph956 on 2007-03-31
I'm sorry that this has been answered so many times, but as everyone else, I feel like my situation is unique.. I hope that you will hear me out.

I didn't do anything different to my Ubuntu boot files and I didn't touch anything to do with my drives in Bios, etc.  so I'm having a hard time knowing what to un-do, or what to even do in the first place.  

I have two hard drives, one with XP and one with Ubuntu (edgy), my XP drive is of course my primary drive and the Ubuntu is secondary.  If you need to know anything else to try and help me fix my problem, please don't hesitate to ask.

The following is the listing I get after pressing "e" in grub over my linux bootup:

```
root (hd0, 0)
kernel /boot/vmlinuz-2.6.17.11-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17.11-generic
boot
```

I am slowly learning the ways of Ubuntu once I'm in, but I have yet to learn how I can now get back in, please help :confused: 

joseph

---

### Post by joseph956 on 2007-03-31
bump, 

sorry guys but im pretty desperate to get back into ubuntu and NOBODY (irc or otherwise) has offered me even a hint.

thanks!

---

### Post by Herman on 2007-03-31
```
root (hd1,0)
kernel /boot/vmlinuz-2.6.17.11-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17.11-generic
boot
```Hello joseph956,
Try that, (just change (hd0,0) to (hd1,0) and it should boot if the information you provided is correct.
                          ...and there should not be any whitespace (gap) between the comma and the '0' in (hd1,0) either.
Once you have it booted, you will of course be able to edit your /boot/grub/menu.lst file to make the change permanent. If you need more help just ask.

Regards, Herman :)

---


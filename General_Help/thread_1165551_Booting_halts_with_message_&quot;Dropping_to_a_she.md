---
title: "Booting halts with message: &quot;Dropping to a shell!&quot;"
date: 2009-05-20
forum: General Help
---

### Post by swerdna on 2009-05-20
Hi
I have Ubuntu 9.04 installed. I multiboot from an openSUSE Grub menu.
Ubuntu stopped booting normally and now this happens: Booting commences with text messages scrolling up the screen until the last few lines which look like this:
[HTML]usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
Done
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  -check rootdelay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell!

BusyBox built-in shell (ash)

(initramfs)[/HTML]

Can you tell me what to do to get booting going again?
Thanks
Swerdna

---

### Post by dsimpson on 2009-05-21
Did you try typing "exit" at the place it says (initramfs)? If you do does the boot continue? If it didn't you may have to use your livecd and modify the rootdelay by editing your /boot/grub/menu.lst

---

### Post by swerdna on 2009-05-22
Thanks for your advice.

I was mutibooting using another openSUSE's menu.lst to boot Ubuntu using:
kernel /vmlinuz
initrd /initrd.img
It seems on close inspection that the link /vmlinuz is broken and doesn't lead to the file /boot/vmlinuz-2.6.28.11-generic
So I copied the exact locations from Ubuntu's menu.lst over to openSUSE's menu.lst. And it works now, thank you.

I suppose if I have fixed the broken link, that would have worked too.

Is this a bug in Ubuntu 9.04? Should it be reported?

---

### Post by Clyssus on 2009-05-23
Hello all. I'm also experiencing this issue... I have 9.04 installed inside Windows Vista. Sometimes if I type "exit" it will continue to boot, although sometimes this does not work. Sometimes if I shut down and restart it will boot right up no problems, although I may have to do this repeatedly! 

Another issue I've been having is with the splash screen and the progress bar. If I make it through the boot it'll appear in the bottom right side of the monitor or in the bottom center without the Ubuntu logo and name. Sometimes the monitor will display an error message that the size and/or resolution is not supported which leaves me stuck, so I have to shut down and restart...  This does not happen all the time, it is intermittent, the previous issue is also intermittent... Sometimes it starts right up with no problems! 

It's a bit frustrating but I love this system... I'm still fairly new to Ubuntu, I've used it in the past but I have never moved passed being a newb with it... LOL

](*,)

---


---
title: "huge console font when not using window manager"
date: 2009-04-16
forum: Desktop Environments
---

### Post by bbt5001 on 2009-04-16
I am testing some software to be installed on an ubuntu 8.10 server, and I'm running my test on a ubuntu 8.04 desktop system. I have gnome installed on the server, but it does not start automatically (I turned off gdm for run level 2).

To mimic the same environment I turned off gdm to the test system. Now, after it boots the font at the login prompt is huge, and most of the console is not even on the screen. The letter 'l' is about 8 mm high!) The alternate consoles (accessed via ctl-alt-f1, etc.) are just as bad.

The initial text (when the system boots up to the level of grub) is just fine. Any thoughts on how I can fix the console font to a reasonable size? Where in the boot process is this being fiddled with?

---

### Post by Daisuke_Aramaki on 2009-04-16
> **bbt5001 said:**
> I am testing some software to be installed on an ubuntu 8.10 server, and I'm running my test on a ubuntu 8.04 desktop system. I have gnome installed on the server, but it does not start automatically (I turned off gdm for run level 2).

To mimic the same environment I turned off gdm to the test system. Now, after it boots the font at the login prompt is huge, and most of the console is not even on the screen. The letter 'l' is about 8 mm high!) The alternate consoles (accessed via ctl-alt-f1, etc.) are just as bad.

The initial text (when the system boots up to the level of grub) is just fine. Any thoughts on how I can fix the console font to a reasonable size? Where in the boot process is this being fiddled with?

Look at this thread

[http://ubuntuforums.org/showthread.php?t=122936]("http://ubuntuforums.org/showthread.php?t=122936")

I am not on Ubuntu. And i use framebuffer, and temporarily one can change the default tty font using the setfont command or consolechars. The fonts reside in /usr/share/consolefonts. It is also possible to add the intended font in the defaultfont file (it is the case in my distribution), don't know about ubuntu. it is /etc/rc.conf in arch for instance. If you have framebuffer support, then you can use the vga entry in grub or lilo to set a higher resolution for your tty and use the default font with ease.

---

### Post by bbt5001 on 2009-04-17
> 
Look at this thread

[http://ubuntuforums.org/showthread.php?t=122936](http://ubuntuforums.org/showthread.php?t=122936)

That was a big help. I used the kernel boot option vga=ask to get started. Some of the combinations that the system suggested did nothing (i.e., black screen requiring ctl-alt-del), but I eventually found a value that gives me sane console character sizes and does not affect my x/gnome setup. Just the ubuntu boot status progress bar page is offset severely.

> 
I am not on Ubuntu. And i use framebuffer, and temporarily one can change the default tty font using the setfont command or consolechars. The fonts reside in /usr/share/consolefonts. It is also possible to add the intended font in the defaultfont file (it is the case in my distribution), don't know about ubuntu. it is /etc/rc.conf in arch for instance. If you have framebuffer support, then you can use the vga entry in grub or lilo to set a higher resolution for your tty and use the default font with ease.
I like Ubuntu - a lot - but the developers seem to delight in breaking useful things or making critical info impossible to find. In my mind there is absolutely no reason to NOT include the kernel configuration file in /proc, nor is there any reason to ship a kernel that by default has screwed up alternative (non-x) consoles. But I'm beginning to foam at the mouth here...

Thanks for your help!

---

### Post by calrogman on 2009-04-19
> **bbt5001 said:**
> Just the ubuntu boot status progress bar page is offset severely.

One of the biggest reasons I just turned off the splash screen on my laptop, it looks awful when the console is set to 1280*800(vga=866).

If you run the following;
```
sudo aptitude install hwinfo
sudo hwinfo --framebuffer | grep Mode
```

You will see a list of resolutions that tty1-6 can use on your system, use the one that matches the screen resolution and has the highest number of bits for the best display.

In my case I get
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits

```

and can use the boot parameters vga=0x0362 or (converting hexadecimal to decimal) vga=866, and to disable the splash screen just remove 'splash' from the boot parameters.

---


---
title: "Inspiron 6400 problems with xserver"
date: 2007-10-17
forum: Dell  Ubuntu Support
---

### Post by brixendk on 2007-10-17
I have just installed ubuntu 7.04 on my inspiron 6400 with a X1300 card. It dident work out with the normal cd so i installed it with the alternate cd. I installed it and the xserver wont start. 
i'm not sure how to get the whole file up, so here's some of it. (i got a usb pen, but how to move the file?)

Backtrace:
0: /usr/X11R6/X(xf86SigHandler+0x81) [0x80a5b91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+09aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d51ebc]
5: /usr/X11R6/bin/x(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
caught signal 11. Server arborting

i'm new to all this linux thing so if you would be clear of what i sould to, it would be great.

---

### Post by neptho on 2007-10-17
Ow. 

Usually a Sig-11 is bad RAM or overheating.

Try this, however, if you haven't installed the (ugh) fglrx drivers:

```
sudo apt-get --reinstall install xserver-xorg-video-ati
sudo aticonfig --initial --input=/etc/X11/xorg.conf
sudo modprobe fglrx
sudo depmod -a
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

Hopefully that fixes it for you; this will at the very least get the proper video driver loaded

---


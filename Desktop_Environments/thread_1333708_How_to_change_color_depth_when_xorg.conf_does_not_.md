---
title: "How to change color depth when xorg.conf does not exist?"
date: 2009-11-21
forum: Desktop Environments
---

### Post by benton on 2009-11-21
Hi there,

Just installed Xubuntu 9.10 on my old laptop. Everything works fine but I want to change color depth to 16 bit. IIRC, that is done on /etc/xorg.conf but this file does not exist on my hard drive. I did:

sudo find / -name xorg.conf

but file was not found.

Any ideas on how to change the color depth when this file does not exist?

Thanks,

-Benton

---

### Post by XubuRoxMySox on 2009-11-21
Forgive me if I have misunderstood what you want, but if you right-click the desktop and choose Desktop Settings you can lighten or darken the brightness and contrast of your Desktop on the same screen that you use to select your wallpaper.

-Robin

---

### Post by yossell on 2009-11-21
I don't know about the sudo find command - but did anything turn up when you looked for the file using a file manager? My own xorg.conf file was in a different folder: /etc/X11  but I'm on an older version of ubuntu and I mainly use gnome, so this may not be relevant for you.

---

### Post by edwardp on 2009-12-06
I've been having Flash audio (radio stations) issues on the desktop (below) with both Windows XP and Linux installed and was able to solve the audio problem in Windows by changing the color from 32-bit to 16-bit.  

I'd like to be able to do the same with Linux, I believe it defaults to 24bpp (24-bit color) and there does not appear to be an easy way to change this.

---

### Post by edwardp on 2009-12-13
With 9.10, create an **xorg.conf** file in /etc/X11/ with only the following in it:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    16
EndSection
```

and restart X (log out) or reboot the system.

This changed the color depth to 16, but the end result is that it did not resolve the Flash-related audio problem I mentioned, so I removed it afterwards.

---

### Post by trackom on 2010-08-12
That issue is not due you have and older version of Xorg but a new one. You can launch:

Xorg -configure

It creates and xorg.conf.new file in your current home folder. Then you can copy this file to /etc/X11/
To read more about this:
[http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)
Regards!

---


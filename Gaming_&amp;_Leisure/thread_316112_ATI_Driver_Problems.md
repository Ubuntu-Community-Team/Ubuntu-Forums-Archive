---
title: "ATI Driver Problems"
date: 2006-12-10
forum: Gaming &amp; Leisure
---

### Post by PPAAUULL on 2006-12-10
Ok so I have tryed in install the fglrx driver for my ATI card cause the opensource driver was giving me some issues. I have been using this HowTo [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and I am using Ubuntu Edgy 6.10. Anyways I get down to the part about testing it to see if it is running and I get this output:```
paulvolk@LinuxPC:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

so I ran the "sudo modprobe fglrx" command and got this: ```
paulvolk@LinuxPC:~$ sudo modprobe fglrx
FATAL: Error running install command for fglrx

```

Could someone please help me? Thanks so much in advance.

---

### Post by Turner.kj on 2006-12-10
I used this site to guide me: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).

Hope this helps.

---

### Post by mpampix on 2006-12-10
Well I don't know in Edgy, but in Dapper I had the same problem on my laptop (Mobility Radeon X600) and I tried the guide you mention but after "sudo aticonfig --overlay-type=Xv" instead of editing manually the xorg.conf I ran "sudo dpkg-reconfigure xserver-xorg" where I chose the fglrx driver and not ati.  It worked perfectly.

---

### Post by PPAAUULL on 2006-12-10
Thanks to the both of you. I got it working what happend was I did the HowTo and then did the "sudo dpkg-reconfigure xserver-xorg" and choose fglrx and it didn't work and I was looking and I did not disable the composite at the end of the xorg config and that fixed it!!!! YAYA thanks soo much I have been loking around for about 3 months how to fix it. I even did a fresh install. Again thanks!!!

---

### Post by squidmaster on 2006-12-15
> **mpampix said:**
> Well I don't know in Edgy, but in Dapper I had the same problem on my laptop (Mobility Radeon X600) and I tried the guide you mention but after "sudo aticonfig --overlay-type=Xv" instead of editing manually the xorg.conf I ran "sudo dpkg-reconfigure xserver-xorg" where I chose the fglrx driver and not ati.  It worked perfectly.

worked like a charm! thanks to that I have been driving myself CRAZY over this because every time I used "gedit" it would ask me for a file option and none of the options worked from "gedit --help"

EDIT:
well
now that i have Ubuntu installed on the HDD it wont work.
just get a "cannot display resolution" on my monitor.
it goes up to 1024x768 but I started it on 800x600 and 1024x768, neither work.

---


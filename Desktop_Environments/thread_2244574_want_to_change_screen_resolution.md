---
title: "want to change screen resolution"
date: 2014-09-17
forum: Desktop Environments
---

### Post by arun-3 on 2014-09-17
I typed following command in terminal 


lspci -nnk | grep -i vga -A3
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
Subsystem: ASUSTeK Computer Inc. Device [1043:82c9]


and this the output i got . Want to change screen resolution 1440*990 .Can you please suggest an solution.


Thanks in advance,

Best Regards,
Arun

---

### Post by TheFu on 2014-09-17
xrandr
lxrandr
arandr

Any of those should do it, provided the GPU supports the resolution AND the monitor supports the resolution.

---

### Post by arun-3 on 2014-09-18
thanks i will  check this command and let you know.....

---

### Post by arun-3 on 2014-09-18
for lxrandr command i got following output

xrandr: Failed to get size of gamma for output default

For arandr command i got following output

/usr/lib/python2.7/dist-packages/screenlayout/xrandr.py:58: UserWarning: XRandR wrote to stderr, but did not report an error (Message was: 'xrandr: Failed to get size of gamma for output default\n')
  warnings.warn("XRandR wrote to stderr, but did not report an error (Message was: %r)"%err)


Both command not worked for me.Please suggest an idea.

Best Regards,
Arun

---

### Post by TheFu on 2014-09-18
Are you running inside a VM?

---

### Post by arun-3 on 2014-09-18
No, i am not using VM

---

### Post by TheFu on 2014-09-18
> **arun-3 said:**
> No, i am not using VM

That's too bad.
[http://askubuntu.com/questions/449820/ubuntu-14-04-screen-resolution-too-low-sis-671-graphics-card](http://askubuntu.com/questions/449820/ubuntu-14-04-screen-resolution-too-low-sis-671-graphics-card) implies that it is time to get a new GPU.

The xorg.conf answer in that link seems like the only option, but VESA is a less-than-ideal solution and you'll constantly need to fight this battle.  I'd get a new $20 GPU and be done with it.

---

### Post by arun-3 on 2014-09-23
[COLOR=#006621][FONT=arial]I just copied download display drivers from this link www.[/FONT][/COLOR][B]sis.com and copied the three display driver files to etc/x11/ and copied file restarted the system. Edit the xorg.confg file change driver: to vesa. Now my display problem solved.

Thanks ,
Best Regards
Arun[/B]

---


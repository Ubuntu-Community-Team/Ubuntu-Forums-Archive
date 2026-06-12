---
title: "Graphics crad &amp; wireless drivers in ubuntu 9.04 &amp; dell inspiron 1525"
date: 2009-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by megazayed on 2009-05-17
hi all,
i have dell inspiron 1525 and i have just installed ubuntu 9.04,
i have sime problems like 
i think that the graphic card driver is not installed & the wireless driver too,
the mozilla firefox browser seems very huge for me becouse i've installed webdeveloper tools and there is not enough place in the webdeveloper toolbar
to show all the webdeveloper tools,
i have problems with flashes in the browser it's qulity is very poor even after installing adobe flash player

thanks all, waiting for reply

---

### Post by coffeeaddict22 on 2009-05-18
Have you gone into System/Hardware Drivers and enabled the restricted drivers?

---

### Post by megazayed on 2009-05-18
yes i did 
and nothing changed

---

### Post by coffeeaddict22 on 2009-05-21
OK.. So what's running?  Open a terminal, type in ```
lshw -C network
``` and look under the display and network subheadings; one of the options is the driver, but there's a bit of other info there too.  Post it back if you need more help.

---

### Post by enlli on 2009-05-21
My 1525 uses the proprietary Broadcom STA wireless driver and works fine. I would check that it is installed in your hardware

---

### Post by megazayed on 2009-05-25
thanks all
my wireless problem had solved,
the problem now with the graphics
i think i have not x setting configration

this is my graphics card
> 
root@ahmed-laptop:/home/ahmed# sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


i want to put setting in xorg.conf file to can understand this driver
can any one help me in this ?

---

### Post by eb sol on 2009-05-26
The same problem here :( ..

---

### Post by UbuJaime on 2009-06-19
The same problem for me, it looks like my Graphic Card doesn't work very well. And my lap get "frezee" sometimes. Any ideas?

---

### Post by cameron365 on 2009-09-22
I have also dell 1525, if you want to install your wireless driver just do:

```
apt-get install b43-fwcutter
```

i am sure it will work for you.

---


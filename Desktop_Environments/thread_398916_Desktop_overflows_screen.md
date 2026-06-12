---
title: "Desktop overflows screen"
date: 2007-04-01
forum: Desktop Environments
---

### Post by SeattleUser on 2007-04-01
I just started using Ubuntu and my desktop overflows the screen.  I can use the monitor controls to move it up or down, but either way I lose something off the top or bottom.  Is there a way to reduce the vertical size of the desktop?

Thanks.

---

### Post by siya_kh1983 on 2007-04-01
can u change the resulotion?

---

### Post by SeattleUser on 2007-04-01
I have the resolution set to the native resolution for my monitor.  The desktop just has a few too many pixels in the vertical direction.  Perhaps this is a problem with the 915resolution package.  I have a widescreen lcd monitor with the builtin Intel graphics.

---

### Post by siya_kh1983 on 2007-04-01
If you wanna quickly learn Ubuntu just read the document that ubuntu present to you in the [www.ubuntu.com](www.ubuntu.com) site.
you better first read "desktop" doc. this doc have two format, it's better give the pdf file. and if you had a problem to open the file on ubuntu you can go "addRemove program" on application ( I mean application --> addREmove (or like some thing like this)) and then on the top of the window on the search textBox write pdf and then select acrobat reader. then ubuntu download it for you and can read any pdf file (( if you had problem to open the file))

I'm new user of ubuntu too. so we can help each other to learn this OS as soon as possible

---

### Post by siya_kh1983 on 2007-04-01
So it's smell that you may need to install monitor or graphic card :(
I don't know maybe there is profesional solve for this problem :(

---

### Post by kellemes on 2007-04-01
Just guessing..
Assuming you're using the correct resolution for this monitor you probably also should enter **DisplaySize** in /etc/X11/xorg.conf

This is the section in my xorg.conf where to put it.. my values are for a 22inch widescreen.
I believe I found them somewhere in /var/log/Xorg.0.log(.old)
But Google might be of help also..

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        DisplaySize     432    324
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0
        Option      "DPMS" "true"
EndSection

---

### Post by RedSquirrel on 2007-04-01
> **SeattleUser said:**
> I have the resolution set to the native resolution for my monitor.  The desktop just has a few too many pixels in the vertical direction.  Perhaps this is a problem with the 915resolution package.  I have a widescreen lcd monitor with the builtin Intel graphics.


Does the monitor *itself* have something to automatically adjust the image on your screen? (I mean in the On-Screen-Display menu).

If that doesn't help, post your /etc/X11/xorg.conf file and the output of:

```
sudo 915resolution -l
```

---


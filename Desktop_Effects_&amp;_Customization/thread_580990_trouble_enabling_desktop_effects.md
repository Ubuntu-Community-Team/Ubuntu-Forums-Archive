---
title: "trouble enabling desktop effects"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Jfire03 on 2007-10-19
I'm installing ubuntu 7.10. This is my first time using and installing Ubuntu. I'm trying to enable desktop effects, i have an Ati Mobility Radeon X1300 and have already installed the driver. First I had an error and fixed it by downloading some packages that needed to be downloaded, xserver something. Now I just have a message saying "desktop effects could not be enabled". I have no idea what's going on.

can anyone help?

---

### Post by opferstad on 2007-10-28
I have exactly the same problem. Why doesn't people have a solution for this? :P

---

### Post by Forlong on 2007-10-28
Do you have the exact same graphics card?

What's the output of ```
compiz
``` in a terminal?

---

### Post by opferstad on 2007-10-29
Yup, got an ATI Mobility Radeon x1300. The output of compiz was:

> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by vmaric on 2007-10-29
Hi evryone 
Can you helpmy_?

Ican not enable panel options like work space switcher and window lists ...
end my button panel is clear wen opened some aplication.
Wen click on them end try to enable it system give message:

The panel encontered a problem while loading 
"OAFIID:GNOME_ShowDesktopApplet

what i can do?

---

### Post by vmaric on 2007-10-29
I have ubuntu 7.04 and gnome desktop

---

### Post by Forlong on 2007-10-29
> **opferstad said:**
> Yup, got an ATI Mobility Radeon x1300. The output of compiz was:```

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```
It seems like you have the restricted driver installed. You have to use Xgl then:
```
sudo apt-get install xserver-xgl
```


@vmaric: please start your own thread for this problem.

---

### Post by JPorter on 2007-10-29
The fglrx driver for ATI cards is currently blacklisted for use with Compiz.


The new 8.42.3 driver should fix this, but it hasn't yet been rolled out to the repositories.  If you want to use fglrx you'll either have to wait, or manually compile 8.42.3 and de-blacklist the driver for Compiz.  There are instructions for doing that somewhere around here.

---

### Post by opferstad on 2007-10-29
> **Forlong said:**
> It seems like you have the restricted driver installed. You have to use Xgl then:
```
sudo apt-get install xserver-xgl
```


@vmaric: please start your own thread for this problem.

That worked. I can activate the desktop effects now.

Thanks!

---


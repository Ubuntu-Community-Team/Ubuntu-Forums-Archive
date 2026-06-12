---
title: "Enable Hardware acceleration"
date: 2010-12-14
forum: Desktop Environments
---

### Post by ryezs on 2010-12-14
Hi
I'm using Ubuntu 10.04 but I have customized the startup so it only start my own application in a xwindow, no gdm. But the problem is that i dont get hardware acceleration for the program when i start it this way, it works in gdm. Is there a way to enable HW acceleration for a xwindow?

---

### Post by Krytarik on 2010-12-15
Did you wrote the video settings to the xorg.conf? What drivers do you use?

---

### Post by ryezs on 2010-12-16
> **Krytarik said:**
> Did you wrote the video settings to the xorg.conf? What drivers do you use?

I use the AMD drivers that ubuntu recomends(ati/amd proprietary fglrx graphics driver), the card is a HD4350. I have tested to generate a new xorg.conf and enabling DRI mode in it. I added the section "DRI" Mode 0666 in it, i found that in another thread. Is this the way to enable it or have i missed something?

---

### Post by Krytarik on 2010-12-16
I assume, even if you don't use gdm, you are using a desktop, right? With Compiz?
If so, try those options, especially the AIGLX-option, purge the DRI-option instead:
[http://wiki.compiz.org/ATI%20with%20AIGLX](http://wiki.compiz.org/ATI%20with%20AIGLX)

Try troubleshooting with this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

What is the output of:
```
fglrxinfo
```

You may also try the proprietary drivers delivered by "Ubuntu X Team":
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by ryezs on 2010-12-17
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series
OpenGL version string: 3.3.10237 Compatibility Profile Context
```

I'm will try AIGLX and the Ubuntu X teams drivers later today.

 I don't know if I use compiz, I have disabled the start of gdm and made a bash profile that starts X, then .xinitrc starts my program. When i run my program that way i get 20 errors like this:
```
fglrx: no matching device section for instance
```
I don't know what that means is it the drivers that don't support fglrx or is it the card that don't support it?

---

### Post by Krytarik on 2010-12-17
"fglrx" is the driver.;)

Try the Ubuntu-X-Team-driver, also look at the options in the xorg.conf and the troubleshooting-hints (at the second link).

You may also try disabling Compiz by setting the Composite-extension in the xorg.conf at "disable".

---


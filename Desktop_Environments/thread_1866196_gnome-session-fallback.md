---
title: "gnome-session-fallback"
date: 2011-10-21
forum: Desktop Environments
---

### Post by Azyx on 2011-10-21
Is it possible to to switch between normal Unity and gnome-session-fallback, if you install it true gnome-session-fallback ?

---

### Post by coffeecat on 2011-10-21
Yes. Choose a different session at the log in screen. The last one you choose becomes the default. I don't believe you can switch directly from Unity to gnome-session-fallback, but you can simply log out and log in to the fullback desktop.

---

### Post by Azyx on 2011-10-21
Do you now how I can get to GDM from a live-USB session? I want to test 11.10 on my desktop before I install it, and it's impossible to see how it worka with Unity. Can't find anything and it takes a lot of time to boot, compared to live-USB 10.04.

---

### Post by coffeecat on 2011-10-21
It's actually LDM with 11.10, but anyway...

I've not tested this with 11.10, but this is what worked with 11.04. Let the live session boot up to the desktop. If your hardware doesn't support compiz, then you will be taken to the Unity 2d desktop in 11.10. Once in the desktop, press Alt+PrintScreen+k. On some machines/keyboards you will have to use the AltGr key instead of Alt. This will kill the xserver and take you to the log in screen. Use "ubuntu" for username and a blank (just press enter) for the password to log into whichever desktop you choose.

If I'm reading you correctly, you are wanting to test gnome-session-fallback in the live USB session. I'm sure you know this, but you will need to create a live USB with persistence and install the package gnome-session-fallback from the Unity 2d desktop.

---

### Post by Azyx on 2011-10-21
> **coffeecat said:**
> It's actually LDM with 11.10, but anyway...
Once in the desktop, press Alt+PrintScreen+k. On some machines/keyboards you will have to use the AltGr key instead of Alt. This will kill the xserver and take you to the log in screen. Use "ubuntu" for username and a blank (just press enter) for the password to log into whichever desktop you choose.


It does not work :(

I have an Asus eeePC 900 and I think it's only Unity 2d.. I have checket that print-sceen work (Fn+Ins) and have tried both Alt and AltGr, but nothing happend when I press Alt+PrintScreen+k.

---

### Post by howefield on 2011-10-21
You could possibly perform a "standard" install on your USB ?

Not sure about the minimum size required, I'm currently setting up an 8 gig stick.

---

### Post by coffeecat on 2011-10-21
> **Azyx said:**
> It does not work :(

I have an Asus eeePC 900 and I think it's only Unity 2d.. I have checket that print-sceen work (Fn+Ins) and have tried both Alt and AltGr, but nothing happend when I press Alt+PrintScreen+k.

Sorry to hear that. Strictly speaking it should be the SysReq key which is often labelled "PrtScr", and on many keyboards one key does both.  The alt+SysReq key combo is one of the magic key combinations and is intercepted by the kernel. If you have an unusual key combination for Print, you may need to add the ctrl key as well. See:

[http://en.wikipedia.org/wiki/Magic_key](http://en.wikipedia.org/wiki/Magic_key)

Otherwise, I agree with howefield that a standard install on USB would be a way of testing the gnome-session-fallback package.

---

### Post by Azyx on 2011-10-22
> **coffeecat said:**
> Sorry to hear that. Strictly speaking it should be the SysReq key which is often labelled "PrtScr", and on many keyboards one key does both.  The alt+SysReq key combo is one of the magic key combinations and is intercepted by the kernel. If you have an unusual key combination for Print, you may need to add the ctrl key as well.[]("http://en.wikipedia.org/wiki/Magic_key")
.

Ok, Imy it was PrtScr, and my SysReq my be called Sys Rq and are Fn Del. Will test now

---

### Post by Azyx on 2011-10-22
I have an 8GB SD card, try to install there. /Cheers

---

### Post by Azyx on 2011-10-22
> **howefield said:**
> You could possibly perform a "standard" install on your USB ?

Not sure about the minimum size required, I'm currently setting up an 8 gig stick.

How do you format the usb? fat, ext3 och ext4 ?

---

### Post by howefield on 2011-10-22
I formatted mine as ext4, but the choice is yours.

---


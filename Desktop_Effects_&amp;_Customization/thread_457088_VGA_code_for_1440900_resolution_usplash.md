---
title: "VGA code for 1440*900 resolution usplash"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by Caste#02 on 2007-05-28
Hi everybody!

I'd like to know if anyone knows the VGA code for **1440*900** resolution...I would like to change the usplash resolution, but I've found codes only for **1280*1024** and other **1.33** screen ratio...
At present the usplash resolution sucks, it gives me back an huge image, besides completely misshapen. It's not a big problem, but I'd like to resolve it anyway. ;) 

Thanks in advance,
Caste.

---

### Post by Caste#02 on 2007-05-29
Help me please! :( *Up!*

---

### Post by Caste#02 on 2007-05-29
I try here too...

First of all: hi everybody!

I'd like to know if anyone knows the VGA code for **1440*900** resolution...I would like to change the usplash resolution, but I've found codes only for **1280*1024** and other **1.33** screen ratio...
At present the usplash resolution sucks, it gives me back an huge image, besides completely misshapen. It's not a big problem, but I'd like to resolve it anyway. ;) 

Thanks in advance,
Caste.

---

### Post by Caste#02 on 2007-05-30
*Up!*

Could anyone help me, please?  :(

---

### Post by Xappe on 2007-05-30
I would try to edit /etc/usplash.conf

---

### Post by Caste#02 on 2007-05-30
> **Xappe said:**
> I would try to edit /etc/usplash.conf

First of all, thanks for your answer. ;)

Passing to the problem: I know which file I have to edit (*/boot/grub/menu.lst*), but to do this I have to know which is the VGA code for my resolution ;)

This is my sickening usplash with default resolution:

[[IMG]http://img255.imageshack.us/img255/5562/p101002721tl4.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=p101002721tl4.jpg)

:(

---

### Post by Premium_User on 2007-05-30
I found this page whilest learning my self how to change the usplash size. 
There are some vga codes with corresponding resolution sizes near the bottom.

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Hope that helps get you started.

---

### Post by Premium_User on 2007-05-30
I found this page whilest learning my self how to change the usplash size. 
There are some vga codes with corresponding resolution sizes near the bottom.

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Hope that helps get you started.

---

### Post by Xappe on 2007-05-30
Well, ok,  I thought that the vga codes given in menu.lst had nothing to do with the usplash resolution nowadays. Since they included the new usplash and startup (dapper to edgy iirc) i've always used /etc/usplash.conf to change the resolution used by usplash.

---

### Post by Premium_User on 2007-05-31
> **Xappe said:**
> Well, ok,  I thought that the vga codes given in menu.lst had nothing to do with the usplash resolution nowadays. Since they included the new usplash and startup (dapper to edgy iirc) i've always used /etc/usplash.conf to change the resolution used by usplash.

I changed it in usplash.conf to my suprise it does nothing when Ubuntu loads.
To my suprise it changed the usplash resolution when shutting down though.


The grub menu list vga=  is the key to getting the resolution to change at boot.

---

### Post by Caste#02 on 2007-06-01
> **Premium_User said:**
> I changed it in usplash.conf to my suprise it does nothing when Ubuntu loads.
To my suprise it changed the usplash resolution when shutting down though.


The grub menu list vga=  is the key to getting the resolution to change at boot.

Yes, it's (*almoust*) the same for me...when I switch on my Ubuntu it doesn't works, but when I shutting down it gives me a a sequence of error (*three purple little distorted Ubuntu logo at the top of the screen, for example, or a giant loading bar...I don't know exactly how to explain*).

Thanks anyway for your help, **Xappe** ;) :(

---

### Post by Xappe on 2007-06-02
Have you tried running

sudo dpkg-reconfigure linux-image-`uname -r`

after the change in usplash.conf?
Maybe that's the key...if not, I can't help ypu any further.

Good luck!

---

### Post by SirYes on 2007-11-24
If you install the **hwinfo** package, it will give you the list of available modes:

```
sudo apt-get install hwinfo
sudo hwinfo --framebuffer
```I was able to use that successfully to enable 1440x900 mode and even configured usplash to look good in that resolution. :-D
See the [thread=622018]thread #622018[/thread] to read my whole post.

BTW. The mode number you're looking for is probably:
> Mode 0x0365: 1440x900 (+5760), 24 bits

---

### Post by SirYes on 2007-11-24
If you install the **hwinfo** package, it will give you the list of available modes:

```
sudo apt-get install hwinfo
sudo hwinfo --framebuffer
```I was able to use that successfully to enable 1440x900 mode and even configured usplash to look good in that resolution. :-D
See the [thread=622018]thread #622018[/thread] to read my whole post.

BTW. The mode number you're looking for is probably:
> Mode 0x0365: 1440x900 (+5760), 24 bits

---


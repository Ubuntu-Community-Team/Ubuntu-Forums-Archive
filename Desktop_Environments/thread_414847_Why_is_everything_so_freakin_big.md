---
title: "Why is everything so freakin big?"
date: 2007-04-20
forum: Desktop Environments
---

### Post by rstuart on 2007-04-20
Hi everyone,

I am new to Ubuntu and haven't really used it at home much. I jsut installed 7.04 and want to know why on earth is everything so big? The windows, the fonts, icons everything, they are huge compared to windows despite being on the same screen resolution!

Is there a way to fix this?

Thanks

---

### Post by Ownerizer on 2007-04-20
What type of graphics card do you have? (e.g., Intel, Nvidia)?

---

### Post by igknighted on 2007-04-20
> **rstuart said:**
> Hi everyone,

I am new to Ubuntu and haven't really used it at home much. I jsut installed 7.04 and want to know why on earth is everything so big? The windows, the fonts, icons everything, they are huge compared to windows despite being on the same screen resolution!

Is there a way to fix this?

Thanks

It's all customizable.  You can change the size of the icons and text and everything else if you want.  Ubuntu does use big icons by default, but if everything else is big you might not be getting the resolution you think you are.

---

### Post by bashologist on 2007-04-20
In this case a screenshot would be worth a million words... Maybe not, but it certainly would help. [http://www.imagevenue.com/](http://www.imagevenue.com/)

---

### Post by rstuart on 2007-04-20
I have a Dell inspiron 640m laptop. It uses the on-board video that comes with the 945GM chipset. Now that i think about, the resolution is wrong. It supports 1440 x 900 but its only at 1280 x 768.

I assume i need a different driver?

---

### Post by zenwalker on 2007-04-20
Before going for a new driver, just try changing the resolution first. Ctrl then Alt then + or - keys.

---

### Post by rstuart on 2007-04-20
Under System -> Preferences -> Screen Resolution 1280 x 768 is the biggest

---

### Post by zenwalker on 2007-04-20
Oh then i guess the driver is capable of supporting that much of resolution then.

---

### Post by rstuart on 2007-04-20
Right, well then, any suggestion where to start looking?

---

### Post by Rackerz on 2007-04-20
Any idea what graphics card is in your Laptop? Nvidia, Intel, ATI?

---

### Post by seamless on 2007-04-20
> **rstuart said:**
> I have a Dell inspiron 640m laptop. It uses the on-board video that comes with the 945GM chipset. Now that i think about, the resolution is wrong. It supports 1440 x 900 but its only at 1280 x 768.
The problem is the video bios is reporting incorrectly. You will need to use the 915resolution tool to set the correct resolution. [Here]("https://help.ubuntu.com/community/i915Driver") is a short guide that should help you.

---

### Post by pepsi_max2k on 2007-04-20
> **rstuart said:**
> Hi everyone,

I am new to Ubuntu and haven't really used it at home much. I jsut installed 7.04 and want to know why on earth is everything so big?

Mainly due to the dpi setting and the default font and icon sizes. Follow the following guide to get stuff more windows like:
[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

Fonts and icon sizes can be changed in system > preferences > fonts / file management.

And this should help out if you have problems setting dpi on an nvidia card:
[http://my.opera.com/CrazyTerabyte/blog/2006/02/20/nvidia-vs-fonts](http://my.opera.com/CrazyTerabyte/blog/2006/02/20/nvidia-vs-fonts)

---


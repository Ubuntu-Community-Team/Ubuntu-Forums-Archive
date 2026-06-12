---
title: "Change Ubuntu login window background from image to hex color"
date: 2011-01-10
forum: Desktop Environments
---

### Post by ryankask on 2011-01-10
Hi. I have Ubuntu Tweak installed but it only lets me change the login background to an image. Is it possible to use a color in hex?

I am using Ubuntu 10.10.

Thanks,
Ryan

---

### Post by hhh on 2011-01-10
This article shows how you can enable Appearance Preferences for the login window (you can skip step 1, he's wrong about you needing to move your image to the /usr/share/backgrounds folder, and the image does not have to be a jpg)...
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

As you can see from the screenshot in that article, just choose the Solid Color background (top-left corner in that shot) and set your color(s) under Colors:

An alternative way to achieve the same affect would be to create a solid colored image with Gimp and use Ubuntu Tweak to set it.

---

### Post by ryankask on 2011-01-11
Thanks for your help.

I'm really looking for a conguration file where I can set the desired color's hex value.

Thanks,
Ryan

---

### Post by ryankask on 2011-01-11
Thanks for your help.

I'm really looking for a conguration file where I can set the desired color's hex value.

Thanks,
Ryan

---

### Post by hhh on 2011-01-11
Whatever, I don't see the difference. This is a GUI which writes the hex code somewhere. If you want to find where, try /usr/share/gdm or /etc/gdm.

---

### Post by ryankask on 2011-01-12
The difference is that the GUI doesn't work for setting colors; only the backgrounds work from that dialog.

---

### Post by stinkeye on 2011-01-12
> **ryankask said:**
> The difference is that the GUI doesn't work for setting colors; only the backgrounds work from that dialog.
...and hex colors.
Choose **no desktop backgound** and then choose your color.

---

### Post by hhh on 2011-01-12
Ja, da top left vun!

> **hhh said:**
> As you can see from the screenshot in that article, just choose the Solid Color background (top-left corner in that shot) and set your color(s) under Colors:

---

### Post by ryankask on 2011-01-13
That's brilliant! Sorry for the tone of my last post. Thanks **hhh** and **stinkeye**.

---

### Post by haikalpribadi on 2011-05-12
we don't have Ubuntu Tweak in natty, anymore. is there other application or way to change the login screen background image?

---

### Post by runesvend on 2011-06-10
You can install ubuntu-tweak from the [tualatrix ppa]("https://launchpad.net/~tualatrix/+archive/ppa"). Here's a guide if needed:

[http://www.liberiangeek.net/2011/03/install-ubuntu-tweak-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/install-ubuntu-tweak-ubuntu-11-04-natty-narwhal/)

---


---
title: "Flash Click Problem using Opera on Lubuntu (LXDE)"
date: 2012-06-15
forum: Desktop Environments
---

### Post by TenPlus1 on 2012-06-15
This is a strange problem to say the least, but...  After installing Opera 12 on my Lubuntu setup I noticed that certain flash programs wont let me click buttons, like this:

[http://www.speedtest.bbmax.co.uk/](http://www.speedtest.bbmax.co.uk/)  <-- Try clicking Begin Test

but...  on other desktop managers like Xubuntu's XFCE or Ubuntu's Unity (or Gnome) it works perfectly fine...  So does anyone have any ideas why this only happens on LXDE ?

---

### Post by Rex Bouwense on 2012-06-15
Couple of questions:  Do other browsers react the same?  Are you having other problems with Opera?  Since Opera is not in the repositories, there may be some glitch.  Have you checked Launchpad for bug reports?

---

### Post by TenPlus1 on 2012-06-15
I've tested many browsers including Chromium, Firefox, Midori and even Opera 11.64 and they all work fine, it's just Opera 12 (and the beta/rc's) that had this problem...  I have also mentioned it as a bug to Opera themselves...

---

### Post by amjjawad on 2012-06-17
> **TenPlus1 said:**
> I've tested many browsers including Chromium, Firefox, Midori and even Opera 11.64 and they all work fine, it's just Opera 12 (and the beta/rc's) that had this problem...  I have also mentioned it as a bug to Opera themselves...


Hi,

Then it must be something to do with Opera itself. I never use it, sorry, I always use Firefox and Chromium.

I assume you have already installed: lubuntu-restricted-extras

```
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by TenPlus1 on 2012-06-23
Yes I have the restricted extras installed for flash and java etc.  It does indeed seem to be a problem with Opera 12 itself although I would love to find out WHY this only happens with LXDE and not any other desktop manager...

---

### Post by menth1979 on 2012-12-06
Same problem here. If you keep clicking, after a while the button will get the click. This is a problem with just only a few Flash (YouTube works fine).

Usually, if I had to click a button that isn't working, I use the keyboard. Click inside the Flash app, navigate the buttons with tab and click them with space.

---

### Post by menth1979 on 2012-12-09
I found a partial solution: keeping pressed shift while clicking.

[http://icculus.org/pipermail/openbox/2010-July/006701.html]("http://icculus.org/pipermail/openbox/2010-July/006701.html")

---


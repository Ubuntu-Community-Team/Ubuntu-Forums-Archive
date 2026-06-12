---
title: "Kde 4.6"
date: 2011-02-25
forum: Desktop Environments
---

### Post by mark9950 on 2011-02-25
Is nothing but garbage on my dell inspiron 1501 laptop,It has to do with the drivers of the nouveau or the vesa driver.I am going to have to reinstall kubuntu and update kde to 4.5.5 if possible.

---

### Post by inobe on 2011-02-26
seems wonderful here with my nvidia 6 series card, it runs like a champ.

i enabled my additional drivers and everything looks so beautiful.


i have a friend that always listens to my advice, i told him never to buy a laptop unless it has nvidia graphics........

he's bought five, he thanks me all the time :)

---

### Post by jcolyn on 2011-02-26
> **mark9950 said:**
> Is nothing but garbage on my dell inspiron 1501 laptop,It has to do with the drivers of the nouveau or the vesa driver.I am going to have to reinstall kubuntu and update kde to 4.5.5 if possible.

Update your video driver by enabling this ppa ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
``` then ```
sudo apt-get update
``` click update manager and enstall the updates then open synaptic and type ati  (dell inspiron 1501 uses ati) locate xserver-xorg-video-ati and check it for upgrade then click apply. Reboot and you should have faster graphics..

---

### Post by khelben1979 on 2011-02-26
> **jcolyn said:**
> (dell inspiron 1501 uses ati)

Indeed!

According to [this source]("http://www.notebookreview.com/default.asp?newsID=3359&review=Dell+Inspiron+1501") it's using ATI Xpress 1150 256MB HyperMemory (Integrated graphics).

---


---
title: "Problems after Narwhal upgrade"
date: 2011-05-14
forum: Desktop Environments
---

### Post by todes69 on 2011-05-14
I have two problems after (auto)updating to Narwhal this evening:
1) Grub boot no longer shows my windows (vista)
2) new ubuntu desktop no longer responds to mouse - although I can keyboard to a terminal (ctrl-alt-F1)

I have a Dell (AMD 64) with (what may be a bad driver) nvidea graphics card
I want to get back to Windows (WOW junkie) and I would like Narwhal to work as well

any help?

---

### Post by todes69 on 2011-05-14
got vista back by <shift> booting to grub and rebuilding Grub loader

Nnarwhal still doesn't work - tried shell loading/activating of nvidea driver by: 

sudo jockey-text -l
xorg:nvidea_173 (prop, disabled, not used
xorg:nvidea_current (prop, enabled, notused)

sudo jockey-text -e xorg:nvideaXXX (here is a problem)Where XXX is "_current" "-current" "_173" "-173" 
none work

looks like a bad nvidea driver

How do I load (explicit directions, please) a driver that will get narwhal working?  I can get a shell from Narwhal by ctrl-alt-F1

Thanks
todes69

---

### Post by todes69 on 2011-05-14
I tried updating the drivers as per
[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)
no improvement - jockey-text -l
xorg:nvidea_173 (prop, disabled, not used)
xorg:nvidea_current (prop, enabled, not used)

---

### Post by todes69 on 2011-05-15
Still haven't gotten the Unity Desktop to work.
ctrl-alt-F1 to a shell to try to gedit /etc/environment and get this:
Gtk-WARNING **: cannot open display

anyone?
Bueler?  Bueler?

---

### Post by todes69 on 2011-05-15
sudo nano -w /etc/environment
allowed me to add "UNITY_FORCE_START=1"
no improvement - still no response from Unity

How do I install the nvidea 173 drivers (which seem to work)from a terminal (since that's all that works for me)?

---

### Post by Krytarik on 2011-05-17
> **todes69 said:**
> 
How do I install the nvidea 173 drivers (which seem to work)from a terminal (since that's all that works for me)?
If you haven't fixed that already, try this:
```
sudo jockey-text -e xorg:nvidia_173
```
Greetings.

---


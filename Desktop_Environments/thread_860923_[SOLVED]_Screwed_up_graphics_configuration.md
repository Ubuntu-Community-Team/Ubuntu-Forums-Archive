---
title: "[SOLVED] Screwed up graphics configuration"
date: 2008-07-16
forum: Desktop Environments
---

### Post by swoopdk on 2008-07-16
Hi

I really need your help to fix my moms pc.

She have just got a new pc where I installed Ubuntu 8.04. The only thing she complains about is low frame rate. So yesterday I tried to do something about it but I didn't turn out very well.

The issues are now this:

1) The normal Ubuntu / Gnome login screen is now only about 1/4 in size and you can't see the login boxes for user name and password.

2) The resolution in Gnome is a bit better and is almost what it was before I started to fumble around.

3) The frame rate is in fact even lower now than it was before. As far as I remember the current rate is 51 Hz.

Graphics card is an Asus GeForce 8600GT, Monitor is Samsung 20" 2032BW.
One of the things I tried was switching from nvidia-glx-new to xorg-driver-fglrx (naturally I have switched back).
The option "Device driver NVIDIA accelerated graphics driver (latest cards)" is activated.

Thanks a lot for any help to improve the current situation.

- Allan

---

### Post by kaola_linux on 2008-07-16
Try to compile an Nvidia driver that matches your card, it can be downloaded from their site MAKE SURE TO SELECT THE APPROPRIATE VERSION...

They have a guide about the installation so it will be fine... ^^

---

### Post by crtlbreak on 2008-07-16
> **swoopdk said:**
> ....
Graphics card is an Asus GeForce 8600GT, Monitor is Samsung 20" 2032BW.
One of the things I tried was switching from nvidia-glx-new to xorg-driver-fglrx (naturally I have switched back). 

> **kaola_linux said:**
> ...  Nvidia driver that matches your card .... 

I dont think the nvidia driver should be used for asus GeForce?
I am not sure what the default driver in ubuntu will be for GeForce - but I recommend a more compatible driver - cant use a bmw cylinder head on a toyota engine just because they are both 3 litre engines?  :grin: :grin:

try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then you need to log out user and log in to restart the xserver (you can also crtl+alt+backspace)
This will reconfigure your xserver graphics side of things.

If hers is an old monitor I dont recommend messing with horizontal and vertical sync - this can (only in certain extreme cases) cause damage to the crt  - most monitors nowadays have protection built in though.
hope this helps
regards

---

### Post by kaola_linux on 2008-07-16
> **crtlbreak said:**
> I dont think the nvidia driver should be used for asus GeForce?
I am not sure what the default driver in ubuntu will be for GeForce - but I recommend a more compatible driver - cant use a bmw cylinder head on a toyota engine just because they are both 3 litre engines?  :grin: :grin:

try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then you need to log out user and log in to restart the xserver (you can also crtl+alt+backspace)
This will reconfigure your xserver graphics side of things.

If hers is an old monitor I dont recommend messing with horizontal and vertical sync - this can (only in certain extreme cases) cause damage to the crt  - most monitors nowadays have protection built in though.
hope this helps
regards


Geforce is a product of Nvidia...Instead of him using the older version from synaptic, he could compile and use the latest driver..

---

### Post by kaola_linux on 2008-07-16
@I dont think the nvidia driver should be used for asus GeForce?
I am not sure what the default driver in ubuntu will be for GeForce - but I recommend a more compatible driver - cant use a bmw cylinder head on a toyota engine just because they are both 3 litre engines?


[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[http://www.asus.com/products.aspx?l1=2&l2=6&l3=514&l4=0&model=1700&modelmenu=1](http://www.asus.com/products.aspx?l1=2&l2=6&l3=514&l4=0&model=1700&modelmenu=1)

Asus is the manufacturer of the card and their using the Geforce 8 series chip of nvidia... So if you think the nvidia driver cannot be used on Geforce, will I use the ATI drivers instead?

---

### Post by swoopdk on 2008-07-16
Thanks a lot guys for your input.

I'll download latest NVIDIA driver [http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)

This should improve the resolution and frame rate. But how can I set the resolution used at the login screen?

---

### Post by crtlbreak on 2008-07-16
for me I would always first make a backup copy before I begin messing with anything 

```
sudo cp -a /etc/X11/xorg.conf /etc/X11/xorg.conf.16jul08 
OR
sudo cp -a /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
OR
sudo cp -a /etc/X11/xorg.conf /etc/X11/xorg.conf.working

```
OR whatever filenaming convention you want to apply - it is always good to keep consistency and clarity in naming files


then you will need to run that

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or

manually edit the xorg.conf file with either vi, gedit or nano
such as

```
sudo gedit /etc/X11/xorg.conf 
```

That will automatically generate a new xorg.conf file for you
regards

---

### Post by aeshanw on 2008-07-16
I just installed a Leadtek NVIDIA 8600GT onto my HArdy Heron PC and i get a weird multi-colour mesh on the screen on-bootup and the system hangs.ANy clue on how I could solve this?thanks!

---

### Post by stitchmysmile93 on 2008-07-17
Have you tried using Envy to install the correct drivers ?

---

### Post by aeshanw on 2008-07-17
Oh I guess I'll have to enter in safe-mode then install Envy?Thanks!

---

### Post by swoopdk on 2008-07-17
You guys are the best.

Now the login screen is back to normal and I can again choose a wide selection of resolutions in Gnome.
What I did was to install the Envy application. Use Envy to install driver followed by activating NVIDIA accelerated graphics driver.

One thing still troubles me ... somehow I can't push the refresh rate higher than:

56 Hz at 1280 x 960
55 Hz at 1280 x 1024
53 Hz at 1400 x 1050
52 Hz at 1440 x 900
50 Hz at 1680 x 1050

It's a fairly new monitor (Samsung 20") with a GeForce 8600GT ... should I believe it should be possible to get a higher refresh rate?
According to this [http://www.pricerunner.co.uk/pi/25-972504/Monitors/Samsung-SyncMaster-2032BW-Black-Product-Info]("http://www.pricerunner.co.uk/pi/25-972504/Monitors/Samsung-SyncMaster-2032BW-Black-Product-Info") it should be possible to run with 75 Hz at 1680 x1050.

I have attached the xorg.conf (rename to xorg.txt in order to could upload it) file to this post - is there something I can improve here?

---

### Post by crtlbreak on 2008-07-17
after you installed the drivers through envy have you tried to reconfigure xorg yet? or is that xorg.conf file you attached the reconfigured version?

```

sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by swoopdk on 2008-07-17
> **crtlbreak said:**
> after you installed the drivers through envy have you tried to reconfigure xorg yet? or is that xorg.conf file you attached the reconfigured version?

```

sudo dpkg-reconfigure -phigh xserver-xorg 
```

When I try to run the command I get:

jette@jette-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for jette: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080717101941

The attached file is the current in use - and because of above error I haven't done reconfigure of xorg.

---

### Post by cocopuffz on 2008-07-17
It may be that the xorg file doesn't know what your monitor is capable of. You fixed the video card issue, now you may have to tell ubuntu what your monitor can handle.

try "gksudo displayconfig-gtk" and try an auto detect. If your monitor is in the list, congrats. If it's not, try the plug & play one that has your desired resolution listed beside it. 

It might look like this "plug & play monitor (1680 x 1050)" 

I would try this outside of X and then do a reset instead of just restarting X. 

Good luck.

---

### Post by swoopdk on 2008-07-17
Thanks a lot cocopuffz and other contributors for your help during this thread.

The resolution and refresh rate are now perfect :-)

---

### Post by crtlbreak on 2008-07-17
and then if you are happy a good practice is to close the thread  - that way people viewing it will know a solution has been found.
regards

---

### Post by stitchmysmile93 on 2008-07-17
I believe envy can be ran in bash...

---

### Post by stitchmysmile93 on 2008-07-17
Sorry guys I don't know how this got sent here LOL....

---

### Post by swoopdk on 2008-07-17
> **crtlbreak said:**
> and then if you are happy a good practice is to close the thread  - that way people viewing it will know a solution has been found.
regards
Didn't know about closing threads - but it's now done :-)
Many thanks.

---


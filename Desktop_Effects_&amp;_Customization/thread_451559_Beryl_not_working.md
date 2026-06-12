---
title: "Beryl not working"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by Kuoi on 2007-05-22
I've tried Beryl in Ubuntu 6.10 before ,  and I could install it , but it didn't work.

I've thought after an update to Feisty Fawn , that I could try it again , maybe it works now ?
It isn't working !

Everytime I start it , and choose Beryl as window manager , the screens are moving a bit , and then it goes back to Gnome Window manager ( metacity ) .

I have a Geforce4 MX 440 videocard 128 MB , but it has to be something with the driver , or am I wrong.

I still don't know what programm Beryl is , after 6 months of using Ubuntu , isn't it a shame ?
According to what I read here , it is !

Kuoi

---

### Post by audax321 on 2007-05-22
First, a few questions:

1. What How-To are you using to install Beryl?
2. What driver do you use for your video card, is it nvidia-glx or nvidia-glx-new?

If you are using the nvidia-glx driver (ver. 9631), give the nvidia-glx-new driver (ver. 9755) a try. They were both in Synaptic for me, and for my card nVidia GeForce 6600GT, I found the 9755 driver to be smoother. Your card has only been supported under Beryl since 8178, so I'd think the newer the driver the better. Also try running Beryl from Terminal (not sure what the command is, try beryl-manager) and see if it outputs any errors before it crashes when you start up Beryl.

---

### Post by Kuoi on 2007-05-23
As soon as I install any driver , I can't boot anymore.

this is my 3th time in 2 days I had to reconfigure xserver-xorg to driver NV !

As soon as I select Nvidia , Ubuntu isn't booting anymore .

Everything is working , but I have some kind of feeling that the videocard isn't what it should be.
Beryl isn't working for some reason , isn't.

BTW : the error when i start in terminal "beryl-manager" is "extension glx is not found on device " or something like that.

Kuoi

---

### Post by audax321 on 2007-05-23
In your xorg.conf, does this section look like this:

```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

```

Just a thought, but that error might be caused by the Load "glx" line being missing.

---

### Post by Kuoi on 2007-05-23
Yes , it is just the same.

Kuoi

---

### Post by Kuoi on 2007-05-23
I've just installed the correct driver ( i think ) using Envy.

Now I don't get an error when I start beryl-manager in terminal , but...

It seems Beryl still doesn't work .
When I change display manager to Beryl , the screens flickering a bit , and it goes back to metacity.

Kuoi

---

### Post by Skavenger on 2007-05-23
> **Kuoi said:**
> I've just installed the correct driver ( i think ) using Envy.

Now I don't get an error when I start beryl-manager in terminal , but...

It seems Beryl still doesn't work .
When I change display manager to Beryl , the screens flickering a bit , and it goes back to metacity.

Kuoi

I have the same problem =(

---

### Post by Kuoi on 2007-05-24
I have Beryl working now !

As far as I remember It worked after I did the following;

type in terminal  "sudo gedit /etc/X11/xorg.conf" , and at the end of the page you must read > Section "Extensions"
    Option         "Composite" "Enable"
EndSection

This setting must set to "Enabled" .

As far as I know , this did it for me.

Hope it helps , Kuoi

---


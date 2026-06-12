---
title: "Slow display, no effects, opoengl apps won't start"
date: 2008-02-02
forum: Desktop Environments
---

### Post by JediKnight on 2008-02-02
I have a Gutsy and Radeon 9600

When I installed Gutsy everything was smooth and nice, and I could use Gnome's standard effects (that means, without compiz and all that)

Recently I tried to install a fglrx driver but didn't manage to

I tried to uninstall everything and revert back to normal and the original open source driver.

The problem I have now is

1. Moving, resizing and scrolling windows is very slow
2. I can't enable the standard effects ('Desktop effects could not be enabled')
3. I can't start 3d applications like Google Earth or Stellarium. Sometimes they even crush the system

So I guess I didn't manage to re-enable the original open source driver. What could have been missing? I am a newbie, I am not sure what I did each time I followed instructions, I can't remember what changes exactly happened so please, don't ask me if I had done this or that. I simply don't remember :)

---

### Post by OlympicSoftworks on 2008-02-03
It's ok, this is an easy fix normally.  Just not an intuitive one.  I don't know of a way to really make this work in the desktop environment so you will have to get into a terminal window.  Type the following, or just copy paste into the terminal window.


sudo dpkg-reconfigure -phigh xserver-xorg


You will be asked to authenticate yourself with your password.  What this will do is run the Debian package manager on the xserver package so it takes another look at your video card and the EDID information from your monitor so everything should be set up like it was when you first installed.  You may be asked to select a couple resolutions you want to have set up by default, kist pick the ones you know your monitor will run with and your golden.

Going forward, for older ATI video cards stick with the open source drivers.  The older ATI proprietary ones are notoriously fickle and do not support any of the AIGLX desktop effects.  This is especially true now that ATI is releasing all the data on the older video chips to the open source community, the module makers are going to have all they need to make some top-notch code for us to use with these cards.  So, for older ATI cards and even older Nvidia cards, stick with the open source modules.

---

### Post by JediKnight on 2008-02-04
Thanks for being the only one to reply so far :)

I am sorry but the problem doesn't seem to be the xorg.conf file. I tried to reconfigure it, I tried what you said, I even deleted it and nothing changed.

---

### Post by JediKnight on 2008-02-05
I think I found the reason.

When I type lsmod |grep ati I don't get anything

While when I type lsmod |grep radeon I get 

radeon                125472  3 
drm                    83348  4 radeon

I think there should be some module relating to ATI. Or not??

---

### Post by JediKnight on 2008-02-06
The problem was the package xserver-xgl

I uninstalled it and speed returned to its normal state

Still didn't manage to restore the default effects and run 3d apps adequately but we will see

---


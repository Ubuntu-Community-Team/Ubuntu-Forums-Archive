---
title: "compiz fusion problems!"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by J'adore le paissons on 2007-11-02
well i tried to install compiz fusion on my dell latitude cpx laptop and to no avail!  :(
i have a ATI technologies Inc Rage Mobility P/M AGP 2x graphics card (which i think mte b my problem).
oh and its on ubuntu 7.10.
i tried to follow [THIS](http://ubuntuforums.org/showthread.php?t=569654) guide but instead of getting :
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

i get Mesa GLX Indirect and none of the trouble shooting stuff helps.
when i go 2 "system->administration->Restricted drivers manager it tells me that "your hardware does not need any restricted drivers" :confused:
and wen i go system->prefernces->appearance it wont let me change my visual effects... it has to stay on none!

can anybody help me 2 get compiz fusion to work or is my laptop just not up to it??

tanx :)

---

### Post by jonray74 on 2007-11-02
This link provides the Hardware requirements for the new ATI driver:

[http://www2.ati.com/drivers/linux/linux_8.42.3.html](http://www2.ati.com/drivers/linux/linux_8.42.3.html)

---

### Post by J'adore le paissons on 2007-11-03
so it wnt wrk then??
am i right?

---

### Post by JoshuaRL on 2007-12-28
Yeah looks like it.  And no support from the ATI site either.  I have a CPx and it seems like it only runs the DRI stuff.  Unless you have a pretty new laptop I think that fglrx is just aggrivating.  Your xorg.conf should have the "ati" driver.  I haven't gotten glxinfo to run with DR returning a yes, but I'll let you know if I do.  I think it'll take a fair amount of tweaking but I'll try to do all the scary part and keep you updated.

Just first of all, try typing this into a terminal:

```

sudo dpkg-reconfigure xserver-xorg

```

It should have a GUI giving you all kinds of options to set up Xorg.  Try to autodetect as much as possible and see if anything changes on your xorg.conf file afterwards.  Try using stuff like 1024x768 resolution and 16bit default color depth.  It should make it run faster and easier.  And before and after you can try running glxgears to get an idea how well everything is running.

If you have any questions on how to do anything I'm talking about post them, maybe they'll help someone else too.

---


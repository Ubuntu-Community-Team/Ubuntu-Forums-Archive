---
title: "How do I make Ubuntu look really good?"
date: 2008-08-28
forum: Desktop Environments
---

### Post by Timberwolf5578 on 2008-08-28
I just installed Ubuntu yesterday for the first time.  I have very limited Linux knowledge.  About all I know how to do right now is use firefox to surf the web.  But I am good at computers overall.  Can someone please explain to me "step-by-step" how I can make Ubuntu look really good?  I tried going to Appearance-Visual Effects-Extra but the nvidia drivers that Ubuntu installed didn't work well, so I removed them and went back to the original settings.  My video card is a 512MB Geforce 8800GT.  And my processor is a AMD Athlon 64 Dual Core 6400+ Black Edition with 2gb PC6400 DDR2/800 memory.

Any responses will be appreciated.

Thanks.

---

### Post by tuxxy on 2008-08-28
Enable your video driver, then navigate to system > prefs > appearance > visual effects , select the extra option.

Now install emerald theme manager from the repos and install some new window themes from here [http://gnome-look.org](http://gnome-look.org), they are under compiz themes.
```

sudo apt-get install emerald
```

Also install compiz effects manager from the repos and enable all the effects you want from this

```
sudo apt-get install ccsm
```

---

### Post by Timberwolf5578 on 2008-08-28
I am going to try to get my video card driver from the Nvidia website.  But how do I install the driver in Ubuntu?  I have no experience in that?  Is it a package that I will download, and do I just have to double-click it?

---

### Post by tuxxy on 2008-08-28
You dont need to download the driver, it is provided for you, just enable the driver here

system > admin > hardware drivers

---

### Post by Timberwolf5578 on 2008-08-28
But as I said in the original post, when I tried to turn on visual effect-extra it downloaded a nvidia glx package that didn't work properly.  So what do I do?

---

### Post by Ms_Angel_D on 2008-08-28
Try [EnvyNG]("http://albertomilone.com/nvidia_scripts1.html") I hear a lot of people are able to got their cards working well with it.

---

### Post by tuxxy on 2008-08-28
Yes try envy then, dont worry that card will work and your best reading up some more about Ubuntu here, [https://help.ubuntu.com/](https://help.ubuntu.com/)

The customising your desktop section should be useful :)

---

### Post by Crafty Kisses on 2008-08-28
Emerald, Compiz, AWM.

---

### Post by Bakon Jarser on 2008-08-28
To get access to a lot more settings you will need the advanced settings.

```
sudo apt-get install compizconfig-settings-manager
```

It will install somewhere in System > Preferences.  Here is a link to their wiki.
[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

If you're looking for new desktop themes try this link.

[http://www.gnome-look.org/](http://www.gnome-look.org/)

If you're looking for a dark theme I recommend overglossed.

[http://www.gnome-look.org/content/show.php/Overglossed?content=74813](http://www.gnome-look.org/content/show.php/Overglossed?content=74813)

---

### Post by MrMarc on 2008-08-29
> **tuxxy said:**
> Enable your video driver, then navigate to system > prefs > appearance > visual effects , select the extra option.

Now install emerald theme manager from the repos and install some new window themes from here [http://gnome-look.org](http://gnome-look.org), they are under compiz themes.
```

sudo apt-get install emerald
```

Also install compiz effects manager from the repos and enable all the effects you want from this

```
sudo apt-get install ccsm
```

I'd hate to hijack the thread but is Emerald essential? Through my time of using Ubuntu I've always just used CCSM on it's own.

I guess I've had no problems doing so but what advantages would there be to using emerald, and exactly what is it?

---

### Post by TenPlus1 on 2008-08-29
Once your gfx card is up and running, check out [www.gnome-look.org](www.gnome-look.org) and look through the themes, icons, pointers, wallpapers, sounds etc to personalize your ubuntu...

---

### Post by linuxlizard on 2008-08-29
Emerald manages the window borders if you install it. I used to use it because it would do transparent borders and stuff, but eventually decided I just liked using gtk themed borders better- there are more to choose from and transparent borders look cool at first but sort of silly when windows are maximized. Just my opinion.

To the original poster- the first step is system-administration-hardware drivers to set up your nvidia card. Or just go into synaptic and pick the one right for your card. 

Second step, go into synaptic and install advanced desktop settings.

Then go system-preferences-advanced desktop settings, and system-preferences-appearance to set everything up how you like.

---

### Post by JECHO on 2008-08-29
you should get emerald, compiz, awn, and conky


then youd be set :guitar:

---

### Post by Richard9795 on 2008-08-29
I Posted some screenshots on what they are talking about making ubuntu look really good. (Besides the nvidia driver) Did i mention you can make windows wobble with compiz when you move them?

---


---
title: "How do I install nvidia driver?"
date: 2008-10-05
forum: Gaming &amp; Leisure
---

### Post by daysgrace on 2008-10-05
I´m new to ubuntu. All I know that I have Ubuntu 8.04.1 with Nvidia geforce7.
I tried to instal many drivers.. but now as I try nothing changes... 
could someone help?

---

### Post by Gutt on 2008-10-05
What doesn't change ?

---

### Post by vishzilla on 2008-10-05
did you install envyng-gtk?

---

### Post by eragon100 on 2008-10-05
> **daysgrace said:**
> I´m new to ubuntu. All I know that I have Ubuntu 8.04.1 with Nvidia geforce7.
I tried to instal many drivers.. but now as I try nothing changes... 
could someone help?

System -> Administration -> Hardware Drivers.

Mark the box saying  "Nvidia Accelerated Graphics Driver" and confirm you want to download and install the driver. Then reboot the computer and see if you have desktop effects (try alt+tab). If you don't have desktop effects, go to system -> preferences -> Appearance and try to enable them in the "Visual Effects" tab. (set them to extra). If they work, your video drivers are correctly installed, else, post back here.

Some nice free games you can play under ubuntu:

- savage 1, get it from [www.newerth.com](www.newerth.com)

- tremulous, from add/remove

- battle for wesnoth, from add/remove

- nexuiz, get the latest version from [www.getdeb.net](www.getdeb.net) (you download a .deb package, you can install it by double-clicking and clicking the Install button in the screen that appears)

- openarena ( [www.getdeb.net](www.getdeb.net) )

- warsow ( [www.getdeb.net](www.getdeb.net) )

- urban terror ( [www.getdeb.net](www.getdeb.net) )

- alien arena ([www.getdeb.net](www.getdeb.net))

- sauerbraten ([www.getdeb.net](www.getdeb.net))

- there are more, this are some of the best free linux games. They should work after you get the driver installed. Enjoy! :wink:

---

### Post by paris_alex on 2008-10-05
i'm a newbie with nvidia as well... but things went very smooth.... i just right click on the desktop to open the "appearence preferences", click on 'visual effects' tab and select 'Extra'. 

Ubuntu 8.04 then automatically prompts me to install the restricted nvidia drivers. It even downloads and install for me automagically! after that... you can do all the cool compiz graphics stuff...

---

### Post by mister_k81 on 2008-10-05
> **vishzilla said:**
> did you install envyng-gtk?

That's what I still use, you can download it from here: 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Though, I'm pretty sure that EnvyNG is also available in the Synaptic Package Manager as well.  


Also, if you want to add some additional settings for your Nvidia driver, you can download the "nvidia-settings" utility from the synaptic. Or you can just open up the terminal and type:  

```
sudo aptitude install nvidia-settings
```

If you used EnvyNG, it will install the nvidia-setting for you automatically. But installing the drivers from Ubuntu's Hardware Driver manager will not install the extra options, as far as I know.

---


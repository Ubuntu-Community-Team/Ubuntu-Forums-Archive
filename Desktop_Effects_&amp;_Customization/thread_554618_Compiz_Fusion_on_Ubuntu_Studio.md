---
title: "Compiz Fusion on Ubuntu Studio"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by dutch_boi1 on 2007-09-19
Hey i have just installed Ubuntu Studio and am loving it.
Now all i wish to do is install Compiz Fusion. I have the nVidia drivers so i have accelerated/optimized drivers.

I Followed the guide @ [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

and also used that script someone in these forums made. I cant remmber the exact name but that did download and set everything up right but in the right directory. It only installed it to home/.cfi_i_u so yes.

Anywayz, i have Compiz Fusion installed but i cant load the configurator so i cant adjust anything :(. Ive tried reinstalling about 3-4 times, compiz fusion that is but to no luck.

So just a question, is there anything specific i need to do for this release tro get it working?

---

### Post by Linder on 2007-09-19
Looks like you are fried, like so many other of us; until Compiz is updated.

[Check this post]("http://ubuntuforums.org/showthread.php?t=534341")

---

### Post by Jadephyre on 2007-09-19
is it not working on Ubuntu Studio ?

i guess then i'll wait with updating to Studio...

---

### Post by Rupertronco on 2007-09-19
It will work with Ubuntu Studio. The only difference between regular ubuntu and studio is some themeing and what software comes preinstalled. 

What repositories are you using for compiz? Trevino's are broken right now. Also make sure you have the settings-manager package. Run "ccsm" in a terminal and post the output.

---

### Post by noodleboy on 2007-09-19
I have Compiz Fusion runnning on my Ubuntu Studio partition and everything seems to be working well. I followed Forlong's guide (plus, check his troubleshooting section for the window borders fix on an Nvidia card). His guide uses the Amaranth sources.
Good luck!

Noodleboy :)

---

### Post by Forlong on 2007-09-19
Hi,

in fact I wrote and tested my guide on an install of Ubuntu Studio (I even pointed that out  in the disclaimer of the main guide). So there's nothing wrong with using Compiz Fusion on Ubuntu Studio.

The main problem for you, dutch_boi1, is obviously that you mixed installs. So I guess this is the result of that.

Please post the output of
```
ccsm
```
as well as
```
dpkg -l | grep compiz
```
in the terminal.

---

### Post by MrTre1z3 on 2007-09-22
Hello everybody.

I installed compiz fusion on ubuntu studio and I have a problem too. I can go to the "CompizConfig Settings Manager" and I started compiz doing "compiz --replace" but I can't do any effects, nor even the cube rotation. 

The output of the ccsm command is:
```
Info: No sexy-python package found, don't worry it's optional.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

I'm newbie and I don't know how to remove those things..

The output of dpkg -l | grep compiz is:
```
ii  compiz                                     0.5.5~git20070921+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070921+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070921+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070921+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-gnome                               0.5.5~git20070921+3v1ubuntu0           OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             0.5.5~git20070921+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070921+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2~git20070918+3v1ubuntu0           GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu2           Settings library for plugins - Compiz Fusion
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration
```

Could anyone help me?
Thanks in advance

---

### Post by Forlong on 2007-09-22
> **MrTre1z3 said:**
> I'm newbie
Then you shouldn't use this repository. Try [this](http://ubuntuforums.org/showthread.php?t=536149) instead.

---

### Post by MrTre1z3 on 2007-09-22
Thanks a lot Forlong =) 
I followed your tutorial and now it's working but not the cube effects. Maybe I should reboot to get it totally functional. Your tuto is awesome. thanks again.
I have one question more: I went to System &#8594; Administration &#8594; Restricted Drivers Manager and chose to not use these drivers. Have the free radeon drivers been restored?

Thanks ;)

edit: forgot about the cube.. I found your other page about Compiz configuration =)

---

### Post by Forlong on 2007-09-22
> **MrTre1z3 said:**
> I have one question more: I went to System &#8594; Administration &#8594; Restricted Drivers Manager and chose to not use these drivers. Have the free radeon drivers been restored?
That is most certainly the case. If you want to check, open your xorg.conf
```
gedit /etc/X11/xorg.conf
```
(if you don't know where to look, there's a sample in the [How-To](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) &#8594; Troubleshooting &#8594; Compiz doesn't work at all &#8594; ATI user)

---

### Post by MrTre1z3 on 2007-09-22
Thanks again for all your help = )

---


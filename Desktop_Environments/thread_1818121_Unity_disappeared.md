---
title: "Unity disappeared"
date: 2011-08-04
forum: Desktop Environments
---

### Post by thunderbirdje on 2011-08-04
Hello,

I want to use Unity (Ubuntu 11.04). It's not anymore in the list of sessions at the login page.

I've tried to run 'unity' from the command line like was suggested in another post resulting in failure (see below).

In the Ubuntu Software it's installed.

Hope someone can guide me? 

Thank you!!!

```
#unity
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

```

---

### Post by akoskm on 2011-08-04
Happened with me too after an upgrade of unity-2d, actually it is still missing.
After typing unity in command line have you checked is it started on another tty?
Example I usually start gdm it on tty4 and when I type
```

sudo service gdm stop
sudo service gdm start

```
gdm will appear on tty7.
To swithc between tty-s hit Ctrl+Alt+(F1, F2, ...).
Hope that same thing applies to unity too.

---

### Post by Krytarik on 2011-08-04
Remember, the session option for Unity is actually called "Ubuntu", not "Unity" as you might expect.

Greetings.

---

### Post by thunderbirdje on 2011-08-04
> **akoskm said:**
> Happened with me too after an upgrade of unity-2d, actually it is still missing.
After typing unity in command line have you checked is it started on another tty?
Example I usually start gdm it on tty4 and when I type
```

sudo service gdm stop
sudo service gdm start

```
gdm will appear on tty7.
To swithc between tty-s hit Ctrl+Alt+(F1, F2, ...).
Hope that same thing applies to unity too.

I've tried this... No Unity on any tty. Only GNOME (tty 8). No luck here... :o. Is there a command to start unity (instead of just typing 'unity'?

---

### Post by thunderbirdje on 2011-08-04
> **Krytarik said:**
> Remember, the session option for Unity is actually called "Ubuntu", not "Unity" as you might expect.

Greetings.

Thank you for pointing that out. I've tried (even all) options but none starts up Unity. 

I however noticed that *Ubuntu* is written in italic. Does this has a meaning?

Maybe my computer (after the upgrade from 10.10 to 11.04) doesn't 'support' anymore Unity and thereby loads gnome? Is there a way to check that? 

Thank you! :-)

---

### Post by thunderbirdje on 2011-08-05
Maybe this screenshot can be of any help:confused:? It appears sometimes when I go to System > Preferences > Appearance.

---

### Post by Krytarik on 2011-08-05
> **thunderbirdje said:**
> 
I however noticed that *Ubuntu* is written in italic. Does this has a meaning?
This only indicates the previously chosen option.
> **thunderbirdje said:**
> 
Maybe my computer (after the upgrade from 10.10 to 11.04) doesn't 'support' anymore Unity and thereby loads gnome? Is there a way to check that? 

The Unity version provided for Maverick 10.10 is not comparable with the its current version, as it is a really early version that uses a completely different base, Mutter instead of Compiz.

Please see this post to check if your video hardware/driver is capable of running Unity, it seems it doesn't think so. Please post the results of these checks, they will also tell us what video hardware is installed and what driver is currently running.
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

---

### Post by thunderbirdje on 2011-08-07
> **Krytarik said:**
> Please see this post to check if your video hardware/driver is capable of running Unity, it seems it doesn't think so. Please post the results of these checks, they will also tell us what video hardware is installed and what driver is currently running.
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Thank you for helping me out so far! I took me some time to reply during the fact that the link provided seemed to be blocked by the GFW in China.

The results:
```
# /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```
```
# /usr/lib/nux/unity_support_test -p --compiz
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes

Compiz supported:         no
```

If you need more information, please ask :-) Although the result is quite self explaining: 'no' and 'no'? Maybe there is a possibility it's a software thing because of the upgrade (I once had to reinstall gnome-desktop as well).

---

### Post by coffeecat on 2011-08-07
> **thunderbirdje said:**
> Maybe there is a possibility it's a software thing because of the upgrade (I once had to reinstall gnome-desktop as well).

It's probably because of your graphics card. As Krytarik explained, Unity in 11.04 is based on compiz for which you need 3d acceleration. At the moment you appear to be using an open source video driver but the output you posted doesn't include the type of GPU. It's possible, depending on the GPU, that a proprietary driver may be available that will give you compiz. What graphics card do you have?

---

### Post by thunderbirdje on 2011-08-07
> **coffeecat said:**
> It's probably because of your graphics card. As Krytarik explained, Unity in 11.04 is based on compiz for which you need 3d acceleration. At the moment you appear to be using an open source video driver but the output you posted doesn't include the type of GPU. It's possible, depending on the GPU, that a proprietary driver may be available that will give you compiz. What graphics card do you have?

Oh, great to know and thank you for your expertise so far!

My GPU is (according to lspci)
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
```

In between I discovered I could do a Video and Display test in Ubunty (System > Administration > System Test) and one of the tests showed actually the 3D animation. Maybe needed?

I somewhere remember that I didn't use an open source driver before because I believe in an older version of Ubuntu I had compiz manager (although with just the minimum options of effect due my not so 'heavy' GPU).

---

### Post by coffeecat on 2011-08-07
> **thunderbirdje said:**
> 
My GPU is (according to lspci)
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
```


OK - forget what I said about open-source and proprietary drivers. For Intel chipsets you only have the open source driver which is just fine for running Unity with most Intel graphics. But I think your Intel chipset is too old to be capable of running Unity 3d. I've seen a few threads where people were having problems with the 9** series.

But all is not lost. Boot into the classic desktop and install the package unity-2d, and then log out and log into unity 2d. I can't remember exactly what it is called at the login screen, but you will get a unity desktop but without 3d acceleration. It's not quite as pretty as the Unity 3d desktop, but it gives you most of the functionality.

---

### Post by thunderbirdje on 2011-08-07
> **coffeecat said:**
> OK - forget what I said about open-source and proprietary drivers. For Intel chipsets you only have the open source driver which is just fine for running Unity with most Intel graphics. But I think your Intel chipset is too old to be capable of running Unity 3d. I've seen a few threads where people were having problems with the 9** series.

But all is not lost. Boot into the classic desktop and install the package unity-2d, and then log out and log into unity 2d. I can't remember exactly what it is called at the login screen, but you will get a unity desktop but without 3d acceleration. It's not quite as pretty as the Unity 3d desktop, but it gives you most of the functionality.

Thank you so much coffeecat and all others for helping me out. My laptop is indeed quit old (I think 3-4 years almost). I did a search on the intel 9** and unity which seems to give quite some trouble(s). So I took your advice and went for the Unity 2D.

As it turns out it's also called "Unity 2D" at the login screen and just added to the list with already existing sessions ;-)

Thank you again! Now I can play with unity! :D :D :D

---

### Post by Krytarik on 2011-08-07
First of all, sorry for the blocked site, China's GFW is blocking all Blogspot sites. Had I known that you are located in China, I had provided at least the commands for the checks directly.

To your issue, although you already seem to be happy with the found solution, I'm curious if the "intel" driver - or more accurately, one of its childs - is actually running.

So, if you don't mind, please post the output of this command:
```
lshw -c video
```If it doesn't return "ixxx" as the driver, try creating a bare minimum "/etc/X11/xorg.conf" to load it:
```
gksudo gedit /etc/X11/xorg.conf
``````
Section "Device"
        Identifier      "Intel"
        Driver          "intel"
EndSection
```

---

### Post by thunderbirdje on 2011-08-09
> First of all, sorry for the blocked site, China's GFW is blocking all Blogspot sites. Had I known that you are located in China, I had provided at least the commands for the checks directly.

Oh, you don't have to apologize for that! I'm happy with your help.

> **Krytarik said:**
> To your issue, although you already seem to be happy with the found solution, I'm curious if the "intel" driver - or more accurately, one of its childs - is actually running.

So, if you don't mind, please post the output of this command:
```
lshw -c video
```If it doesn't return "ixxx" as the driver, try creating a bare minimum "/etc/X11/xorg.conf" to load it:
```
gksudo gedit /etc/X11/xorg.conf
``````
Section "Device"
        Identifier      "Intel"
        Driver          "intel"
EndSection
```

Always open to experiments! :D

The output for lshw -c video:

```
#lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f8000000-f80fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff
```

I've created a bare minimum "/etc/X11/xorg.conf"-file and loaded it.

The output seems the same:
```
#lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f8000000-f80fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff

```

I noticed that now "Unity" is used as environment when selecting "Ubuntu" at the login screen. Before the same choice provided me with GNOME. Although I'm not sure, maybe it's because by installing Unity 2D before that this have changed now.

Hope the output of the commands give more information ;-) If you have any suggestions, let me know! :-)) I'm still open to test! :D

And thank you for all your effort!

---

### Post by Krytarik on 2011-08-09
Thanks for the check. As you can see in both outputs, "i915" is being run as the driver, so it's ok.

Surprisingly though, that after only installing Unity-2D, you even get the 'real' Unity now. But who cares, if it works, eh!? ;-)

However, if it again stops working, try to 'force' Unity to run. Excerpt from my guide I linked to earlier:

Add "UNITY_FORCE_START=1" to "/etc/environment":
```
gksudo gedit /etc/environment
```
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
UNITY_FORCE_START=1
```
Greetings.

---


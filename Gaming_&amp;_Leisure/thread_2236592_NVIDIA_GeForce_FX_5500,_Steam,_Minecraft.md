---
title: "NVIDIA GeForce FX 5500, Steam, Minecraft"
date: 2014-07-27
forum: Gaming &amp; Leisure
---

### Post by kendra2 on 2014-07-27
Well, I hope this is the right place to post this.

I just installed Lubuntu a few days ago. I have been getting used to the change from Windows, and was able to install steam. However, it is not working for me. When I was on windowsXP, steam and several of it's games worked fine, despite my old hardware. Now it wont even open. 
[Here's]("http://i.imgur.com/YrNCCv9.jpg") the message I get when I try to open Steam. I am unable to press Okay or exit any Steam application for at least five minutes. When it lets me press Okay, it all closes. 

NVIDIA GeForce FX 5500 is my graphics card if this helps at all. 

Also, I downloaded and started Minecraft, since I hadn't played it in a while. The FPS does not go above 10, in game or in menu. Is this an issue I can fix? 
Still new to the Lubuntu OS, so non-complex answers are apprechiated. Thanks!

---

### Post by oldrocker99 on 2014-07-27
Which nVidia driver do you have installed? You may be running open-source drivers, which are much slower (currently) than the nVidia drivers, currently 3.40.24.

---

### Post by kendra2 on 2014-07-27
> **oldrocker99 said:**
> Which nVidia driver do you have installed? You may be running open-source drivers, which are much slower (currently) than the nVidia drivers, currently 3.40.24.

From my Additional Drivers page it says-
Using NVIDIA legacy binary driver -version 173.14.39 from nvidia-173 (proprietary, tested).

---

### Post by oldrocker99 on 2014-07-27
You might try the xorg-edgers PPA, which is where the latest nVidia (and other) drivers can be found.
Open a terminal and type this:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install dkms
sudo apt-get upgrade
```

Installing dkms allows the system to upgrade the kernel without your having to reinstall the video driver. If there are more recent drivers, this will install them. If it doesn't update the drivers, you can look in Synaptic for "nvidia" and see if there are more updated ones.

---

### Post by kendra2 on 2014-07-27
Alright, I went through Synaptic and got a more recent one, 310 and restarted my computer afterwards. Now when I try to open steam, it gives me [this]("http://i.imgur.com/ItuMj5i.jpg?1?5530").

---

### Post by oldrocker99 on 2014-07-28
Have you run nVidia XServer (in Preferences)? What is your output of

```
glxinfo
```

Please post. You **may** need to reinstall the nVidia driver, and the 3.10 driver is still pretty old.

---

### Post by kendra2 on 2014-07-28
> Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".


This is what I recieve after entering glxinfo.

How would I go about reinstalling the driver?

---

### Post by oldrocker99 on 2014-07-29
```
sudo apt-get purge nvidia*
sudo apt-get install nvidia-[whatever]
```

This is the usual way to reinstall the driver; good luck!

---

### Post by holastickboy on 2014-08-19
The GeforceFX 5500 is a really old GPU, are you sure that the new drivers would even work with it?

---

### Post by oldrocker99 on 2014-08-20
nVidia doesn't obsolete their old cards the way ATI does; and they currently support back to the 5 FX series, so, yes, I think it would work.

---

### Post by frank18 on 2014-09-12
> **oldrocker99 said:**
> nVidia doesn't obsolete their old cards the way ATI does; and they currently support back to the 5 FX series, so, yes, I think it would work.

oldroker99, i just installed this video card on xubuntu14.04 ,it works well on VGA but the Svideo is Black& white, i use Xxorg drivers,the legacy  don't work at all on vga.

---

### Post by R33D3M33R on 2014-09-15
> **oldrocker99 said:**
> nVidia doesn't obsolete their old cards the way ATI does; and they currently support back to the 5 FX series, so, yes, I think it would work.

Don't be so sure about that. My experience with older nVidia cards on (K)Ubuntu 13.04 and 12.04 was pretty bad: [http://ubuntuforums.org/showthread.php?t=2141611](http://ubuntuforums.org/showthread.php?t=2141611)

@[**[COLOR=#000000]frank18[/COLOR]**]("http://ubuntuforums.org/member.php?u=1854911"): look here: [http://ubuntuforums.org/showthread.php?t=1001756](http://ubuntuforums.org/showthread.php?t=1001756).

---


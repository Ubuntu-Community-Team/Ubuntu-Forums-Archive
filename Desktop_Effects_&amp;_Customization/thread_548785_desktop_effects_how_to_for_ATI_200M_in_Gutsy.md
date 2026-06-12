---
title: "desktop effects how to for ATI 200M in Gutsy"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by android6011 on 2007-09-11
Recently ATI/AMD have decided to opensource their driver. I was happy to hear this news, but for now this is how to enable desktop effects for the ATI 200M card in Gutsy. I am not sure what other cards this will work for so feel free to leave comments saying if it worked for you, or if you have any questions I might be able to help you with

The first thing to do is enable the ATI driver:

```
System -> Administration -> Restricted Drivers
```

```
ATI accelerated graphics driver -> Enable [Click Enable when prompted] 
```

When I tried getting things working the first time I was just messing around, but enabling this didn't actually break anything, but I am not sure if this step is required. At the terminal type:

```
sudo gedit /etc/X11/xorg.conf
```

Then find this and change the "0" to "1"

```
Section "Extensions"
	Option		"Composite"	"1"
EndSection

```
Next we will use XGL to get things going

```
sudo apt-get install xserver-xgl
```

now restart X by pressing ctrl+alt+backspace

Now we can enable the desktop effects through Ubuntu

```
System -> Preferences -> Appearence -> Desktop Effects -> Enable Extra Effects
```

This is not required, but if you would like to choose effects etc install the Compiz Config Manager

```
sudo apt-get install compizconfig-settings-manager
```

```
System -> Preferences -> CompizConfigManager 
```

I would like to thank the Ubuntu developers for helping make the process of getting desktop effects going easier and I look forward to the final release of Gutsy

side information:

I only decided to check these after everything was working, but I figured I would add this incase anyone wanted to know. 
```

android6011@b0xybr0wn:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```
```

android6011@b0xybr0wn:~$ glxinfo | grep OpenGL
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:

```
```

android6011@b0xybr0wn:~$ lspci
...
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
...

```

---

### Post by amadeus266 on 2007-09-12
Is is possible that this may also work in feisty? I don't have that particular card but I know some other people who do.

---

### Post by vl_ado on 2007-09-12
> **amadeus266 said:**
> Is is possible that this may also work in feisty? I don't have that particular card but I know some other people who do.

I have exactly the same card with my Compaq Presario V2650Ca and to tell you the truth I had to install ubuntu so many times because i mess up with the 3d effects :(

---

### Post by Forlong on 2007-09-12
Please don't use this on Feisty.
Do not set the Composite option to "1" while using the fglrx driver. This will break your usual session and you won't be able to use your system without Xgl.

Xgl will work just fine with compoite disabled when using a separate session (see [here](https://help.ubuntu.com/community/CompositeManager/Xgl)). That's only for AIGLX of Ubuntu's X-Server.

---

### Post by the yawner on 2007-09-12
> xserver-xgl
This will certainly speed up and simplify the setting up of XGL. Nice.
I wish there'd be a Feisty deb, but only because I'm impatient to try this package without going Gutsy (until it's finally released). Haha!

---

### Post by raxz on 2007-09-12
So these commands won't fix the "Desktop Effects"?

I installed the ATI driver for my 9600 on feisty and I tried enabling the Desktop effects and I got an error "The Composite Extension is not Available".

I was hoping this thread would be my answer :)

---

### Post by the yawner on 2007-09-12
Not so I'm afraid. The XGL package is only available on Gutsy and as long as ATI's latest driver does not have AIGLX support you'll have to either isntall/setup an XGL on your Feisty install (which is what I did on my Thinkpad R51e with an ATI 200M), or just go with Gutsy and it's XGL package which something very useful for people with ATI/Compiz woes.

---

### Post by android6011 on 2007-09-12
> **raxz said:**
> So these commands won't fix the "Desktop Effects"?

I installed the ATI driver for my 9600 on feisty and I tried enabling the Desktop effects and I got an error "The Composite Extension is not Available".

I was hoping this thread would be my answer :)

did you try changing the "0" to "1" in xorg.conf? that is the only way I know to enable composite, if that doesn't work then you will need a separate work around I guess

---

### Post by raxz on 2007-09-16
> **Forlong said:**
> Please don't use this on Feisty.
Do not set the Composite option to "1" while using the fglrx driver. This will break your usual session and you won't be able to use your system without Xgl.

Xgl will work just fine with compoite disabled when using a separate session (see [here](https://help.ubuntu.com/community/CompositeManager/Xgl)). That's only for AIGLX of Ubuntu's X-Server.

Does this apply to me as well? So it's not really recommended for noobs to play with Compiz/XGL stuff?

---

### Post by Forlong on 2007-09-16
> **raxz said:**
> Does this apply to me as well? So it's not really recommended for noobs to play with Compiz/XGL stuff?
If you want to use the fglrx driver, you have to install Xgl [like this](https://help.ubuntu.com/community/CompositeManager/Xgl). And when you have you can use Compiz or Beryl.

btw: with your graphics card I recommend removing the fglrx driver, then desktop effects will work out-of-the-box (without Xgl). :)

---

### Post by mrgnash on 2007-10-03
Doesn't work for me. XGL is displays artifacts, runs slowly, and when I try to run compiz it gives the error about not being able to pass two textures. My card is a X700 mobility.

---

### Post by foundation on 2007-10-04
I just wanted to say thank you, everything is working perfectly now. :)

---

### Post by BinaryMadman on 2007-10-07
I have an ATI 200M just like the original poster and sure enough, it worked!  I was a little worried given my inability to get this working on Feisty but the simple steps provided got things done.  I have to say, this really makes Ubuntu feel more modern to me - it's the minor things (drop-shadowed windows & tooltips, minimizing animations, window previews, etc.). :)  Gutsy is going to be a great release!

---

### Post by Unnicknamed on 2007-10-14
Excellent, this worked for me. Thank you.

---

### Post by drascus on 2007-10-19
umm it worked it worked it worked!!!!! I have tried so many things in the past but this one worked!! I would kiss your feet if I could but I am sure you think that is unnecessary. Please post a Howto... thank you!!

---

### Post by cro_crx on 2007-10-19
I also have a 200M, while this works great, is there a way to enable direct rendering with this video card ??? I have tried almost everything i can think of to get it to work with no luck.... is it possible ?

Also what FPS are you getting roughly ... my laptop with a Pentium m 1.6hz 768mb ram gets roughly ~ 120fps while doing nothing, 50-60 while rotating the cube etc....

---

### Post by What_the_deuce on 2007-10-19
Great guide. Made setting up XGL in my shiny new Gusty install really simple. One problem though, it laggs, a lot. I had it on Feisty and it was fine. For some odd reason. the effects lag.

Any idea why and how do i fix i?t

---

### Post by Odice on 2007-10-19
This guide works. I just had a problem after rebooting (weird colors on screen and a fallback to basic colors) but i just disable fglrx, reboot, and enable again, and now everything is fine. I just have a question. Its normal the the Direct Render: No, as you show on you logs?.

Thank u man :D

---

### Post by petzworld999 on 2007-10-20
This works for Compiz. Will it work for Beryl?

---

### Post by shriek on 2007-10-27
I have gutsy with ATI 200M installed and all the eye candy turned on. I'm trying to run Warsow but it keeps saying that I don't have direct rendering. Is this true? if I don't have direct rendering would I be able to run all these compiz effects?

---

### Post by Lucky Parker on 2007-12-19
thank you... i couldn't figure this out for the longest time.... worked flawlessly on my Hp Pavilion zv6000 64 amd

---

### Post by What_the_deuce on 2007-12-19
Hi all

Does anyone know how to get direct rendering to work with this card and the FGLRX  driver?

I have spent all evening trying to find out how, no luck so far
I installed x11proto-xf86dri-dev, after searching Synaptic for "XFree86-DRI" as in the missing extension thats apparently stopping direct rendering

Thanks

---


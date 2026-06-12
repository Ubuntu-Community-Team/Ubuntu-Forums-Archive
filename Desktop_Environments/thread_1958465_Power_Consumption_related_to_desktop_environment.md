---
title: "Power Consumption related to desktop environment"
date: 2012-04-14
forum: Desktop Environments
---

### Post by raptir on 2012-04-14
Planning on coming back to Ubuntu after a little time away. I just got a new ultraportable and threw Fedora on it until 12.04 releases. Fedora is decent, but I think I'm coming back to Ubuntu.

I am running gnome-shell currently and I'm getting pretty disappointing battery life compared to with Windows. I like gnome-shell, and Unity looks solid too, but I'm wondering if I would likely see bettery battery life with xfce or lxde. Does anyone have any experiece with power consumption on the different desktop environments? Thanks.

Edit: And my point with this was that I would switch to Xubuntu or Lubuntu rather than Ubuntu if this would be the case.

---

### Post by 3Miro on 2012-04-14
Unless you have too many desktop effects enabled, the DE shouldn't make that much difference on your power consumption. Things like background programs and overall power management of the kernel and drivers should make all the difference. This is also hardware dependent.

Adjusting the settings on your distribution should help more with power consumption than switching the DE. Look at things like jupiter applet and laptop mode.

---

### Post by 2F4U on 2012-04-14
The choice of desktop environment can influence both performance and power consumption. For a more indepth analysis I suggest you read this article on Phoronix.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_precise_desktop&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_precise_desktop&num=1)

The article has benchmarks on various desktops available for Ubuntu 12.04.

---

### Post by raptir on 2012-04-14
I installed Lubuntu and saw an immediate difference. The battery life does not quite match Windows, but it is much better than with Gnome on Fedora. Also, my processor temp went from ~58C when browsing the web to ~50C. I realized that I didn't perform a "controlled experiment" so I installed Gnome on top of Ubuntu and saw the same results. Unity was better, but still significantly worse on battery/temp than lxde. Xubuntu is giving me similar results to Lubuntu. I'll try Jupiter/laptop-mode-tools and see if I can match or beat Windows.

Thank you both for the help.

---

### Post by 3Miro on 2012-04-14
> **raptir said:**
> I installed Lubuntu and saw an immediate difference. The battery life does not quite match Windows, but it is much better than with Gnome on Fedora. Also, my processor temp went from ~58C when browsing the web to ~50C. I realized that I didn't perform a "controlled experiment" so I installed Gnome on top of Ubuntu and saw the same results. Unity was better, but still significantly worse on battery/temp than lxde. Xubuntu is giving me similar results to Lubuntu. I'll try Jupiter/laptop-mode-tools and see if I can match or beat Windows.

Thank you both for the help.

Interesting. It seems that the OpenGL effects are taking a tow on your video card. What type of video card is it? Intel/AMD/Nvidia?

---

### Post by raptir on 2012-04-14
Sorry, I meant to include all that and ask for troubleshooting tips, but I completely forgot.

The laptop is an HP dm1-4170us. It runs a Core i3 2367m with the stock Intel HD 3000 integrated graphics. I have not done any extra system configuration apart from disabling powersave on the wireless due to a bug. Is there anything I can do to decrease power usage with the hd 3000? A better driver than the i915 perhaps?

---

### Post by 3Miro on 2012-04-14
> **raptir said:**
> Is there anything I can do to decrease power usage with the hd 3000? A better driver than the i915 perhaps?

There is no other driver. Unlike AMD and Nvidia, Intel provides fully functioning FOSS drivers for their video cards.

Now I have to do some tests myself, I have the same graphics. Jupiter and Laptop Mode should help, but I don't know of anything specific to the Intel video.

---

### Post by raptir on 2012-04-14
So, quick update. I installed GZDoom, and I cannot get the game to work with the OpenGL renderer. The game loads but freezes as soon as I start an actual game. The game works fine with the software renderer. Any way that I can check if OpenGL is working and performing properly on my laptop? Like a simple benchmark I can install? Thanks.

---

### Post by 3Miro on 2012-04-14
Just installed OpenBox (with just lxpanel, not the entire lxde) on my Laptop Sandy Bridge i7 + Intel 3000 HD. It just made a huge difference on the battery life. 

I am not sure what the deal is, but when I tried it on my old laptop (Intel GMA4500 + Pentium Dual Core), Gnome 2 with Compiz and Metacity made little difference.

Well, now I know how to get more battery life out of my machine.

---

### Post by 3Miro on 2012-04-14
Go to the command line and type:
```
glxinfo | grep direct
```
if you see
```
direct rendering: Yes
```
then you have enabled hardware acceleration. You can also take a look at:
```
glxinfo | grep OpenGL
```

---

### Post by raptir on 2012-04-14
I do get direct rendering: yes from glxinfo. glxinfo | grep opengl returns:

```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2
OpenGL shading language version string: 1.30
OpenGL extensions:

```

...so it seems like OpenGL is at least being loaded properly. Are there any basic/very compatible OpenGL games/tests I can install and run quickly?

Edit: Also, mesa-utils was not installed on my machine and I had to install that to run glxinfo. Not sure if that tells you anything.

---

### Post by 3Miro on 2012-04-15
mesa-utils is just a few helper apps, not the OpenGL itself. It seems that OpenGL is up and running, now the issue may be with a bug in the  game or maybe SandyBridge isn't powerful enough to render this particular game.

Try running the glxgears, with VSync enabled you should get at least 50 - 60 FPS, without it, you should something in the thousands.

---

### Post by raptir on 2012-04-15
glxgears runs at ~59.8 FPS with Vsync on, but I don't know how to disable Vsync. However, I believe this is a problem with the game itself. I was able to run Skulltag, which is another engine based on Gzdoom, with the OpenGL renderer with no problem. I was also able to run Darkplaces, which is an OpenGL Quake engine that is much more demanding, with no issue. I'll take this over to the gzdoom forums. Thanks again.

---

### Post by 3Miro on 2012-04-15
> **raptir said:**
> glxgears runs at ~59.8 FPS with Vsync on, but I don't know how to disable Vsync. However, I believe this is a problem with the game itself. I was able to run Skulltag, which is another engine based on Gzdoom, with the OpenGL renderer with no problem. I was also able to run Darkplaces, which is an OpenGL Quake engine that is much more demanding, with no issue. I'll take this over to the gzdoom forums. Thanks again.

59.8 is what you should get with Vsync, things are working right it seems.

If you have no more questions, you can mark this thread as "Solved".

---


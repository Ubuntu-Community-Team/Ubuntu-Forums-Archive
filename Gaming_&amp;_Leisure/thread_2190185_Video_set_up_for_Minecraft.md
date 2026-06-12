---
title: "Video set up for Minecraft"
date: 2013-11-26
forum: Gaming &amp; Leisure
---

### Post by afnqx3 on 2013-11-26
Hello, first i have to say i'm on elementary os and not ubuntu, but i don't think that will change anything.
So: i installed Minecraft on my distro, but it's running 20-30 fps lower than Minecraft on Windows on the same machine.
I guess it's because i don't have nvidia drivers installed (i have a Geforce 60m + an intel video card).
i tried to install the correct video driver a few days ago and that caused the os not to show up the DE and other problems, so i'm a bit afraid of installing it again.
what can i do to run minecraft properly?


```

lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev a1)


glxinfo | grep direct
direct rendering: Yes



cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: no such file or directory (very strange imho)


```

---

### Post by dannyboy79 on 2013-11-26
its most likely as you stated, that you're using the built in intel graphics card versus the discrete card. you need to look into either bumblebee or vga_switcheroo to disable your built in card. i don't have any experience with this so i can't help specifically BUT i can help if you have issues while following 1 of the tutorials. Good luck
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by efflandt on 2013-11-26
You may need to use **nomodeset** boot parameter, especially with 2 different types of graphics. That way modules would be used for graphics instead of built-in kernel modeset trying to do that.

It looks like "elementary OS" is somewhat based on Ubuntu 12.04 or at least can use its packages. So you would likely need to follow instructions for getting bumblebee and nvidia drivers working on that. I have not done a laptop with dual graphics in 12.04, so not sure if installing nvidia drivers after installing **bumblebee** automatically installs **bumblebee-nvidia** or if you also need to install that. I use **nvidia-experimental-310** drivers (which now load a 319 version) on both my 12.04 desktop with GTX 550 Ti graphics and 13.10 laptop with Intel HD 4600 and nvidia GTX 765M graphics.

I have not run minecraft on my laptop yet, but I imagine once you get bumblebee and nvidia drivers installed you would launch the minecraft launcher with:```
optirun java -jar actual_path_to/Minecraft.jar
```optirun would run it on the nvidia graphics.

---


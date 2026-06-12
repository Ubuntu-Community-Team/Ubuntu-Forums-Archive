---
title: "[SOLVED] OpenGL is not working since reinstalled Gutsy :\"
date: 2008-01-22
forum: Gaming &amp; Leisure
---

### Post by b0rka7a on 2008-01-22
OpenGL is not working since the last reinstall of Gutsy.
I've installed my nVidia drivers with Envy, because these from Restricted Drivers Manager didn't worked. My graphics card is nVidia 7300GT 256MB.
I know that OpenGL is the problem, because I'm trying to run CS: 1.6 in opengl mode and the game doesn't want to start. It's working in D3D and Software mode, but i don't want them.

I'm waiting for a solution...
Thanks!

---

### Post by Sockerdrickan on 2008-01-22
...d3d mode in wine is obviously opengl since there is no direct3d in linux world.

---

### Post by b0rka7a on 2008-01-22
But the game has bugs when it's in D3D mode ;( I need it to run in OpenGL mode but it can't start it in opengl, and in d3d it has bugs ?! Any idea please!! I was playing in opengl before I reinstalled my Ubuntu and I don't know what's wrong now.

Screenshots of the game are attached below.
1 - I can see the shots through the walls
2 - I can see other details through the walls like the hostage rescue area

Please help me!! :(

---

### Post by padawan555 on 2008-01-26
Same here.
*Everything* requiring openGL makes the computer logoff and directely go to the login screen.
Have not been able to figure out why at all.

---

### Post by Sockerdrickan on 2008-01-26
You fix this by manually installing the video driver again.

---

### Post by Sockerdrickan on 2008-01-26
my nVidia how2:

```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

---

### Post by padawan555 on 2008-01-27
It worked. Thank you.
Although not perfectly: I had to install the NVIDIA drivers again with envy, after following your instructions. Maybe I did something wrong.
Thanks anyway.

---

### Post by b0rka7a on 2008-01-27
Tux0r, THANK YOU, THANK YOU, THANK YOU !!! :D
:lolflag:

---

### Post by Sockerdrickan on 2008-01-27
You are welcome everyone! :KS

---


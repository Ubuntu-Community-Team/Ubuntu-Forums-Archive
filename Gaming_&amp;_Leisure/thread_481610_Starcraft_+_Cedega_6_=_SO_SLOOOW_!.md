---
title: "Starcraft + Cedega 6 = SO SLOOOW !"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by lospo on 2007-06-22
Hi, i've installed cedega 6, and i try to play starcraft but... it doesn't work!!!

The installation of the game is clean and quick, i can see the intro film but when i have to choose ehat to do (single player, multiplayer or campaign editor) is SO SLOOOOW !

I've go an AMD Athlon 3000+ Single core 64bit, 512 Mb RAM (64 shared), Integrated GeForce 6800. 

Cedega pass all test (OpenGL and glx... only green square)

I'm using Ubuntu 7.04 (clean install) + NVidia driver 100.14.something and all other things (such games, programs firefox...) seems to work great!

Please someone tell me something... i've lost my faith...

Thank you so much.

---

### Post by jinx099 on 2007-06-22
try Wine.  Last time I installed starcraft with regular wine it worked great!

---

### Post by lospo on 2007-06-22
i've tried to launch the executable by wine... blak screen with audio, only hard reset (push the button) save me.

> nice -n 20 wine "starcraft.exe" 

In every forum that i navigate someone always say that install SC by cedega is so simple... am i a stupid??

Thanks for reply.

---

### Post by wingnux on 2007-06-22
It works at full speed here but I have an ATI card... Do you have direct rendering enabled?
On terminal: glxinfo | grep "direct rendering"

---

### Post by lospo on 2007-06-23
> 
lospo@bobogrigio:~$ glxinfo | grep "direct rendering"
direct rendering: Yes


](*,)](*,):cry::cry:

My Nvidia 6800 isn't enough for Starcraft???
I know, it isn't the best but...

Thank you for any reply.

---

### Post by vem0m on 2007-06-23
Ummmmmm just use wine..... Cedega is good for some games and Wine for others in this case Wine is the better

---

### Post by Enverex on 2007-06-24
When using Starcraft on Wine, you can enable the OpenGL renderer for DirectDraw and it will speed it up massively.

Download this file: [http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg](http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg)
Run "wine regedit" in a terminal and then import this registry file and watch Starcraft fly.

---

### Post by ViperKnight on 2007-06-25
Starcraft in Cedega runs smooth as anything on my desktop and even my crappy laptop!
My laptop is only a Pentium M 1.63ghz, 512mb ram and an Intel855GM video card (about as powerful as those really old Nvidia TNT2 cards....so pretty pathetic!!).

I can only think of these things:
1) Disable MMAP for audio and use ALSA.
2) Disable Compiz or Beryl if they're running.  Since there's no 3D rendering it shouldn't be that bad...but give it a shot.
3)Change "Desktop" to 640x480 to run Starcraft in a window.
4. Use XRandR video mode instead.

Apart from that....try Wine :P

---


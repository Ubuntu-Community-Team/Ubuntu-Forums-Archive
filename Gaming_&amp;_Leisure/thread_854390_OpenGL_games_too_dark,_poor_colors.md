---
title: "OpenGL games too dark, poor colors"
date: 2008-07-09
forum: Gaming &amp; Leisure
---

### Post by trazart on 2008-07-09
I have installed Quake 3 on Ubuntu Hardy. I'm using nvidia propietary drivers.

The problem is the game looks too dark. I think it is not a gamma problem, it's not just dark but colors are poor, there are no lights in the game. It may be an opengl related problem.

This is a screenshot under Ubuntu:
[IMG]http://img241.imageshack.us/img241/2357/qwrongmx5.jpg[/IMG]

and this is under Windows:
[IMG]http://img241.imageshack.us/img241/4197/qrightfd0.jpg[/IMG]

Both have the same settings. As you can see 2D objects are fine, they have the same brightness.

I installed Doom 3 and it has the same problem. It is EXTREMELY dark.

Can anyone help me? Thanks

---

### Post by nikgare on 2008-07-10
Are both machines using the same resolution?

---

### Post by trazart on 2008-07-10
Yeah, same machine, same monitor at 1680x1050, same config file for the game.

Under Windows, if I play in window mode the game looks dark as under Ubuntu.

---

### Post by nikgare on 2008-07-10
I don't have time for games any more :-( Is quake 3 native or running under wine?

---

### Post by trazart on 2008-07-11
It is native. I have installed the latest linux updates for Quake 3 and Doom 3.

You have time, you just choose how you spend it ;)

---

### Post by hessiess on 2008-07-11
try playing with the settings in
```

sudo nvidia-settings
```

you may need to install the nvidia-settings applet first

---

### Post by nikgare on 2008-07-11
There is a setting in nvidia-settings which might fit the bill:
Under Antialiasing there is a tick box for texture sharpening and the help says
"To improve image quality, select this option to sharpen textures when running OpenGL applications with antialiasing enabled"

Sounds promising

---

### Post by trazart on 2008-07-13
I have been playing with the nvidia-settings with no luck.

BTW I'm not using antialiasing. Thank you for the replies

---

### Post by lordhaworth on 2008-07-14
I am having the same trouble with doom 3 it is too dark really to even play at all. If I find any solution I'll let you know, similarly ill be keeping an eye on this thread!

---

### Post by lordhaworth on 2008-07-14
Have you tried changing the brightness/ gamma / lightscale from the in game console? 
Im working from a different computer tonight so cant test at the mo

>bring up the in game console
>type r_gamma and then a number from 1 to 2
the default is 1, so increasing this may improve visibility


could also try the same with

>r_brightness and then a number from 1 to 2
however this setting may be no different to changing the brightness in the regular options menu--->which I didnt find helped at all!

---

### Post by trazart on 2008-07-15
I have tried that but that is not the solution. Increasing the gamma/brightness improves visibility and makes the game more playable, however textures are wrong, I'm sure it is not how it should look.

I will try uninstalling the restricted nvidia drivers.

BTW, what's your card, drivers, distribution?

---

### Post by trazart on 2008-07-16
I tried running in software mode using the mesa driver and there was no difference :(

---

### Post by lordhaworth on 2008-07-16
heya i've still had no real improvement im quite busy at the mo so getting this sorted has been pushed aside a little! Im still working on it though

My Spec...

Base	Intel® Celeron Processor 550 (2.0Ghz, 533 MHz FSB, 1 MB L2 cache) - N-Series
Memory	2048MB 667MHz Dual Channel DDR2 SDRAM [2x1024]
Video Card	Integrated Intel® Graphic Media Accelerator X3100

I've seen this problem posted elsewhere so i would assume ill be able to find a solution eventually

---

### Post by lordhaworth on 2008-07-16
Oh yeah
Im running hardy

---

### Post by trazart on 2008-07-26
I solved it using Wine!

Install the latest version. Then you have to copy your windows doom3 folder to the .wine/drive_c folder.
Then just run Doom3.exe.

Linux native mode
[[IMG]http://img142.imageshack.us/img142/3069/d3linuxrt3.th.jpg[/IMG]](http://img142.imageshack.us/my.php?image=d3linuxrt3.jpg)


Using Wine
[[IMG]http://img210.imageshack.us/img210/3262/d3wineaj7.th.jpg[/IMG]](http://img210.imageshack.us/my.php?image=d3wineaj7.jpg)

---

### Post by desertboy on 2008-07-27
LMAO you had to use wine to solve your linux binary problems, congrats that's pretty much what I would have done.

Doom3 ran fine for me on Gutsy with nvidia drivers for 8800GTS but I no longer have it (I gave it away) and have long since switched to Hardy.

---

### Post by lordhaworth on 2008-07-28
Awesome cheers there!

---

### Post by xblackxphoenix on 2008-08-06
i'm having the same problem with doom 3 running natively, except the only light comes from computer screens inside the game. did anyone find a solution besides wine?

---

### Post by Vrils on 2012-01-08
this is an OpenGL problem since i also have it in many games and on Windows 7
if i use OpenGL i can`t control the gamma, it just doesn`t work and everything is darker

one solution is to open my nvidia control panel and force gamma from there until i play my games then reset

---

### Post by Perfect Storm on 2012-01-09
Necromancing, thread closed.

---


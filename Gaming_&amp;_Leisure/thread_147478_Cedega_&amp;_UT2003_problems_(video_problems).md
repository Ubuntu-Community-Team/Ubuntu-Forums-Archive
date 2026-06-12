---
title: "Cedega &amp; UT2003 problems (video problems)"
date: 2006-03-20
forum: Gaming &amp; Leisure
---

### Post by Pyronhell on 2006-03-20
Hi!!
After install UT on my PC... I install Cedega & UT2003, but... 2 things:
1- Ut2003 is on the lowest graphic quality, in-game is good except when (in a large map) I saw all the terrain (too polygons), that it "rumbles" (Spanish: tirones).
2- I have installed the Nvidia drivers with Automatix, but when I run the Hardware test con Cedega, it says me that I don't have correctly installed the drivers :S

Attached: a screen with the cedega and glxgears running

With cedega closed:
```
pyronhell@pyronhell:~$ glxgears -printfps
1016 frames in 5.0 seconds = 203.089 FPS
1000 frames in 5.0 seconds = 199.958 FPS
974 frames in 5.0 seconds = 194.798 FPS
981 frames in 5.0 seconds = 196.105 FPS
973 frames in 5.0 seconds = 194.562 FPS
980 frames in 5.0 seconds = 195.825 FPS
952 frames in 5.0 seconds = 190.179 FPS
992 frames in 5.0 seconds = 197.269 FPS

``` 
With ALL APPs closed...
```
pyronhell@pyronhell:~$ glxgears -printfps
1055 frames in 5.0 seconds = 210.923 FPS
1032 frames in 5.0 seconds = 206.336 FPS
1023 frames in 5.0 seconds = 204.532 FPS
1023 frames in 5.0 seconds = 204.512 FPS
1026 frames in 5.0 seconds = 205.053 FPS
1024 frames in 5.0 seconds = 204.745 FPS
1018 frames in 5.0 seconds = 203.536 FPS
1016 frames in 5.0 seconds = 203.090 FPS
1020 frames in 5.0 seconds = 203.902 FPS

``` 
Is this normal?

My PC:
Pentium III 500 Mghz (OvClk -> 560 Mghz)
256 MB RAM DDR 133
Nvidia GeForce 2 MX 200/400 64 MB

Half Life needs a Pentium233 Recommended... I suppose that it can run normal on cedega, can it?

PD: Escuse my very bad english, I'm spanish :'(

Thanks to all

---

### Post by el3ktro on 2006-03-20
I'm just wondering why you try to run UT2003 trough Cedega, when you can download a native version for Linux?

Tom

---

### Post by Pyronhell on 2006-03-21
I havent installed UT2003 with Cedega, I have installed it with the native installer on CD3, I install Half Life with Cedega.

---

### Post by Horndog on 2006-03-21
UT2003 was never meant to run on a system with your specs. You need to upgrade at least your processor.

---

### Post by Pyronhell on 2006-03-21
And Half Life on Cedega?

---

### Post by Horndog on 2006-03-21
Sorry, I don't have or use the other programs so I don't have an answer.

---

### Post by Silwenae on 2006-03-22
Half-life isn't going to run on Cedega with those specs.  It would barely work on Windows.  Your RAM is the biggest problem for Half-Life.

---

### Post by Pyronhell on 2006-03-23
Ano.......
The Half Life requeriments (RECOMMENDED REQUERIMENTS)
Pentium 233, 32 MB of RAM & VGA 16bit

---

### Post by NXArmada on 2006-03-23
Pyron to get Cedega to display the gears and get your 3D Acceleration working you need to enable it in your XConfig file.

Since you have an NVIDIA card you well want to use NVIDIA drivers for your xserver.  I suggest you make the change I provide below to your xconfig.

Stop your xserver
At the terminal do: sudo nano /etc/X11/xorg.conf

Remove the line:

      Driver "nv"
  (or Driver "vesa")
  (or Driver "fbdev")

and replace it with the line:

    Driver "nvidia"

Remove the following lines:

    Load "dri"
    Load "GLCore"

In the Module section of the file, add the line (if it does not already exist):

    Load "glx"

Hit CTRL+X and yes to save and yes to overwrite

type STARTX to start your x server and try the cedega tests again.

---


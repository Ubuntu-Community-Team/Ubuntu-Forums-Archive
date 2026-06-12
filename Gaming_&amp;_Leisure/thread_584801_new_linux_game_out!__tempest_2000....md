---
title: "new linux game out!  tempest 2000..."
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by Cresho on 2007-10-21
This guy just released the tempest clone.  you can view the game in youtube here.   
[http://www.youtube.com/watch?v=hbPCUYkcHow](http://www.youtube.com/watch?v=hbPCUYkcHow)

download it from here
[http://dogfight.cheops.php-4.info/typhoon_2001_r3992.tar.gz](http://dogfight.cheops.php-4.info/typhoon_2001_r3992.tar.gz)

this is the home site.
[http://typhoon.kuto.de/](http://typhoon.kuto.de/)

just extract it anywhere, navigate to the files location and right click on typhoon to set permission for your username to be able to execute the game.  after the permission is set, double click on it like a exe file and it launches.  configuring the controls is needed or you will expirience slow mouse movement just like myself.  Also read the readme file for keyboard control of the game.(HIT ENTER ON THE KEYBOARD TO CONFIGURE IT)

added a pic

[IMG]http://typhoon.kuto.de/images/screen_t2k1_select.jpg[/IMG]

---

### Post by gOLdenHaWK3D on 2007-10-21
c00L. :D
Downloading...

Oops.. Downloaded! :P
Trying to play now. bRb
:popcorn:

---

### Post by negated on 2007-10-21
Hey,

Just wanted to report that contrary to the developers warning ("*OpenGL capable 3D-Accelerator card. Does not have to be on par with a GeForce 8800 but should be decent... not one of them onboard crap thingies*"), it works GREAT on my laptops 945GM integrated graphics...perfect!

Awesome game, great job!

-S

---

### Post by Cresho on 2007-10-21
This game is based on the atari jaguar tempest 2000.  The original author of the game gaved this guy permission to recreate it and it runs very nice.  I think this is the best arcade action for the ubuntu to date.  has the original techno music and added new voices along with the option to use the original from the tempest 2000.

---

### Post by DoktorSeven on 2007-10-21
Fairly nice, but there's not enough difference in the color of the enemies and their shots and the web/background (or not enough contrast, or something, making them blend in too well at times) like there was in the original, making the enemies and bullets VERY hard to see and therefore making it harder than it should be.  Even adjusting the background/web/etc settings doesn't help.

Original T2k did this well.

---

### Post by Cresho on 2007-10-21
> **DoktorSeven said:**
> Fairly nice, but there's not enough difference in the color of the enemies and their shots and the web/background (or not enough contrast, or something, making them blend in too well at times) like there was in the original, making the enemies and bullets VERY hard to see and therefore making it harder than it should be.  Even adjusting the background/web/etc settings doesn't help.

Original T2k did this well.

Actually, i been tweeking around the settings and there is.  have you tried going into the visual settings and...
reduce line width, dot scale, web alpha, web detail to simple, stars to simple, gradient "no"?  after that, you can increase it to your liking.  these settings make it look very similar to the original atari game on the jaguar.

---

### Post by DoktorSeven on 2007-10-21
Turning the starfield off helped bigtime.

There was one other thing I forgot to mention; the controls are too touchy.  Getting into a certain slot is very hit or miss, especially when you do it in a hurry.  The original had a sort of stick/go control scheme that made it easy to stop where you needed.

I'm not really saying this is bad -- it's a very good recreation of Tempest 2000 -- just pointing out areas that can be improved.  I think if the enemies stood out more against the default background settings and the feel of the controls were closer, it would be that much better.

---

### Post by octotom on 2007-10-21
Wow, that game is difficult!

---

### Post by Cresho on 2007-10-21
> **octotom said:**
> Wow, that game is difficult!

yes it is very difficult.  That is how arcade games are.  im trying out keyboard arrows vs the mouse.  There is also an option to tweek the mouse setting.

---

### Post by Cresho on 2007-10-22
here is my configuration for the game which totally towns down someof the blended graphics.

[display]
fixed_res = 1
xres = 1280
yres = 768
xvp = 1280
yvp = 768
zbuf = 24
cbuf = 32
aa = 1
accel = 1
fs = 1
weblines = 1
stars = 2
dotscale = 0.016405
linewidth = 0.916405
moving_camera = 1
rotating_camera = 0
flash = 1
gradient = 1
mipmap = 0
web_detail = 3
details = 1
pos_z = -6.000000
webalpha = 0.300000
glowalpha = 0.400000
fov = 60.000000
aspect = 1.000000

---

### Post by steveneddy on 2007-10-22
Sweet!

---

### Post by AJB2K3 on 2007-10-23
Um how do i run it?

---

### Post by DoktorSeven on 2007-10-23
extract it to a directory, make the file **typhoon** executable (via its properties in your file manager or **chmod +x typhoon** from the terminal) and run that file.

---

### Post by motin on 2007-10-28
It won't start... I guess Xgl is the problem - anyone encountered and solved this? Running Feisty...

---

### Post by Cresho on 2007-10-29
there are number of reasons why it does'nt work.

1. you have not configured your 3d accelerator in xserver-xorg
2. no driver installed
3. no restricted driver enabled
4. nvidia or ati?

anyway, you can open up a terminal and type glxgears.  it will show you a few gears spinning and this would tell you if you have something configured.  if it gets choppy, then you have a problem.

in any case, you can run the game without a graphics card.  after you run the game, typhoon.cfg is created after closing the game and is within the directory of where you extracted and ran the game.  in this file, edit it in text editor and change "accel=1" one to zero "accel=0"

your now running the game without an accelerator.

---

### Post by sylware on 2008-05-22
#=}**!
I buy a game pad as soon as I have a 64 bits build...

---

### Post by raydeen on 2008-06-01
Anyone else having trouble getting the sound to work? I'm running 8.04. Other than no sound, the game runs great. Brings back memories of Tempest X on my PS1.

---

### Post by GSZX1337 on 2008-06-02
Tempest 2000?

*rummages through Sega Saturn games*

*holding a Sega Saturn copy of Tempest 2000* This is a new game?

---

### Post by Perfect Storm on 2008-06-02
> **GSZX1337 said:**
> Tempest 2000?

*rummages through Sega Saturn games*

*holding a Sega Saturn copy of Tempest 2000* This is a new game?

[http://gaming.gwos.org/doku.php/games:alphabetical:t:typhoon2001?s=tempest](http://gaming.gwos.org/doku.php/games:alphabetical:t:typhoon2001?s=tempest)

---

### Post by GSZX1337 on 2008-06-02
> **Artificial Intelligence said:**
> [http://gaming.gwos.org/doku.php/games:alphabetical:t:typhoon2001?s=tempest](http://gaming.gwos.org/doku.php/games:alphabetical:t:typhoon2001?s=tempest)

Oh, okay, I understand now.

---

### Post by BryanFRitt on 2009-02-07
This game ran fine the first time I ran it from the command line.  It never runs/ran on double clicking the file in Konqueror, doing so would cause a black screen and no way to exit it without restarting X (default Ctrl+Alt+Backspace).  At one point the frame rate went down quite a bit, and then there was no sound even after deleting the typhoon_2001_r3992 directory, and re-extracting the file, and restarting my computer.  I tried it again after watching a Google Video to verify that my sound worked, and closing all possible windows(that's all I think I did) and the next time the sound, etc... worked!  Maybe all other windows need to be closed?

By the way, I think I read the author prefers you to link to the download page and not to the file itself.

[http://typhoon.kuto.de/download_mirrors.html](http://typhoon.kuto.de/download_mirrors.html)
---
update:
I tried running it using it's full path via the command line and that results in the same black screen requiring a restart of X. Guess it also requires being started from it's own directory.

---

### Post by Naiki Muliaina on 2009-02-08
Just given it a go, cant agree more with the folk above that have said this game is realy realy hard ^^

---

### Post by Xcursion666 on 2010-12-14
> **raydeen said:**
> Anyone else having trouble getting the sound to work? I'm running 8.04. Other than no sound, the game runs great. Brings back memories of Tempest X on my PS1.
i cant get the sound to work either

---


---
title: "anisotrpic filter, antialiasing, vblank sync, compiz"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Cresho on 2007-12-21
Hi all!

I must of spent the whole weekend figuring out why my switches did not activate during boot up.  Anyway,  I want to share what I discovered in getting these special nvidia features enabled for smooth, no jaggy edged cube, clean filter and no screen tearing at all  

First off, in the application under system->preferences->advanced desktop effects settings->General settings->Display settings  
Change the texture filter to "best", tick or untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" value string 1920x1200+0+0

Now for the nvidia settings.  go to system tools->nvidia x server settings. under "x server xvideo settings" tick "sync to vblank, under antialiasing, choose override application settings and start of low with like 2x bilinear. anisotropic filtering should override application setting as well and choose 2x, tick texture sharpening

now under
system->preferences->sessions add+

name: Nvidia
command: nvidia-settings --load-config-only
comment: Nvidia settings loader


create a file called .compiz.sh in your user directory and make sure you can view hidden files.  add this code

#!/bin/bash
sleep 5 && compiz;

save and now right click on the file and allow as executabeunder properties->permissions.(you might need to right click and allow show hidden file)

go to prefference->sessions

add a new entry as compiz and direct it to this file and save it.  should work when you boot up.

the last part should be set or this will not work.  In gutsy, the problem with compiz is that it is totally startup up before the sessions are activated rendering the antialiasing and anisotropic filter useless.  So that is why we added this session and this last final piece.  system->preferences->Appearance->visual effects.  set to none and never activate it here.  Wont cause any problems if you do but it will not activate the settings that will create a more pleasant compiz experience under Ubuntu.  REBOOT!  and every time you make a change, the settings will not take effect till you reboot.  The faster your pc, the higher you can set the settings and experience true artifact free desktop with no tearing, no jaggy edges, and no pixlelated images.



I would seriously like to see other people's setups....thanks!

my setup:

gutsy 32bit
amd 64x2 black edition 6400
2gb memory at ddr800
bfg 8800gt
HP 2408 (just because the viewing angle is better than the fhd2400 but not color wise)


update!  some problem can occur when running wine.  after closing a game such as my typhoon using a script

#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
cd /home/ranxerox/Installed_Programs/Typhoon_2001
./typhoon

#Compiz on;
compiz --replace &

and then tried running any wine applications, I would expirience bad refresh of the screen causing me to force log out ctrl+alt+backspace.  you can do two things here, try figure out what settings works.  test the options out in the antialiasing section (i had to use anisotrpic filter x2 and antialiasing x2 with texture sharpening to remove my problem).  THe other option was to disable all the settings in the antialisasing section, anisotropic, and texture sharpening.



updated wed 23, 2008


I noticed video tearing on some of my videos.  If you did the above, the only thing left to do is open nvidia-settings and under OpenGL Settings, tick sync to vblank and allow flipping.  and move image settings to high quality.  you will probably need a reboot

---

### Post by xgravix on 2007-12-24
thanks it works for me

it was a shame to waste all the anti-aliasing ability of the 8800!

---

### Post by Princegiri on 2007-12-27
Hai guys.... i had also created a thread along the same lines..... 
here is mine.... somehow i think i got about the anti-aliasing and stuff fixed for my COMPIZ

[http://ubuntuforums.org/showthread.php?t=650363](http://ubuntuforums.org/showthread.php?t=650363)

IM a complete noob taking my first few steps in ubuntu..... forgive me if the thread was useless and unncessary.... im just catering to the million other noobs that enter ubuntu everyday

**BTW im on Fiesty FAWN and most of things in the above instructions had to be adapted to use here.**

---

### Post by Cresho on 2007-12-27
> **Princegiri said:**
> Hai guys.... i had also created a thread along the same lines..... 
here is mine.... somehow i think i got about the anti-aliasing and stuff fixed for my COMPIZ

[http://ubuntuforums.org/showthread.php?t=650363](http://ubuntuforums.org/showthread.php?t=650363)

IM a complete noob taking my first few steps in ubuntu..... forgive me if the thread was useless and unncessary.... im just catering to the million other noobs that enter ubuntu everyday

**BTW im on Fiesty FAWN and most of things in the above instructions had to be adapted to use here.**

on that question about why you cannot change nvidia settings while compiz is running, you cannot unless you relog in or reboot.  BUt I added information on your thread on how to do this.  ill add it here too.

well, what you are really asking for is why you cannot change antialiasing configuration or anisotropic filter values while the 3D accelerator is engaged. YOU CAN'T! It's like trying to the settings on a video game while the game is running. what you need to do is shut down compiz and after the change re initialize it. Nvidia drivers (even in xp and vista) are not designed for 3d environment modification. It was set up for 2d desktops or you would actually see a change after you hit apply but apply applies if no 3d application is running or nvidia settings would be smart enough to shut it down and re initialize it.

WE ARE USING BLEEDING EDGE STUFF! and like bleeding edge stuff, you start using your brain unlike vista users.

sooo.......

you create 2 empty files on your desktop(right click on screen and.
"create document and empty file".
one says shutdown_compiz.sh and other says powerup_compiz.sh (if you looked at my last post about antiliasing, you can see a script I wrote for this purpouse for my video game typhoon powerups or shuts down. It disables and enables compiz) Now on each file, do this. right click and under properties->permmisions tick option execute allow file as program. do the same for the second file you created so both are now executable.

in shutdown_compiz.sh, add this following code. (edit with the text editor program and save it. right click and edit with text editor and save)

#!/bin/bash
killall compiz.real &
metacity --replace &




and in powerup_compiz.sh add this following code. (edit with the text editor program and save it. right click and edit with text editor and save)

#!/bin/bash
compiz --replace &

so from now on, before modifying nvidia, shutdown compiz and then modify and then power up compiz. when a pop up pops up and displays with questions, click on run.

you can have those two ugly files hanging around in a folder or something but why go there right? what I did was integrate these executables to my ubuntu desktop. I added them to my start menu and this is how.

open up your documents. aka file browser. go to view tab and click on "view hiddin files." now navigate to your desktop where you created the executables and add a period infront of these files. THEY NOW BECOME INVISIBLE. put these two files into your home directory under your username. This is where they will stay.

now open up main menu under preferences so you can add 2 entries.

highlight system tools and add 2 entries. compiz off direct it to the shutdown compiz sh in your user directory. If you cannot see invisible files in your location with the choosing application, just right click anywhere in the navigation window and click on view invisible files.do the same with compiz on and navigate that to powerup compiz sh. now you have those in your start menus under system tools.

---

### Post by Princegiri on 2007-12-30
I didnt see that you had replied to my post for two or three days... but now while looking for something i came back here...... 

thanks a lot cresho... you had taught a lot of things to me and in just ONE post.... 
i had to thank you twice, once in my thread and once in yours..... will try everything you posted about, and now i know where to go for help too.

---

### Post by Princegiri on 2007-12-30
your method worked perfectly for me once i really understood what i was doing... 

the script just makes compiz wait for 5 seconds before starting in which time nvidia loads... 

but the .compiz.sh file had to be modified to 

```
#!/bin/bash
sleep 5 && compiz --replace;
```

from ```
#!/bin/bash
sleep 5 && compiz;
```

for the whole thing to work for me....

---

### Post by []Milo on 2008-01-12
I'm not sure this is working for me.  i hadn't realised that there was a quality setting in Compiz and that was very useful to know and make a *huge* difference.  

I'm fairly sure tho that the changes I make to my NVidia settings are not having any impact.  I've done as you suggested and invoked compiz at start up with a delay but I think it still loads the nvidia setings after Compiz.  is there any way to force the load order of these things at start up?  Do we know for sure that Compiz won't just go ahead and ignore the nvidia settings anyway?   

Cresho, my setup's a bit older than yours:  

32bit Gutsy
X2 4800+ (65nm)
4G Corsair DDR2-800
Evga 8800GTS (640M)
shite old but big CRT :)

it would be nice to really use that 8800...

---

### Post by adamorjames on 2008-01-12
I'm on the last step and I don't see sessions-visual effects. "system->preferences->sessions-visual effects" is what you said but did you mean to make another arrow? Even if you did... I don't see visual effects either. "Help! I need somebody! Help! Not just anybody!", The Beatles. So, I'd appreciate it if someone could clarify for me the last step. Thanks.

my lappy:
 Gutsy 32 bit
 Intel Core 2 Duo 2.2GHz
 2 GB of memory at DDR2 667MHz
 NVIDIA 8600M GT
 Vostro 1500

EDIT: I figured it out. The last step is unchecking Visual. 
Imageshack scales the image down so click the image a second time to see the unaltered image.
[[IMG]http://img263.imageshack.us/img263/954/screenshotvp7.th.png[/IMG]](http://img263.imageshack.us/my.php?image=screenshotvp7.png)

---

### Post by Cresho on 2008-01-13
> **'[]Milo said:**
> I'm not sure this is working for me.  i hadn't realised that there was a quality setting in Compiz and that was very useful to know and make a *huge* difference.  

I'm fairly sure tho that the changes I make to my NVidia settings are not having any impact.  I've done as you suggested and invoked compiz at start up with a delay but I think it still loads the nvidia setings after Compiz.  is there any way to force the load order of these things at start up?  Do we know for sure that Compiz won't just go ahead and ignore the nvidia settings anyway?   

Cresho, my setup's a bit older than yours:  

32bit Gutsy
X2 4800+ (65nm)
4G Corsair DDR2-800
Evga 8800GTS (640M)
shite old but big CRT :)

it would be nice to really use that 8800...


I think I found out what I mistyped on my original post.  go to......
system->preferences->Appearance->visual effects. set to none and never activate it here.

Let me know if it helped.  ohhh by the way, any changes done to the nvidia settings will not take effect until after a log out and re log in when compiz is enabled.

here is a picture of my current desktop

[http://ubuntuforums.org/g/index.php?n=1969](http://ubuntuforums.org/g/index.php?n=1969)
[http://ubuntuforums.org/g/index.php?n=1880](http://ubuntuforums.org/g/index.php?n=1880)

---

### Post by Cresho on 2008-02-18
also posting a small update

here is one line.

Change the texture filter to "best", tick or untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" value string 1920x1200+0+0

and also make sure your nvidia has vsync enabled.

---


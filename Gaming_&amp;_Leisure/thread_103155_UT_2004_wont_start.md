---
title: "UT 2004 wont start"
date: 2005-12-13
forum: Gaming &amp; Leisure
---

### Post by madjinx on 2005-12-13
Im getting this message from command line:

WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


anyone?

---

### Post by Harleen on 2005-12-13
The game misses OpenGL support from your X-Server.
Do you have the display drivers from the manufacturer installed?

---

### Post by madjinx on 2005-12-13
[QUOTE=Harleen]The game misses OpenGL support from your X-Server.
Do you have the display drivers from the manufacturer installed?[/QUOTE]

had to double check, but yea. THe default ones that come in the repos, i use the old Ubuntu starter guide to get up and running:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)


as far as i know, this all still applies. I thought i remember something liek this happening, and i had to rename some file related to nvidias driver....

---

### Post by JimmyBEng on 2005-12-13
only a guess. but check your xorg.conf. look for the section like below.
```
Section "Module"
        Load    "xxxx"
        Load    "yyyy"
        Load    "glx"
        Load    "zzzz"
EndSection
```

is the Load "glx" line in there.

---

### Post by madjinx on 2005-12-14
[QUOTE=JimmyBEng]only a guess. but check your xorg.conf. look for the section like below.
```
Section "Module"
        Load    "xxxx"
        Load    "yyyy"
        Load    "glx"
        Load    "zzzz"
EndSection
```

is the Load "glx" line in there.[/QUOTE]

yea its there

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

i try glx gears though and get:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

wth am i missing?

---

### Post by BLTicklemonster on 2005-12-14
I had that same problem, so I did the hardcore nvidia driver install, and let me tell you, it's a totally different machine with the actual nvidia drivers.

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Be warned: 

PRINT OR COPY THIS PART (you still need to go to the link, the following is only a part of what you will be doing)

> ctl-alt-f1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd “directory where you have the nvidia installer”

CC=gcc-3.4

export CC

If you have Ubuntu 64bit type: 

sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run

NOTE: the name of the installer may vary:
e.g. it could be NVIDIA-Linux-x86_64-1.0-7667-pkg1.run.
So just put the name of the installer you've downloaded from Nvidia website

If you have Ubuntu 64bit you can't install OpenGL32bit compatibility libraries, so when the installer asks whether to install it just answer no OR you may want to try a workaround which Draugen found but which I haven't tried myself (look at the PROBLEMS SECTION at the end of the guide: point 5).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with “Modules” and comment out (by putting a "#" before the line) the 2 lines I put in blue and add Load "glx". It should look like the example below:


Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#Load "dri"
#Load “GLcore”
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"

Then find the section Device and make sure the word I put in red is “nvidia”:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

sudo /etc/init.d/gdm start (or "kdm start" if you use KDE)

Now you have installed the new nvidia driver.


That last part about editing the conf file, twice I've done this, and the info was already in the file, but check it anyway. 

Trust me, you will want that printed or copied on paper, because once you hit ctrl alt f1, and you don't have all that, you are going to be really pi$$ed off.

Good luck, have fun.

---

### Post by BLTicklemonster on 2005-12-14
By the way, I don't know if there's a cache cleaner for linux 2k4, so here's one you can make for yourself. First, go to synaptic and get Gawk installed, then open a text editor, and copy and paste the following:

```
#!/bin/bash
cd ~/.ut2004/Cache || exit 1 # change this to your ut2004 user dir
if [ -f cache.ini ] ; then
{
export ut2004dir="/home/bill/ut2004/" # change this to your main ut2004 folder
gawk -F= ' 
ut2004dir = "${ut2004dir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " ut2004dir targ $2 | "sh";
}
{
if(match($2,".ut2")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".ogg")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
else if(match($2,".usx")) moveit("StaticMeshes/");
else if(match($2,".ukx")) moveit("Animations/");
}
END { close("sh") }' cache.ini
#rm *.uxx cache.ini
}
fi;
# end script
```

Assuming you used the installer on the disk, of course.
Edit this line to reflect your own setup: 
```
export ut2004dir="/home/bill/ut2004/" # change this to your main ut2004 
```
that should be the only thing you need to alter if you used the installer that came with the game disks.

now save it as 2k4cleaner in /home/yourname/ and go to terminal, and 

```
chmod +x 2k4cleaner
```

This makes it executable.

Now when you want to clean your cache folder, you go to terminal, and type

```
./2k4cleaner
```

And it ought to work. "Ought" meaning that you jsut never know, do you?

Don't like the terminal, want an icon you can dbl click?

Right click desktop, click make launcher, name it 2K4 Cleaner or whatever you want. In command, put 

```
/home/yourname/2k4cleaner
```

and I check run in terminal, because I get a kick out of watching it do it's thing, lol. (I will double check that when I get home, but I'm pretty sure that's the correct command)

I think I have the pertinent extensions listed in that. If I missed any, you can add them easily enough using any line as a reference.


*IF any UT users want a cache cleaner for UT, let me know, it's a bit different from that. KUDOS GO TO ~V~ AT UNREALADMIN.ORG FOR THE INFO ON HOW TO DO THE CACHE CLEANER!!!!


(now one interesting thing about all this.... would it be that easy in windows? NO.)

---

### Post by madjinx on 2005-12-14
ive already tried installing nvidia's drivers from scratch, it never works out right.

Id like to know whats actually wrong.

---

### Post by tburns on 2005-12-14
[QUOTE=madjinx]ive already tried installing nvidia's drivers from scratch, it never works out right.

Id like to know whats actually wrong.[/QUOTE]


You can't install the driver with x running. 
You need gcc3.4 not gcc4.
Also when I did the install of a fresh AMD64 Breezy, I wasn't able to use the newest nvidia driver. I had to grab an archived version. The installer spit out something about versions etal. I can't remember exactly what.

---

### Post by tburns on 2005-12-14
[QUOTE=tburns]You can't install the driver with x running. 
You need gcc3.4 not gcc4.
Also when I did the install of a fresh AMD64 Breezy, I wasn't able to use the newest nvidia driver. I had to grab an archived version. The installer spit out something about versions etal. I can't remember exactly what.[/QUOTE]

This may not be the problem, but when I installed nvidia and then rebooted. My changes where lost due to an nvidia-glx init script. There is an archive posting here [http://ubuntuforums.org/archive/index.php/t-79039.html](http://ubuntuforums.org/archive/index.php/t-79039.html)

---

### Post by madjinx on 2005-12-14
ive noticed that in the guide it has:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"Driver "nvidia"
BusID "PCI:1:0:0"


well my xorg is missing the BusID line, ive got an nvidia 5700LE on AGP, what should it be?

---


---
title: "Help getting dolphin(Gamecube emulator) to work."
date: 2008-12-08
forum: Gaming &amp; Leisure
---

### Post by cloverz7 on 2008-12-08
First of all what revisions do you guys use and are you using the windows version underwine or the compiled linux version, I tried to do the linux one but it was missing the openGL plug which basically wasn't compiled due to GL and GLU? no idea what exactly that means

---

### Post by grossaffe on 2008-12-09
isn't tuxcube based off dolphin?  maybe give that a try. (though i don't know how to get the joystick working in that.)

---

### Post by hikaricore on 2008-12-09
Just a note, if you're actually trying to use an emulator to play gamecube games you're not going to have much luck.
Gamecube emulation still has a long way to go and you're likely to be thoroughly unimpressed with the framerates you get.

---

### Post by Sockerdrickan on 2008-12-09
> **hikaricore said:**
> Just a note, if you're actually trying to use an emulator to play gamecube games you're not going to have much luck.
Gamecube emulation still has a long way to go and you're likely to be thoroughly unimpressed with the framerates you get.
I get 24fps in Metroid Prime, minor graphical glitches. Sound and music works. :confused:

---

### Post by hikaricore on 2008-12-09
Yea with your setup you get 24fps.  :p
No telling what kinda specs the OP is working with.

To many people I've seen post around these parts, 24fps won't cut it.
I know gamecube emulation is improving, but thought I throw my 2 cents out there.

---

### Post by Sockerdrickan on 2008-12-09
Just remember 30 fps is consoles 60fps.

---

### Post by cloverz7 on 2008-12-09
I mean I'm pretty sure my set up will get fine fps...I have a 9800gx2 and my processor is pretty fast (Can't remember exactly the ghz) but its water cooled custom built

edit: Tuxor what rev are you using any tips on getting it set up, Are you running through wine or did you compile the linux version?

---

### Post by Lyon on 2008-12-10
Bump, I'm having the same problem, would really like to try the new release

When it is reading the Sconscript files:
> 
Checking for gl... (cached) yes
Checking for glu... (cached) no
Plugin_VideoOGL must have opengl (gl and glu) to be build


Have the very newest scons package. Tried reinstalling various libraries (libglu1-mesa libglu1-mesa-dev etc)

x86_64, Ubuntu 8.10 btw

---

### Post by Lyon on 2008-12-10
Nevermind, I've fixed the OpenGL problem (namely, I removed all the libraries and re-installed them, and all of a sudden it worked for some reason). Only remaining problems I seem to be having with it are:
[LIST]
[*]fullscreen presents nothing but a grey screen (need to force quit to get out)
[*]no sound (but that seems to be the case on any system, not just linux)
[*]graphics config dialogue does not open when I click it
[/LIST]

Also, tried playing with a 360 controller, but it looks like Intrepid has slipped some weird drivers in there since Hardy, and the controller is acting like a mouse, meaning I can't config it for the emulator. Kind of off topic, but are there different drivers that I have to get for that? Ubuntu documentation seems to be down/under-renos/who-knows-what atm.

---

### Post by pelao00 on 2009-01-05
> **Lyon said:**
> Nevermind, I've fixed the OpenGL problem (namely, I removed all the libraries and re-installed them, and all of a sudden it worked for some reason). Only remaining problems I seem to be having with it are:
[LIST]
[*]fullscreen presents nothing but a grey screen (need to force quit to get out)
[*]no sound (but that seems to be the case on any system, not just linux)
[*]graphics config dialogue does not open when I click it
[/LIST]

Also, tried playing with a 360 controller, but it looks like Intrepid has slipped some weird drivers in there since Hardy, and the controller is acting like a mouse, meaning I can't config it for the emulator. Kind of off topic, but are there different drivers that I have to get for that? Ubuntu documentation seems to be down/under-renos/who-knows-what atm.

a while ago i installed epsxe on ubuntu 8.04 LTS and couldn't select the configure option (nothing happened, the configure window did not pop out).  to solve the problem i gave 0777 permission to the folder and sub folders and files were i had the emulator. 

try 

sudo chmod 0777 /usr/local/games/dolphin/*/*

note: my path is "/usr/local/games/dolphin/", replace yours with whatever you have to replace and the "/*/*" is to give every folder and file permission 0777 so it won't bother you with any kind of permission problems.

giving the right permissions to the folder and files will allow the emulator to make the required changes and save them.
IMPORTANT: check for the lock symbol on the configuration files.  if it has the lock, give 0777 permission to the file.

Also if that doesn't help i remember with another emulator i had to create an empty configuration file corrsponding to the plug in, either because it was missing or it was corrupt (in my case i think a file called cfgPeops-something- or Peops-something-.cfg was missing so i created a blank file with that name).  try any of this and see if you can solve the configuration problems.  i will try to install dolphin soon and try to make it run.  

For the 360 controller problem try installing the latest joystick/gamepad drivers for ubuntu if u haven't.  [[here]("http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/")] i leave a tutorial i found to install the drivers.


How to install XBox 360 controller [[tutorial]("https://help.ubuntu.com/community/Xbox360Controller")]

---


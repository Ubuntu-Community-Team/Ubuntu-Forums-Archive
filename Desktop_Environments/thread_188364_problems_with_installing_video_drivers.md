---
title: "problems with installing video drivers"
date: 2006-06-04
forum: Desktop Environments
---

### Post by tehubersheezy on 2006-06-04
so every time i try to install video drivers for my 6800GT, even with 5.05, after i reset i can hear that it went to the start up screen, my computer didn't freeze but there's nothing on the screen
here's the directions i followed:
      Nvidia cards: Open Synaptic and search for and install nvidia-glx. When installation has finished, open a shell window and type sudo nvidia-xconfig. Then reboot.
      Test your new 3D configuration, after reboot, by selecting one of the OpenGL screensavers (System -> Preferences -> Screensavers). AntSpotlight is pretty cool. If it runs smoothly then everything has worked. 

please help!

---

### Post by croak77 on 2006-06-04
Did you follow the wiki?

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Does X start? Do you see the Nvidia splash screen?

---

### Post by tehubersheezy on 2006-06-05
if splash screen is the login part, it doesn't show that, i dunno what X is
how do i go about restoring the default video drivers?

---

### Post by pellgarlic on 2006-06-06
"x" is what controls what displays the graphics on your monitor. without x, the computer cannot draw graphics, only print text.

to restore the default video drivers, you need to get to a terminal prompt. boot your computer as normal. when you get to the point that you "can hear that it went to the start up screen", press ctrl-alt-backspace - this kills x (this just means that it stops trying to display the "picturesque" graphics, and just shows text). 

you should now be looking at a black screen with white writing. it should say "login:" so type your login name, then press enter. it will ask for your password - enter your password and press enter. it should now say something like: "user@ubuntu:/user" (where "user" is substituted for your own user name). 

now, type this (entering password whenever it asks for it):

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf

this will create a backup copy of the xorg.conf file, then open it in the "nano" text editor. use the cursor keys to move the cursor down a couple of screens, until you see a section called "device", and look for the line that says "driver = nvidia", and change "nvidia" to say "nv". (use the cursor keys to position the cursor, and then backspace, and type as in any text editor). next, press ctrl-x, press "y" then enter to save, and press enter again to accept overwriting xorg.conf.

now type startx and press enter, and you should be back to the ubuntu desktop.

it's strange that installing the nvidia-glx drivers should cause this problem to happen - they should be pretty widely compatible. perhaps if you're feeling adventurous, you could try compiling and installing the 8756 drivers from nvidia's website? :)

---


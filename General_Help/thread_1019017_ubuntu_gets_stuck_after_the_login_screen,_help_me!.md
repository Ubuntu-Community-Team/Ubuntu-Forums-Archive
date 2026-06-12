---
title: "ubuntu gets stuck after the login screen, help me!"
date: 2008-12-22
forum: General Help
---

### Post by rockstar686 on 2008-12-22
im trying to install ubuntu 8.10 on my older dell laptop inspiron 1200, celeron m processer 1.40 ghz 256 megs ram 40gig hardrive and intel 915gm/910gml graphics i have a live cd that i orderd from ubuntu the cd loads fine all the way through the page that tell me to select my language and boot wihout any changes to your computer ect.. then it takes me to the log in screen and outomatically logs me in after like 20sec then the screens goes a peach/tan/white color and then goes black and doesent actually load anything? ive never used ubuntu or linix so i dont know how to fix the problem, any ideas

---

### Post by rockstar686 on 2008-12-22
if i go to the install button insted of clicking on boot without makin changes it goes through everything and brings up the install menu but the whole menu is white and while i have a cruser it wont let me type ( not that theres actually any fields to type in anyways )

---

### Post by kpalanikannan on 2009-04-18
Hi,

up to my knowledge, There are two reasons which causes the problem.

1. Not enough disk space. Check your disk space with "$df -h" command.
Clear the all files in /tmp folder with "$cd /tmp , $rm -rf *" commands.
Try to login now. If this is not your problem then try the next solution.

2. The Graphics card resolution value set to high value but it is not supported by your monitor.

you can solve this issue by editing the Display settings file manually.

The Display setting file is "/etc/X11/xorg.conf". If the file does not exist edit "/etc/X11/XF86Config" file.

Example Screen section below. In the section change the hi lighted Modes line only shown below.

Section "Screen"
   Driver      "vga2"
   Device      "Generic VGA"
   Monitor     "COMPAQ 5500"
   Subsection "Display"
       Modes       "800x600"
       ViewPort    0 0
   EndSubsection
EndSection

If you log in to the system after changing the line. The resolution will be low.

If this is not solving your problem.

Just copy and paste the below lines at the end of the 'xorg.conf' file. Then try to log in.

**********************************************************************

# The Colour SVGA server

Section "Screen"
   Driver      "svga"
   Device      "Generic VGA"
   #Device      "Intel 830"
   Monitor     "COMPAQ 5500"
   Subsection "Display"
       Depth       8
       #Modes       (null)
       ViewPort    0 0
   EndSubsection
EndSection

# The 16-color VGA server

Section "Screen"
   Driver      "vga16"
   Device      "Generic VGA"
   Monitor     "COMPAQ 5500"
   Subsection "Display"
         Modes       "640x480" "800x600"
         ViewPort    0 0
   EndSubsection
EndSection

# The Mono server

Section "Screen"
   Driver      "vga2"
   Device      "Generic VGA"
   Monitor     "COMPAQ 5500"
   Subsection "Display"
       Modes       "640x480" "800x600"
       ViewPort    0 0
   EndSubsection
EndSection

---


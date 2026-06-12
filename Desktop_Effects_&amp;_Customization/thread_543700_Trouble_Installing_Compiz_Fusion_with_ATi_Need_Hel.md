---
title: "Trouble Installing Compiz Fusion with ATi Need Help"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by Almas on 2007-09-05
Hi, I have like many others made the switch to Linux and I'm having some growing pains, for the past couple of days I've been trying to get this Compiz to work reformatting and trying again with numerous guides and no matter what I can't seem to get it working.

So far I have been able to install Compiz start it up and get to the point where I start with the XGL session and load compiz.  The problem is when I move any window Ubuntu freezes and the frame rate of the OS is VERY choppy I know it's trying to work because when I go to switch the "cube" I see the cube rotate but then it cuts back to the OS and freezes.  I checked the status of my OpenGL acceleration and it says that direct render is off, another problem is when I attempt to fix this issue I did what many guides tell to which is go into the xorg.conf file and add 3 lines to the bottom to disable composition, though after doing this and restarting when I log in Ubuntu loads with graphical errors, the only thing on the screen I can make out if the cursor everything else looks a jumble of crap meaning that the OS could not properly render I'm guessing.  I know I don't have a lot of technical information to help you guys help me so if someone could give me some terminal commands to get some more information for my thread that would be great I know I'm somewhere near getting this working I just need to figure out how to enable direct rendering I'm thinking.  thanks for the help.

So far:  
Installed ATi Prop drivers via Envy
Installed Xorg-Server
Using XGL Session
Used the Ubuntu guide to installing gnome-compiz manager
Computer freezes when any effects are activated ie ( Moving windows, turning the Cube)
Updated the xorg.conf file with :

Section "Extensions"
Option "Composite" "0"
EndSection

After adding those lines I get a completely messed up Ubuntu screen now only thing that looks normal is the cursor
Almas

---

### Post by kellemes on 2007-09-06
Please post /etc/X11/xorg.conf and /var/log/Xorg.0.log (within [CODE]-tags)

---

### Post by jazz452 on 2007-09-07
type  "fglrxinfo" in terminal you should get 

j@j-desktop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6) 

im using older driver for ati in gutsy gibbon (ubuntu)
if you get mesa 3d try reinstalling driver
whenever i used envy in feisty with ati had to install twice to make it work.

---


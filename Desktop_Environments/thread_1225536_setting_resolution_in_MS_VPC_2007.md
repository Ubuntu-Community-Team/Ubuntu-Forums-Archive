---
title: "setting resolution in MS VPC 2007"
date: 2009-07-28
forum: Desktop Environments
---

### Post by minah17 on 2009-07-28
Having problems setting up my resolution. I am using Windows Virtual PC 2007 and 've messed with xorg.conf enough times now without any success... I am trying to set my resolution to 1280x1024. I normally would change the depth in the xorg.conf to 32 and reboot. I get a configure video dialog with default selection set to "Plug n play" and 800x600 resolution. I then proceed to choose "Generic Monitor" with resolution 1280x1024 instead and then press test button. The first time I always get a black screen (with this setup) but when I test it again it gives me black boxes with gray background and I accept the setting. When I reach the login screen i see 
 
[please view attached login.jpg---
edit: just viewed the jpg files attached here the login.jpg should be much larger than the logged.jpg. Unfortunately lost that here... as a matter of fact the virtual pc window shrinks as i login and then I see the messed up screen...is there some session specific setting that I need to adjust?
]
 
However when I login I see....
 
[please view attached logged.jpg]
 
 
Any help would be greatly appreciated....

---

### Post by minah17 on 2009-07-29
Anyone?  may be a trick that may have worked with others before...or some file name that sets stuff when one logs in?  I've already checked .profile file.

---

### Post by rannable on 2009-07-29
hey is your installation 32 or 64? 
also is vpc installed through wine or do you have ubuntu as the guest os through it?

i would be tempted to try using virtualbox or paying for VMware instead, microsoft vpc is well known for having problems with linux vm's: [http://coolthingoftheday.blogspot.com/2006/06/virtual-pc-2004-ubuntu-and-video.html](http://coolthingoftheday.blogspot.com/2006/06/virtual-pc-2004-ubuntu-and-video.html) and also [http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)

---

### Post by minah17 on 2009-07-29
[COLOR=black][FONT=Verdana]thanx for the reply...32 and guest!  Not sure what wine is as a matter of fact...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I've been trying to get different video card drivers to work lately with no success, I installed xorg-driver-fglrx and ran aticonfig but it returned unable to detect video adaptor type error.  I have an Ati adaptor. Is it possible I am doing something wrong here i.e. I need the right adaptor installed or something?  Trying to avoid switching VPCs at this point as I've invested some time already in this setup...would like to hope that that would be the last resort...[/FONT][/COLOR]

---

### Post by minah17 on 2009-07-29
Some progress finally, not exactly what I was looking for but nonetheless.  **Before I go on does anyone know if I could achieve 32bit depth? ** Here's what I did
 
From login screen selected Options->Select Session... 
chose Failsafe Terminal and logged in.  
After clicking through the dialog box entered the following command on the cmd-line:
gnome-control-center
 
Looked for, I think it was, "Set resolution" other versions of ubuntu may have "Display" instead... 
 
here it listed resolutions that I did not have in my xorg.conf file.  For e.g. [EMAIL="1152x768@60"]1152x768@60[/EMAIL].  Not exactly what I was looking for but nonetheless better than 800x600.  I selected it and pressed Apply.  The display looked good so I pressed "keep the change" on the dialog box that appeared.
 
Since I did not have this resolution in the xorg.conf file I added a "modeline" for it (used cvt command to get the info for the resolution, one may also look into /var/log/Xorg.0.log if need be) and placed this resolution as the first entry in the "Mode" list.
 
Ctrl+Alt+Backspace to restart X.
 
Logged back in and this time the window did not shrink and I had 1152x768 resolution.  
 
I dont know why the Fail safe session was needed or why these unique and limited list of resolutions were listed here, some of which were not even in my xorg.conf file (so where are they coming from?).  What's more is that I have recofigured my display and this time I automagically get a resolution of 1152x768 and the desired resolution 1280x1024, first in the list is readily ignored???!!!  If anyone has any suggestion please do let me know.  
 
here are couple of helpful links:
[http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/](http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/)
 
[https://wiki.ubuntu.com/X/Config/Resolution#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do](https://wiki.ubuntu.com/X/Config/Resolution#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do)

---


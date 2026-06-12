---
title: "Resolution problem"
date: 2005-08-17
forum: Desktop Environments
---

### Post by masterkale on 2005-08-17
Hello, I have read other threads on how to change the resolution in ubuntu. My problem is that it is running at 800x600 when it should be at 1280x1024. And it on the monitor it says refresh rate to low. and it bumps it up to 60. I have tried editing the /etc/X11/xorg.conf but I am not allowed to save the file. From what I have read there is no root in ubnuntu(I am actually running kubuntu) and you have do Sudo root? I am on a dell  and it has the entergrate extreme graphics 2 card I beieve. If you need any more info to help just ask, I am really eager to get this problem solved to see if I want to keep running kubuntu. Thank you for your help.

---

### Post by Martin Witte on 2005-08-17
If you want to edit a file for which you need root permissions do sudo emacs  /etc/X11/xorg.conf, thewn enter the root password; 'sudo' gives all sudo users root rights.

---

### Post by tseliot on 2005-08-17
Ok, type:

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the lines with the resolution and add (or substitute) the resolution you need. For example:

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

For example put "1280x1024" instead of the word in red.

Then find the lines with the refresh rate and change the values.

Once you've modifed the file (you can only use the keyboard in this case), press

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

Tell me if it works

---

### Post by Ptero-4 on 2005-08-17
[QUOTE=Martin Witte]If you want to edit a file for which you need root permissions do sudo emacs  /etc/X11/xorg.conf, thewn enter the root password; 'sudo' gives all sudo users root rights.[/QUOTE]
 Actually type sudo pico /etc/X11/xorg.conf (emacs and pico are text editors but emacs is cumbersome and complex, pico is more userfriendly).

---

### Post by masterkale on 2005-08-17
Hey, I edited the file, so that the only resolution in  the files is 1280x1024, which is my monitor max res. Still starts in 800x600. Should I add anything to the file? like under the section labled manitor? I still get the out of frequency message on the monitor, too. Are there any intel drivers I should download? That you for your quick replies, and help.  

Edit:
And yes the second method posted did work.

---

### Post by masterkale on 2005-08-17
I figured that damn thing out. I changed the driver form i810 to vesa. Now it looks all pretty. Thank you guys so much for all your help, I couldn't have done it without you. Or google, lol.

---


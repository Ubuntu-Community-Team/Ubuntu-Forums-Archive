---
title: "cannot open files on /media"
date: 2020-01-12
forum: Desktop Environments
---

### Post by darkthuban on 2020-01-12
while old version of some applications (i. e ProjectLibre or SweetHome3D) were able to open files on internal flashdrive (the drive is on the /media like an external usb drive) wer able to see subfolders and file, new versions are not. They can se files only from the main drive where the operative system is installed. I have all my files on /media/internal_flash_drive. 
I have Ubuntu 18.04, cannot find any hints anywere. 
Many thanks

---

### Post by CelticWarrior on 2020-01-12
You installed snap versions and there's currently a limitation.

---

### Post by darkthuban on 2020-01-12
many thanks so for sweethome3d i have solved the issue with [FONT=Helvetica]**snap connect sweethome3d-homedesign:removable-media**, but don't understand how to solve it with projectlibre as the snap with projectlibre gives the following

[/FONT]snap connect projectlibre:removable-media (enetered command)
error: snap "projectlibre" has no plug named "removable-media" (error I have got back)

---

### Post by darkthuban on 2020-01-12
unistall projectlibre

install project libre as per the below snap, and after I am able to see the files on the /media. Issue solved

[COLOR=#333333][FONT=&amp]snap install [/FONT][/COLOR]projectlibre[COLOR=#333333][FONT=&amp] --edge [COLOR=#00BF00]--devmode

[/COLOR]
[/FONT][/COLOR]

---


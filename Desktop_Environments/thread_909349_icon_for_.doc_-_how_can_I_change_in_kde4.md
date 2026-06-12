---
title: "icon for *.doc - how can I change in kde4?"
date: 2008-09-03
forum: Desktop Environments
---

### Post by maestrobwh1 on 2008-09-03
Okay, so it has been a while since I tried to fix this.  The *.doc extension for kde4 still shows a "?" while the other openoffice counterparts, *.ppt and *.xls show the proper icon.  Right clicking in dolphin/konqueror pulls up the properties and one can change the program that opens the extension, but one cannot change the icon that represents the file type.  

I searched for 45 min on google for a variety of "change *.doc icon kde4" and any other combination of words and I find people posting the issue, but no solution.

Is there one, even if it means I have to edit a file somewhere in the system?

---

### Post by sayakb on 2008-09-03
Assuming that you use the oxygen theme, goto /usr/lib/kde4/share/icons/oxygen/<size>/mimetypes and change the icon from there. You need to launch dolphin/konqueror as root to be able to write to the folder.

---

### Post by maestrobwh1 on 2008-09-03
That just makes an icon different.  The issue is that the *.doc extension does not get an icon assigned and there seems to be no way to have one assigned, so it doesn't really matter what I put in the folder... all of the other MS documents get assigned the appropriate OpenOffice icon automatically because it is the preferred program to open each file type.  Somehow this gets skipped for the doc extension.

Looking in the folder, I cannot determine how to get one of those images to assign itself to an extension... config file somewhere?

---

### Post by Splondike on 2008-10-09
Same problem with KDE4 in Archlinux, I managed to solve it however:
[LIST=1]
[*]Open a terminal, log in as root and navigate to the oxygen directory (*cd /usr/share/icons/oxygen*).
[*]Enter the 'scalable' directory and make a symmlink from application-vnd.ms-word.svgz to application-msword.svgz (*ln -s application-vnd.ms-word.svgz application-msword.svgz*).
[*]Change back to the oxygen directory and repeat step 2 for each sise (128x128, 64x64 etc.); symlink application-vnd.ms-word.png to application-msword.png in each case.
[*]Still as root enter the command: *touch -m /usr/share/icons/hicolor*.
[*]Within a few seconds your icon should show up.
[/LIST]

The reason as noted above is that the /usr/share/mime directory uses (incorrectly I believe) application/msword rather than application/vnd.ms-word for *.doc files. The touch command causes kde4 to rebuild its icon cache, which is why the OP wasn't seeing the change.

---

### Post by ungethym on 2008-10-19
Thanks for the tip, Splondike! 

For kubuntu 8.04 the paths are the following:

1. cd /usr/lib/kde4/share/icons/oxygen
2+3 ...
4. sudo touch -m /usr/lib/kde4/share/icons/default.kde4

---

### Post by paillon_libre on 2008-12-07
Also thanks for the tips, Splondike and Ungethym! 

This is for Kunbuntu 8.10 (small changes, same bug): 

paths are: 
*/usr/share/icons/oxygen/nxn/mimetype*
(with 16 < n < 128 ) 

links are now like: 
*sudo ln -s application-vnd.ms-word.png application-msword.png*

then: *sudo touch -m /usr/share/icons/default.kde4*
and it seems magic to me ...

---


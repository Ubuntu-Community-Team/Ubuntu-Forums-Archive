---
title: "Downloads go to wrong folder, only show in Nautilus"
date: 2013-09-23
forum: Desktop Environments
---

### Post by Luxx on 2013-09-23
I'm assuming this a DE/file manager issue and hope I'm posting it the right place. If not, please move to the correct forum.

1.) Does anyone know why downloads would suddenly start going directly to the home folder instead of the folder they are directed to?
AND
2.) why they would ONLY show up in the home folder in Nautilus -- after installing Nautilus when nothing else seemed to be working????


I downloaded a couple of .iso files and a couple of USB creator files, the first .iso went to the desktop as directed, then a USB creator package. Less than an hour later, without making any changes, the other files downloaded and seemingly disappeared. I tried downloading them to Downloads and then to Desktop and they just never showed up. I tried searching for them but nemo, muffin and emelFM2 did not seem to see them.

I found them clearly displayed in the Home folder after installing and running Nautilus from terminal. Any clues? 
Should I file a bug report... and if so, under which dev project?

It may be relevant that I'm using Ubuntu 13.04 x64 with the gnome-session-fallback DE.

Additional info:
I tried to move the files to the desktop and nautilus crashed. I tried changing permissions in nautilus and nautilus crashed. Permission changes seemed to stick, however I still cannot move the files to the Desktop because permission is denied. I can move them into the Desktop IN nautilus, but they can still ONLY be seen IN nautilus.
After a reboot this is still the case with newly downloaded files. I can't actually download and USE anything. 

I may have downloaded a bad file. I downloaded Live-USB-creator. I have checked the bug reports in Launchpad and verified the download source is the same url listed there, so I didn't think it would be something that could cause this, but maybe...

When I downloaded it to the desktop and double-clicked it, Software Center opened as expected and it installed, but with the warning below. After it installed it appeared in Software Center as an installed program with the option to reinstall rather than uninstall and showed up in the Applications/System Tools menu, but could not be found again in Software Center later.

> The package is of bad quality
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organization who provided this package file and include the details beneath.

Details
Lintian check results for live-usb-install[something]
E: live-usb-install[something]: control-file-has-bad-permissions postinst 0775 != 0755

I just ignored it as I usually do. I didn't use dpgk -i or gdebi.



The error says the file permissions are bad. That might explain the screwed up file permissions, but would that make the file invisible, and then cause further downloaded files to also be invisible?
The folder for the installed program is in usr/share.


(**Tag dropdown menu offers suggestions that are over 18 characters, but a post can't be submitted with tags that long.)

---

### Post by Luxx on 2013-09-24
Additional info, see edit above.

I don't know enough to determine if this is really a DE or file manager issue, or if the downloaded program caused my computer to behave strangely or if something else happened.
It seems perhaps a bug report should be filed, but I still have no idea where the issue actually is, or how to get downloads from here on out to show up normally.

---


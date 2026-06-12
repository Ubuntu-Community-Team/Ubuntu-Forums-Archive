---
title: "Warcraft 3 Issues (wine)"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by TchaTcha on 2006-08-27
Hello folks, i am a new linux user... i have been hooping from distro to distro to find the home one to become a user! Did Gentoo, Kurumin and Ubuntu now.
Everything is great since is like Kurumin with more apt-get control.

Now that i am doing ok with linux and its configurations and programs i want to take the next step forward, or should i say give the big over canyon jump... start to play games on linux!!!

I did read i think some 4 tutorials, even here in ubuntu forum, about installing War3 on linux, and infinite troubleshooting topics... all seem so simple but none works for me =(. This topic seems old but if anyone care about a noob =).

I installed wine from CVS, compiled, installed... did winetools, got IE6 all the nescessary windows programs. Did winecfg clicking on autodetect devices.
Portaged xlibmesa-x11, x11proto-dev, freeglut, and so many others.

Now i have War3 installed on the pc... 2 things happens... when i start the game, he asks me for the CD and say that couldnt find opengl32.dll.
1) I tried getting a no-cd patch from the many ones in the website that  winehq told... tried almost all patches, but none worked. It still asks for the cd.
2) I recompiled wine with -enable-opengl many times now and still he cant find opengl32.dll!
Edit 1: I run the game wine Warcraft\ 3.exe -opengl. Just for the info 2 =).

Big post for 2 problems =). Any help?

Thanks

---

### Post by YetiHunter on 2006-08-27
Hi!
Well I'm a linux newbee, too. ;) 
Try to get a no-cd crack from [www.megagames.com](www.megagames.com) and you can get the dll file from [www.dll-files.com](www.dll-files.com). Then copy the dll file in your .wine/drive_c/windows/ directory.

---


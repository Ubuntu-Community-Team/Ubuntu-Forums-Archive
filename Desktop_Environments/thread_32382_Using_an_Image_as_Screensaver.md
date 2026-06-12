---
title: "Using an Image as Screensaver"
date: 2005-05-07
forum: Desktop Environments
---

### Post by #Vizc@ch@ on 2005-05-07
Hi, I'm trying to figure out how to use an image as a screensaver. I tried copying the image to /usr/share/man/man6, which is the folder where all the default system screensavers are, but it didn't work. Then I noticed that the extension of those files (the screensavers ones) had a 6x.gz extension, for example: GLmatrix.6x.gz would be the file that corresponds to the screensaver named GLmatrix.

So the idea is to use a non animated image.. like a gif (which is the one i'm trying to use... or a jpg, or whatever)

Ok, hope someone can help me out with this. Thanks.
Bye  :)

---

### Post by crmanski on 2005-05-07
I use the GLSlideshow screensaver to display a directory of images.
To do this...

1. Open System-> Preferences -> Screensaver
2. Choose Only One Screen Saver from the drop down and then select GLSlideshow.
3. Click on Advanced tab and check off "choose an random image" and specify a directory that has the images.

---

### Post by Firetech on 2005-05-07
1. This forum is for finished howto's (E.G. People who have the solution from the first post), not for questions, This post belongs in the "Application support forum"
2. The /usr/share/man/* directories are NOT where screensavers are found, it's the manpage database, containing manuals for all (or most) of your installed software. You use it by typing "man [manual-name-here]" in a terminal window.
3. Why use a static image as a sceensaver? a screensaver is made to give the screen some "relief" my changing the image frequently (to avoid the image burning stuck on the screen, which only affects CRT screens)

---

### Post by McQuaid on 2005-05-07
Actually pretty much all modern crts do not suffer from 'screen burn' so screen savers are nowadays just for fun.  So if you want to use a static personal picture have fun.  But ya this is for completed how to's not inquires on how to accomplish something.

---

### Post by mrbass on 2005-05-07
Well that GLSlideshow it says go to ADVANCED tab ...I do but it has no remote directory option.  Maybe I'll have to end up using chbg

Anyway I spent a couple hours today going through all OPENGL screensavers and here are my favorite ones:

BlockTube
Endgame
Eurphoria
Flocks
Flurry
GLKnots
GLText(clock)
Helios
HyperTorus
JigglyPuff
Lattice
Molecule
Polyhedra

btw, flurry is a port of flurry on mac os x....doesn't quite compare.  Flurry is by far my favorite mac os x screensaver.

---

### Post by #Vizc@ch@ on 2005-05-07
Hi everyone, thanks for the answers.
First of all i'm sorry i posted in the wrong place .. i was kind of in a hurry and didn't realize.
The GLslideshow thing didn't worked.
And i correct myself, the path to the screensavers file is /usr/share/xscreensaver and all the files are with a .xml extension... any idea about this?

Although i didn't know about the utility of screensavers, i had heard something, but anyway I wanted it for fun, because the .gif image I want as a screensaver is a Windows Blue Screen of Death  :grin: 

Byte, thanks

---

### Post by mrbass on 2005-05-08
well you can always 
sudo apt-get install chbg
I wrote all the descriptions for the effects.  It can use directory of images for a screensaver.  Also can generate random fractals.  Here's some fractals I generated with chbg [http://mrbass.org/fractals](http://mrbass.org/fractals)

---

### Post by fakie_flip on 2007-07-07
Is there any way to get this really awesome screensaver working in Ubuntu? If so, please let me know how you did it.

[http://www.microsoft.com/technet/sysinternals/Miscellaneous/BlueScreen.mspx](http://www.microsoft.com/technet/sysinternals/Miscellaneous/BlueScreen.mspx)

---

### Post by fjgaude on 2007-07-07
> **#Vizc@ch@ said:**
> Hi everyone, thanks for the answers.
First of all i'm sorry i posted in the wrong place .. i was kind of in a hurry and didn't realize.
The GLslideshow thing didn't worked.
And i correct myself, the path to the screensavers file is /usr/share/xscreensaver and all the files are with a .xml extension... any idea about this?

Although i didn't know about the utility of screensavers, i had heard something, but anyway I wanted it for fun, because the .gif image I want as a screensaver is a Windows Blue Screen of Death  :grin: 

Byte, thanks

All you have to do to get a screensaver is to use File Browser, click on the image, the image viewer shows the image, and at the bottom of the Image menu, Set as Wallpaper. That's it. Now when you right click desktop background and click Change Desktop Background you will see the new image and the rest that are as defaults.

frank

---


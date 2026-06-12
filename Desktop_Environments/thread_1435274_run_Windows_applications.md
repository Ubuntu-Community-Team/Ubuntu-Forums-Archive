---
title: "run Windows applications"
date: 2010-03-21
forum: Desktop Environments
---

### Post by chuchi on 2010-03-21
Hello to all!! I'm doing a course and I had to install an application which run in Windows. I've probed to use "wine", but when I use "wine application" it failed. I can't use the Virtual box because I've lost my Windows CD installation. Does anybody know another way to run Windows applications in Ubuntu??
Many thanks!!

---

### Post by lazerradial2003 on 2010-03-21
Worth persevering a bit with Wine, lots of things don't run out of the box (although many do) but will with a bit of tweaking. Are you using the latest version of Wine from their site or the version in the Repos?

---

### Post by chuchi on 2010-03-21
I'm using the one of the repository. Do you think that installing the one from de web site I can have better results?? I'll uninstalling wine and reinstalling it from de web site. I'll tell you the results. Many thanks!!

---

### Post by Jakey_TheSnake on 2010-03-21
Which piece of windows software are you installing? You could try Crossover Office, it's like Wine but has some dependencies built in by default. 

Download: [http://www.fileden.com/files/2007/5/20/1096740/crossover.sh](http://www.fileden.com/files/2007/5/20/1096740/crossover.sh)

To install, put this file on your desktop. Then open up a terminal, and type the following: 

```
cd ~/Desktop/
sudo sh crossover.sh
``` 

Type in your password. Note: no characters will appear. Then configure and install your software.

---

### Post by chuchi on 2010-03-21
Hello!! I downloaded the least version of wine, but I got the same error, i got a window "Application Error". I'm going to try with CrossOver office, and I'll tell you the results. Many thanks to all!!!

---

### Post by Enigmapond on 2010-03-21
It would also help greatly if you included in your OP exactly what software you are trying to install as it may not be compatible or there may be a better Linux programme for the same thing.

---

### Post by chuchi on 2010-03-21
I need to run a program for my course which is for Windows. Cross Over only allow run particular applications (Office programs and other  Adobes). Many thanks anyway!!

---

### Post by chuchi on 2010-03-21
I'm doing a course of English (my English is poor clearly xD). The software is the CD of face2face. Enigmapond, what do you mean with "my OP"?? Sorry, but I don't understand a lot of english. Many thanks

---

### Post by Enigmapond on 2010-03-21
OP = Opening Post and if this is Face2Face webcam, you may want to have a look at this thread.

Good Luck...
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by chuchi on 2010-03-21
I'm sorry Enigmapond!!! xD xD!! Due to my poor english i didn't explain well!! "Face2Face" is the name of the CD for the Course of english I am doing. I had to install this CD in Windows for installing the program and it is installed in "Program Files". But I hate Windows, and I want to run this program in Ubuntu.
Many thanks and sorry!!

---

### Post by VernonA on 2010-03-22
Are you talking about the Cambridge University Press English course? If so, have you actually checked if the CD can be used from Ubuntu? There is a fair chance that the important resources on the disk can be read with a browser and/or a PDF viewer, and that the Windows app is just a fancy GUI for presenting them. Try navigating onto the CD and see how much of it is in HTML/DOC/PDF etc.

Also if you want a free implementation of Windows to run under VirtualBox have you looked at [ReactOS]("http://www.reactos.org/en/index.html")? It still needs some work, but it might be enough to get you going.

---


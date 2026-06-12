---
title: "Doom 3 demo installation help"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by umdzig on 2005-08-01
I have downloaded the doom 3 demo and i have it saved to my desktop. However, i cannot figure out how to install the dang thing. Double clicking it wont work it just brings up a text editor. Can someone give me a step by step instructions on installing it? I apoligize for my noobiness. Should the download be a tar or installer of some sort because all i have is a file with the extension .run. (doom3-linux-1.1.1286-demo.x86.run) Any help is appreciated!

---

### Post by Omnios on 2005-08-01
Well I can't give you a step by step but I remember from a while ago a linux game had a .run and what they had to do was open menu / run application and run it from there, Write in the path and filename and should start the install. ex: /home/..../...run. Not 100% how those work out though never tried it myself.

---

### Post by umdzig on 2005-08-01
[QUOTE=Omnios]Well I can't give you a step by step but I remember from a while ago a linux game had a .run and what they had to do was open menu / run application and run it from there, Write in the path and filename and should start the install. ex: /home/..../...run. Not 100% how those work out though never tried it myself.[/QUOTE]

even using the run application in the application menu still opens up a text editor. It wont install.

---

### Post by umdzig on 2005-08-02
I have found the problem....the file had to be made to open with sh, it kept wanting to open as a text file!!!!

---

### Post by umdzig on 2005-08-02
I am now plagued with another problem. How do i run the file in sh as root?

EDIT: nevermind i was being a fool...fixed

---

### Post by Omnios on 2005-08-02
Think you might have to change the permitions to make it executable. You can use chmod or right click the file choose properties/permissions click the executables. If this doesn't work you could run it in terminal by putting . infront of the filename

---

### Post by setite on 2005-09-12
yea just chmod +x doom3(which i renamed it too)
then click and drag the file to the run line to easily get teh filename...
run as root...

---


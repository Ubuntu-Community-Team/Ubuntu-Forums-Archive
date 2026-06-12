---
title: "[SOLVED] help with my new webcam ?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by tropcky on 2008-02-08
hi all 
ones agen the same old problem the web cam driver  but i still happy to be ubuntu user 
i have an old webcam  called ( logitech )  its dosent work  any way is any one can help me to make it work 

and to tell any program name to record videos from thes cam    

thank u so much

---

### Post by linuxwizard on 2008-02-08
Try using Ekiga see if webcam is detected/works. Also you might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there. If it does not work post the results of the command > lsusb

---

### Post by tropcky on 2008-02-08
thank u man for helping 
 about Ekiga i dont know what is it but any way i dont have it 

tropcky@tropcky-Linux:~$ Ekiga
bash: Ekiga: command not found
tropcky@tropcky-Linux:~$ sudo apt-get install Ekiga 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Ekiga
tropcky@tropcky-Linux:~$ 

and results of the command > lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-02-08
Ekiga is already installed. Applications > Internet > Ekiga. Looking for which driver you may need.

---

### Post by linuxwizard on 2008-02-08
Here you go this is the driver you need. Good Luck

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

---

### Post by tropcky on 2008-02-08
thank u thank u so much

---

### Post by linuxwizard on 2008-02-08
Did you install the driver and the webcam works ?

---

### Post by tropcky on 2008-02-09
oky i download it install it and evry thing and i tryed to have a pic with camorama  it was sooooo blue

if u see that 2 blue lines in the lighter   thes lines in real is red so red 

hoe 2 fix that   and how 2 get a program 2 record videos from the web cam   ( easy 2 use )  

thank u

---

### Post by tropcky on 2008-02-09
any help ?

---

### Post by linuxwizard on 2008-02-09
When you open Camorama their should be a white box on the right side, under effects, right click in that box will beings up some filter settings you can use. Add filter > color correction

---

### Post by tropcky on 2008-02-09
i tryed it noting it just play between the blue and green

---

### Post by linuxwizard on 2008-02-09
I take it that you also try using the other adjustment that are there also. Have you tried using Ekiga see if you get a better picture there ?

---

### Post by tropcky on 2008-02-09
ya in Ekiga the web cam work so good   thank u man and sorry for wasting ur time but u forgat to tell me a program to record vidoe :lolflag:

 thank u

---

### Post by linuxwizard on 2008-02-09
tropcky
You're Very Welcome I was glad that I could help you. That's great you have your cam working. You didn't waste my time we are here to help each other.  For recording video not for sure I am going to have to search on that see what to use.

---

### Post by tropcky on 2008-02-09
man thank u so much for evry thing  ppl like u who make me love ubuntu 
 ( and so sorry for my bad english ) 
thank u

---

### Post by linuxwizard on 2008-02-09
I have seen a few talk about VLC Player
[http://ubuntuforums.org/showthread.php?t=377517](http://ubuntuforums.org/showthread.php?t=377517)

Look down this page for > Recording to an AVI file
[https://help.ubuntu.com/community/Webcam#head-30cd93abefc680b108332471c2b6475a25668fb9](https://help.ubuntu.com/community/Webcam#head-30cd93abefc680b108332471c2b6475a25668fb9)

Look over these. Is this what you are looking for ?

---

### Post by tropcky on 2008-02-09
u know i was hop 2 finad somthing like move maker ( in windows ) i tryed vlc but i dont see what i am recording or know wher thes video saved

---

### Post by linuxwizard on 2008-02-10
Look 1/2 way down this page > [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) > it shows Window Movie Maker with 4 Linux equivalents software. See if they will help for what you want.

---

### Post by tropcky on 2008-02-10
hi man i cant faind any thing even near the windows move maker plez if u know wher it is just tell me what line 
thank u

---

### Post by linuxwizard on 2008-02-10
These are the Linux equivalents to window movie maker according to that link > iMira Editing > MainActor > Broadcast 2000 > Avidemux.

---

### Post by tropcky on 2008-02-10
thank u man so much i will try when i be at home  i am in the dem work :(  

 i will mark thes as sloved cus my cam is so fine now thankz 2 u bro

---


---
title: "sound problem in kde"
date: 2012-02-23
forum: Desktop Environments
---

### Post by forsubhi on 2012-02-23
I installed kde and sometimes the sound doesn't appear and Always longman dictionary doesn't emit any sound , however in gnome desktop the sound work well and longman work well
please help me to solve this problem 
I love kde very much

---

### Post by Rodney9 on 2012-02-24
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


You could also try pavucontrol

sudo apt-get install pavucontrol

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

Rodney

---

### Post by forsubhi on 2012-02-24
thanks man I'll try and reply when the problem is solved

---

### Post by forsubhi on 2012-02-24
oh ..  I catch something that can help you to help me 

the problem is not related to kde but 

when I run the program from the terminal 
by execute sudo ./ldoce5  ( the name of longman binary ) the sound not work and when I click on it and the Nautilus tell me to run it in terminal the sound work 
this print screen when appear in terminal when I click it and it work 


[IMG]http://s14.postimage.org/hf6x84vb5/Screenshot_at_2012_02_25_01_23_57.png[/IMG]


please help me to do like this in konsol cos the Nautilus doesn't work in kde

---

### Post by arapaho on 2012-06-10
Here is the solution to the sound problem:
install alsa-oss from Muon or
```
sudo apt-get install alsa-oss
```
In your /home folder there is desktop folder
/home/user/Desktop/
Create new text file. Open it and paste:
```
#!/usr/bin/env xdg-open
 
[Desktop Entry]
Comment=ldoce5
Encoding=UTF-8
Exec=aoss '/home/user/ldoce5//ldoce5'
GenericName=
GenericName[en]=
Icon=/home/user/ldoce5//splash.xpm
Name=ldoce5
Terminal=false
Type=Application
```

Of course don't forget to change user to the name of your own user name. Save. Rename it to ldoce5.desktop. Make sure it has executable permission.
Click on this file. And check, it should work.

If you want to have a shortcut in your menu open menu editor (right click on menu). There should be the icon of ldoce5 already there.
In command field paste:
aoss '/home/user/ldoce5//ldoce5'

If you don't have ldoce5 entry just create one. The icon is in ldoce5 installation folder.

For 64-bit I found this:
[http://starodubtsevss.wordpress.com/2010/05/09/install-ldoce5-longman-dictionary-on-ubuntu-64-bit/#comment-113](http://starodubtsevss.wordpress.com/2010/05/09/install-ldoce5-longman-dictionary-on-ubuntu-64-bit/#comment-113)
If it doesn't work - sorry, just google for other solutions.
If it works, confirm and mark topic as solved.

By the way you should rename topic name to something more precise, like: sound problem in ldoce5.

 ):P

---

### Post by forsubhi on 2012-06-10
I'll try and reply soon

---


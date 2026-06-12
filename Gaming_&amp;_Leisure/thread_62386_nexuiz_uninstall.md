---
title: "nexuiz uninstall"
date: 2005-09-04
forum: Gaming &amp; Leisure
---

### Post by ToiletDuck on 2005-09-04
I can only get about 3-4 fps on this game with a gforce 5600 with all the options either low or off. So how do i got about uninstalling the game?

Thanks

---

### Post by KingBahamut on 2005-09-04
Remove the directory. 

Are you using the properly enabled Nvidia drivers. i have a machine with a 5500 overlock 256, and it gets about 80 frames a second no problem.

---

### Post by ToiletDuck on 2005-09-04
[QUOTE=KingBahamut]Remove the directory. 

Are you using the properly enabled Nvidia drivers. i have a machine with a 5500 overlock 256, and it gets about 80 frames a second no problem.[/QUOTE]

 Is there a guide to show what drivers your using? Or how do i go about getting the current ones installed? Im only about 3 days into Ubuntu and my plate is full of things i want to use.

---

### Post by arnieboy on 2005-09-04
[QUOTE=ToiletDuck]I can only get about 3-4 fps on this game with a gforce 5600 with all the options either low or off. So how do i got about uninstalling the game?

Thanks[/QUOTE]
type the following in a terminal and tell us what fps u get:
```
glxgears
```

---

### Post by KingBahamut on 2005-09-04
assuming thats an Nvidia card in your system

drop to a terminal and do an 

sudo nvidia-glx-config enable 

then reboot your system. If you see an Nvidia splash before GDM kicks over, youve got drivers loaded for your card and should be getting some decent 3daccel.

---

### Post by arnieboy on 2005-09-04
[QUOTE=KingBahamut]assuming thats an Nvidia card in your system

drop to a terminal and do an 

sudo nvidia-glx-config enable 

then reboot your system. If you see an Nvidia splash before GDM kicks over, youve got drivers loaded for your card and should be getting some decent 3daccel.[/QUOTE]
before u do that make sure u have nvidia-glx installed.  do a:
```
sudo apt-get install nvidia-glx
```
After that backup your current xorg.conf to make sure u can get back to the original conf incase xserver crashes:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
then do:
```
sudo nvidia-glx-config enable
```
and reboot your comp.

---

### Post by KingBahamut on 2005-09-04
[QUOTE=arnieboy]before u do that make sure u have nvidia-glx installed.  do a:
```
sudo apt-get install nvidia-glx
```
After that backup your current xorg.conf to make sure u can get back to the original conf incase xserver crashes:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
then do:
```
sudo nvidia-glx-config enable
```
and reboot your comp.[/QUOTE]
 mah bad.....forgot that tiny little detail. 
=)

---

### Post by ToiletDuck on 2005-09-04
ok guys, i did uninstall the game. Then i came back and did what you posted. While trying to run the installer now i get this error.

.setup7438: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by arnieboy on 2005-09-04
[QUOTE=ToiletDuck]ok guys, i did uninstall the game. Then i came back and did what you posted. While trying to run the installer now i get this error.

.setup7438: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/QUOTE]
do tyhe following:
```
sudo apt-get install libgtk-1.2 libgtk1.2-dev
```
and then try running the game installer again

---

### Post by ToiletDuck on 2005-09-04
[QUOTE=arnieboy]do tyhe following:
```
sudo apt-get install libgtk-1.2 libgtk1.2-dev
```
and then try running the game installer again[/QUOTE]


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2

This is what im getting now

---

### Post by ToiletDuck on 2005-09-04
Follow up here, Its been a good night. I got it running with sound to boot. In fact, i have sound for all the games isntalled now.  :-P 

Once agin, thanks for the help

---

### Post by Alacrity on 2005-09-07
Thanks Bahamut!  Based on your Nvidia inputs, I now have Nexuiz in the right ball park.

I have 1300 fps on glxgears but it drops to 5fps when I attempt to log on to one of the servers for Nexuiz....even the lowest ping servers.

Another peculiar thing....when I first look at the servers, the pings are withing reach (40 for the lowest) but they all go >250 when I log on to the first and lowest ping server.

Any suggestions?

Thanks.

---

### Post by KingBahamut on 2005-09-07
Either a latency issue, or a ports issue. 

Im suspecting the later. 

TCP Ports for Nexuiz are as such 
26000 UDP 

Probably should be a static route to your machine more than a generalized open port.

---

### Post by Alacrity on 2005-09-08
Thanks for your feedback.  Unfortunately, I am a NOOB to Linux and Ubuntu.  Can you give me some inputs in how to either check and/or change the port?  Thanks for your help.

---

### Post by Alacrity on 2005-09-08
King,

Dropped all the "effects" and now have 70-200 fps.  Problem now is after 30 seconds I get the clock in the upper left hand corner and the game freezes.  Any suggestions?

---

### Post by KingBahamut on 2005-09-08
the clock = Network latency issue. 

Do you have a router? What type? 

If not, are you directly connected to your dsl or cable modem?

---

### Post by Alacrity on 2005-09-08
Hi King,

Thanks for helping out.  My router is an Airlink 101 54MB/s.  I am on DSL.  No problems with XP o/s on the network and the same system.  Are there special drivers I need for the Airlink?  I had to pull down special Nvidia drivers to get that going.... 

I see on Ubuntu a related problem I think.  Whenever I do the updates, it stalls midway and I have to restart to downloads.  Under XP, no restart of download is required. Seems very similar.

Any suggestions are welcome.

John

---

### Post by Alacrity on 2005-09-08
Thanks for your help in this process.

Finally sorted everything out.  Went to the Airlink101 web site and downloaded and installed the latest upgrade/update software.

Everything now running smoothly.  High fps, no freezes, and no clocks.

---

### Post by Alacrity on 2005-09-08
By the way, was a little disappointed in Nexuiz.  Seems a few years behind in realism compared to my favorite windows multiplayer game....HL2DM.

Would you know any Linux multiplayer game that comes close to HL2DM?  I would love to try it.

---


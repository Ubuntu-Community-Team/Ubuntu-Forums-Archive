---
title: "Wierd and random  happenings"
date: 2009-02-02
forum: General Help
---

### Post by Roger N on 2009-02-02
I am new to Linux. Loaded the Ubuntu 8.10 distro (from the January issue of Linux Format Magazine) as a double boot with XP.  
I am having apparently random problems – I cannot see that they have been covered else where – which are 

1)Sudden appearance of thin white zigzag lines all over the screen. If I open a window and expand it – then close it – the lines have disappeared.
2)Sometimes when I attempt to scroll the contents of a window (in firefox, Thunderbird etc)  the main bulk of the contents does not move – but the very top and the very bottom line of  the contents of the box will scroll. Occasionaly changing the screen resolution will fix this problem.  
3)Sometimes when I open up Open Office the centre of the workspace window is ok – but the area around (including the menus across the top) is transparent.
4) System Lockups that require me to turn of the PC to clear. Sometimes this can happen 5 times in 10 mins other times the PC can run for 5 hours with out problems.
As I have a SIS on-board video chip (which I see from the forums is not fully supported) I just put it down to driver problems  - cursed it and lived with it. 

However I have just come across another problem – Having completed the moving of my data across from windows  - I thought I would try the other windows Managers that cane with this version of the distro.  I can not get out of Gnome. I log out – select a different session from the options and when I log back in it takes me back into Gnome. I have also changed the default settings  under System-Admin-Login window   to default session Xfce – and it still comes back to Gnome. 
However if after I have tried changing to a different manager I use the Ctrl,Alt F7 or F9 keys the screen will alternate between Gnome and a blank screen with a blinking cursor. 
I can not put this down to a doggey video driver so perhaps my Ubuntu system  is flawed somewhere. But where?

Specs  are - AMD Sempron 300+ (S-754)  - Foxconn K8S760MG Motherboard with SIS 760/SIS 964 chipset – 512mb Ram – Relisys TL785 17” TFT monitor - Wireless Internet via a D-Link DWL G122 USB dongle 

Visual effects are turned off within Gnome

The first part of the x session error log is attached

As the distro came from linux format I have also posted the question there

Thanks for your help

---

### Post by kayvortex on 2009-02-02
The graphical problems all sound like a patchy driver, and you might be stuck with that if the driver support is poor.

As for loading a different graphics manager, I know this is an obvious thing to ask, but are you sure have installed all the necessary program/libraries?
I don't know how you installed Ubuntu, and especially what the CD from Linux Format magazine was or how it worked, but at the very least you could start synaptic (on my Hardy system: System -> Admin -> Synaptic Package Manager) and search to see if you have the necessary xfce libraries installed (just search for "xfce" and scroll down for names of packages that have xfce in them). I've never manually installed a graphics manager, let alone xfce, so I personally couldn't tell you what needs to be there, but you could try some of the other forum posts on installing xfce.

If you're sure that xfce *has* been installed correctly, then try looking at the system log messages (System -> Admin -> System Log) for errors related to graphics manager (try the syslog and Xorg logs, I think). If you post them here, then someone might be able to help you out, but, again, I'm not sure how much of a help I'll be.

Edit: sorry, you've already posted some of the X session error log. Well, the first thing that sticks out to me (and bear in mind that I know virtually nothing of what *should* be happening) is that it appears to be loading KDE4 (or at least, trying to). Xfce uses the GTK+ toolkit, so in order for Xfce to start, it will have to start some GTK+ stuff (or something like that, I imagine). Maybe you should post the rest of that log too.

---

### Post by Roger N on 2009-02-02
Hi
Looking through Synaptic it would apppear that all the relevant packages for both Xfce and KDE are loaded - I can also see the various hidden directories specificily for them. The magazine also stated that they would be loaded as a matter of course.

The references to KDE in the error log looked strange to me but without understanding the meanings I don't know the significance - It might just simply be saying that it is tring to load KDE but falling back to Gnome default - because even with that KDE reference I get Gnome. 

Have added more of the error log but removed most of the "loading writer for key" entries to keep the file size down. plus Sys Log (covering the period up to the first lock up for the day) , Xorg log (in two parts) and the user log which  seems to contain several references to failed operations includin X11 not loading.

Thanks

---

### Post by kayvortex on 2009-02-02
Hmmm, well, I don't see anything interesting in the log files (which, again, probably doesn't mean that there isn't something suspicious in there); but one thing you could try is this: stop the gnome session and start xfce manually, which will allow you to see any error messages produced directly as they'll just be spit out to the screen.

First, check to see if you have access to text virtual console: press Ctrl-Alt-F1. You *should* see a login prompt. If not try replacing F1 with F2 up to F6. If you never see a login prompt, you've got another problem in accessing a virtual console, and should not continue.

If, however, you do see a login prompt, then press Ctrl-Alt-F7 to go back to the GUI. To stop gnome (warning: don't have anything open that you may want!), type into a terminal:
```
sudo /etc/init.d/gdm stop
```
This should kill the graphics and you should end up at a screen prompting you to login. If that *doesn't* work and the graphics reappear, then try:
```
sudo killall gdm
```

If gnome has been killed, then login to the text console: you should then simply see a prompt like you would see when you open a terminal in a GUI.
Into that prompt, type:
```
startxfce4
```
which should start up xfce.
Now, that program *should* spit some info out to the screen from which you'll be able to see what is going wrong. If any graphics appear, but don't ever finish loading or anything like that, just type Ctrl-Alt-F1 (or F2-F6, whichever one it was that worked) to go back to your text console.

Edit: In any case, to get your GNOME GUI back, type:
```
sudo /etc/init.d/gdm start
```

---

### Post by Roger N on 2009-02-02
Not successful 
Ctrl Alt F1 takes me to a terminal 
Type in sudo /etc/init.d/gdm stop

After asking for password - it states "command sudo /etc/init.d/gdm not found" 

on typing startxfce4

I get error message /usr/bin/startXfce4: start X server

Fatal server error
Server is already active for display 0
if the server is no longer running, remove /tmp/.xo-lock

typing sudo /etc/init.d/gdm start
gets response "command sudo /etc/init.d/gdm not found"

Ctrl Alt F1 gets no response

So I have to re-boot

---

### Post by Roger N on 2009-02-02
Hi I must have typed something wrong the first time - This time it worked OK - went straight into Xfce4 without any error messages - So Xfce works just to work out why Gnome will not let me change sessions.

Seding this from within Xfce

Sorry about the mistype.

---

### Post by Roger N on 2009-02-02
Packing for the night - must go and see the wife - will try again tomorrow.

---

### Post by cariboo on 2009-02-02
The SIS 760/SIS 964 chipset isn't well supported, you may have better luck using the vesa driver. Using a different windows manager isn't going to solve the problem.

I have a system in my shop that has that chipset, I'll try the LiveCD on it and get back to you.

Jim

---

### Post by Roger N on 2009-02-04
Not been able to solve the session problem as such - I need more knowledge of how gdm works and its config files - but have produced a work around -

Have changed the default desktop manager to kdm - using 
sudo dpkg-reconfigure gdm  - kdm now implements my chose of session (and have gone to both Xfce and KDE - rather than keep droping me into Gnome as gdm did.

Am wondering if it might be worth reinstalling gdm. Would this be a good idea?

The screen problems seem to relate to a poor driver - Have had a look around but cannot find details of how to impement the VESA driver which is already one of the instaled packages. Would the Vesa driver restrict me to 800 by 600?

I can see from various posts that the Lock ups seem to be a familiar problem with 8.10 so perhaps it is a bug ( may be introduced by the special Linux format version). I have noticed that it occured most when resizing a window (but not always) so pehaps this is again linked to the driver!

---

### Post by Roger N on 2009-02-05
Hi Jim

Any luck with that Vesa driver test - and if yes how to I cange the driver. Not chasing you just taking the opportunity to bump this back up the list.

Regards

---

### Post by kayvortex on 2009-02-05
Well, the gdm config files are in /etc/gdm (gdm.conf or gdm.conf-custom). Now, I'm not sure how much further "help" I can be: perhaps you should post your problem on the GNOME forum (to at least find out how to diagnose the problem). I'd personally play it safe and try asking there before reinstalling gdm: there's nothing "wrong", per se, with reinstalling gdm, but it might just be overkill and *could* throw up more problems.

As for reconfiguring to use the vesa driver, you can probably just edit the xorg.conf file directly. I think you can just open /etc/X11/xorg.conf (with root permissions) and under
> Section "Device"
change the "Driver" line to:
> Driver  "vesa"
You could also do it the long-winded proper way by entering:
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "vesa" when it gives you a list of drivers t choose from. Some of the other questions it can ask can be daunting, but answer them as best you can or just leave the default suggestions.
In any case, backup your xorg.conf file beforehand:
```
sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf-original
```

---

### Post by Roger N on 2009-03-10
Hi - Appear to have now resolved these problems - Have installed a cheap APG Video card (Nvidia 5200 £23) - all scroll and transparency problems have ceased. PC has not locked either - so it does appear that all the problem were a poor driver for the sis on board chip.

The Nvidia 5200 works OK with Ubuntyu 8.10 - with full resolution options - Installation was a bit tricky at first as it would only put me in lo res mode. So I took the card out - and downloaded the 173 driver - put the card back in and fixed X - Now works perfectly - 
Still using the kdm as apposed to gdm - so don't know it that was also affected by the poor driver.

Regards

Roger

---

### Post by Roger N on 2009-03-10
Forgot to amend the title to say salved

---


---
title: "Clean Install of Ubuntu on Latitude D600 Freezes"
date: 2009-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DoubleStew on 2009-11-18
I got a free Dell Latitude D600 laptop from work with the hard drive reformatted to remove any work related stuff. NoOS present.
 
I thought I'd give Ubuntu 9.10 a try and downloaded the ISO and installed it on my laptop. If I run it in failsafe Gnome mode it boots up fine and applications work but no wireless connection. I'm guessing failsafe is something along the lines of Windows Safe Mode - limited drivers etc. However, if I boot up in 'normal' Gnome I get the login screen OK but then it useally freezes and a I have to forcibly shut down. Occassionally it will boot up fully but as soon as I open any application it freezes.
 
I'm a total novice at linux and I'm at a loss what to do. 
 
I have trawled the forums for answers with suggestions on amending the xorg.conf file so I now know about the Terminal and what a sudo command looks like but that file doesn't seem to exist in failsafe mode.
 
Should I try the Dell 9.4 ISO that is available on these forums? If I do that can I upgrade to 9.10? Or are there any other suggestions anyone may have?
 
Thanks

---

### Post by mikewhatever on 2009-11-18
It would be nice to find out more about the hardware. Boot with failsafe enabled again, get to Terminal and run the following:

```
sudo lshw > ~/Desktop/hardware.txt
```

Then look for the hardware.txt.file on  you desktop and post it here as an attachment, if possible.

---

### Post by DoubleStew on 2009-11-19
Thanks Mike. 
 
Hardware text file attached.

---

### Post by meson2439 on 2009-11-19
Have you done memory check on both CD and ram. The last time it happened to me is due to the cd having wrong hashes due to incomplete download of the image cd another time due to broken RAM.

---

### Post by pawhtiobo on 2009-11-19
Hi :)

Check this tread:

[http://ubuntuforums.org/showthread.php?t=1245109&highlight=d600](http://ubuntuforums.org/showthread.php?t=1245109&highlight=d600)

Iadvise you to install Ubuntu LTS 8.04, otherwise you will have problems with ATI VGA Card.

See ya...

---

### Post by didayha on 2009-11-19
I have trawled the forums for answers with suggestions on amending the xorg.conf file so I now know about the Terminal and what a sudo command looks like but that file doesn't seem to exist in failsafe mode.

---

### Post by mikewhatever on 2009-11-19
> **didayha said:**
> I have trawled the forums for answers with suggestions on amending the xorg.conf file so I now know about the Terminal and what a sudo command looks like but that file doesn't seem to exist in failsafe mode.

It seems like your card doesn't play nicely with desktop effects, and everything is ok when they are disabled in gnome failsafe.
xorg.conf used to be an essential configuration file, but since a few releases back, it's only an option. Find the configuration you want to use, then run **gksudo gedit /etc/X11/xorg.conf** ,paste the configurations into the file, save and exit. There is no need to reboot to test your new xorg.conf, just logout and log back in.

---

### Post by DoubleStew on 2009-11-19
OK, I think I broke it.
 
I tried Mike's suggestion of creating a xorg.conf file and I pasted in the code as given in this thread [http://ubuntuforums.org/showthread.php?t=550082&page=2](http://ubuntuforums.org/showthread.php?t=550082&page=2) by Michael Longval
 
I've no idea what all the suff about compiz or Emarald means.
 
When I rebooted, I get no GUI just a prompt to login to the laptop and password, then I some stuff about last login, packages and updates and finally a prompt/command line that states:
 
stew@stew-laptop:~$
 
And I've no idea what to do next :(
 
I can re-install Ubuntu 9.10 at no cost as there is nothing on the laptop.
 
Just a noob making some noobish mistakes
 
=======================================================================
Re-installed Ubuntu 9.10
 
I did a bit more hunting around and I thinkI have taken a big step forward to solving the problem wth some information in this thread: [http://ubuntuforums.org/showthread.php?t=1305349&highlight=D600+video+card](http://ubuntuforums.org/showthread.php?t=1305349&highlight=D600+video+card)
 
I used the exorg.conf posted by Giblet5
```
Section "Device"
        Identifier "ATI Radeon"
        Driver "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection
 
Section "Screen"
    Identifier    "Default Screen"
        Device          "ATI Radeon"
    DefaultDepth    24
EndSection
```
 
I can now boot up, open applications and connect to the internet.
 
The problem is that is not quite right. If I resize a wndow it sometimes works but usually it freezes and gets a black border round it. I can still open other applications but I can't resize them or close them down as they freeze with black borders round them. I will aslo get black flashes and other artefacts.
 
Also, sometimes when I login I get the toolbars at the top and bottom but the desktop doesn't diplay - I get a black screen with Ubuntu - the screen you get when booting up but applications such as mozilla still run and then sometimes the desktop will suddenly come back usually after a few black flashes.
 
Any suggestions on what I can tweak to try and improve things?

---

### Post by mikewhatever on 2009-11-19
You don't need to reinstall the OS just because of one configuration file. If greeted with command line login, log in and run the following to delete the previously created xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```

then reboot

```
sudo reboot
```

I'd suggest turning off the desktop effects under System->Preferences->Appearance, and also, look for more specific configurations for your graphics card, which is Radeon RV250 [Mobility FireGL 9000].

---

### Post by upwinger on 2009-11-19
I too have a  Dell Latitude D600 and had problems with latest version of Ubuntu JJ. But with stable version HH the laptop works great. Now if I can only figure out how to make jack work so that I can record some guitar loops with hydrogen drum machine layers i would be very happy   :guitar:

---

### Post by DoubleStew on 2009-11-19
Thanks Mike, I've turned off the effects and that seems to have done the trick!
 
I'll have a hunt around to see if there are more specific configurations for my graphics card and ... learn how to use Ubuntu!

---

### Post by mikewhatever on 2009-11-20
Looks like there is a thread dealing with Latitudes D600/C600 graphics in the Dell subforum. Take a look.
[http://ubuntuforums.org/showthread.php?t=828588](http://ubuntuforums.org/showthread.php?t=828588)

---

### Post by jdos2 on 2009-12-08
This is a couple weeks into the thread, but I'm having trouble getting compiz to simply NOT start- I can't quite get to the "Appearance" panel before the laptop locks up- and of course, cant get to a shell to shut it down nicely when things get frozen.

I know there's a thread about to show which file to edit to do that. Gotta dig deeper...

---


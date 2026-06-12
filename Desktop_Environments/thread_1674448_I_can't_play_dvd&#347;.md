---
title: "I can't play dvd&#347;"
date: 2011-01-23
forum: Desktop Environments
---

### Post by bobcoss on 2011-01-23
Hi, 

I installed Ubuntu 10.10 64bit a month ago.  I&#7743; sure that it played DVDs at one time but I tried to night to play one and it won't now.  I tried it using Movie Player and VLC.  I hear sound, but the picture is black.   In VLC, it appears that there is video, but it is very dark.  I can see a little bit of something I know is bright on my TV and DVD player. 

I have a Nvidia GT 220 card running two displays
I&#7743; using the NVIDIA drivers
I installed the "Ubuntu restricted extras" from the Ubuntu Software Center.
I also installed the gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multivers, gstreamer0.10-plugins-ugly,  and gstreamer0.10-plugins-ugly-multivers

Does anyone know why I can't play DVDs?

Thank you in advance for your support.

---

### Post by Copper Bezel on 2011-01-23
I can help with this part: DVDs doesn't take an apostrophe, and you seem to be using the international keyboard layout (with deadkeys) without knowing it. = ) Go ahead and add the layout for AltGr Deadkeys or the standard US to get your apostrophe key back.

In any case, you clearly do have DVD codec support and libdvdcss installed, if you're hearing sound at all and possibly seeing a picture. Is it possible that the disk has some unusual kind of copy protection? Have you tried other DVDs, or is this problem only coming up with one particular disk?

---

### Post by garvinrick4 on 2011-01-23
Do make sure you have installed open terminal:
```
sudo apt-get install libdvdcss2
```

---

### Post by bobcoss on 2011-01-24
Thank you.  I'm having the problem playing DVDs with all of my disks.   I cycled through a bunch.   I double checked and I have libdvdcss2 installed properly.  I also have libdvdread4 installed.

I tried clicking on some .avi and .mkv files, and it isn't working with either movie player or vlc.

I'm getting frustrated.

BTW I know about the international keyboard.  I need it to write in Spanish.   I get lazy because I don't like the way the us international keyboards work in the last couple of versions.

Anyone have any other ideas about my dvd, .avi, and .mkv problems?

Thank you.

---

### Post by freshmeatz on 2011-01-24
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jchw on 2011-01-24
I tried to install libdvdcss2 and got the following message. I have access to the restricted repositories in Ubuntu software Centre. A couple of days ago I had to reinstall 10.10 and since then I have had nothing but problems, the DVD does not work, wifi failed, Rythembox does not work etc. My original install of 10.10 worked like a dream until the reinstalation.

john@john-eMachines-E525:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate
john@john-eMachines-E525:~$

---

### Post by bobcoss on 2011-01-24
John,

Oddly enough I can help you with that.

Open a terminal and enter 

sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
It will install libdvdcss2 for you.

---

### Post by Copper Bezel on 2011-01-24
I'm sorry if I came across as sarcastic earlier. Anyway, I'm not certain what to say except that this is very unusual. 

Try this: disable one of your displays, log out, log back in, try your movie.

I don't want this to work, but I've seen VLC drop to a black screen, with the audio still playing exactly as you describe, if my desktop resolution gets too big with two displays going - some kind of unredirecting/compositing/video card cluster****. I don't have a fix or know if there is one.

---

### Post by jchw on 2011-01-25
Bobcross,

Thanks for that info. I forgot the sudo piece at the front - must be old age!

I tried the fix but unfortunately it did not work and it came back with the following log;

john@john-eMachines-E525:~$ sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up firmware-b43legacy-installer (4.178.10.4-4) ...
Not supported card here (PCI id 14e4:4315)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-eMachines-E525:~$


Seems to me to be a problem with b43 firmware but as a newbie I have no idea how to fix it.

---

### Post by jchw on 2011-01-25
I found a solution to this in Bug no 651010 post 3 by Kontza.

"
                 Had the same problem, then I noticed that instead of firmware-b43-installer I had to install (manually, via synaptic) firmware-b43-lpphy-installer.  My install is a x64-version via netboot, i.e. mini.iso. Just the other  day when I tried x86 netbook live-cd, it managed succesfully to  automatically set up my wireless.
 I would still keep this as a valid bug, since the system couldn't automatically resolve this."


This has solved both my DVD and wifi problems in one simple fix. Wow what a relief. Thanks Kontza.

---


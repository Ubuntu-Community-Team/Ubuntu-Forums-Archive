---
title: "Okay. So I broke X. what now?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by SpencerStarnes on 2006-09-22
Okay, so I was editing my xorg.conf file. and I tryed to add 1440 X 900 and I did pretty much everything they told me to do. (I also made a backup) 

this could be what I have. Im not sure. 
I just redid the changes (added 900 instead of 1440X1400 and changed the monitor section)

```
Section "Monitor" 
 Identifier "monitor1" 
 VendorName "Plug'n Play" 
 ModelName "H191W" 
 HorizSync 31-83 
 VertRefresh 56-75 

 ModeLine "1440x900_60" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync

EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "H191W"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

```

okay so heres the problem. 
X crashes, bluescreen, really messed up text. blah. 

So. I go to the terminal, log in, enter my password. and try to run "X"

turns out X wont start because it cant find a montior. or something of the sorts. (im at school right now, so I cant really go home and check what it is right away. Also our internet is down.)

So, I try some commands to restore the xorg.conf file. I think the command was.

```
**sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf**
```
 
and it says that /etc/X11/xorg.conf_backup is not a exisiting file or location. 

I KNOW that backup file was there. 

Remember, that might not be it exactly. but I think its pretty close (I tryed it alot of times)

okay. so I was quite upset. bleh. 
Any ideas?

[I]my setup is
Nvidia 5200
AMD 3000+
I had installed XGL and Compiz
Ubuntu 32 bit
Nvidia drivers
Help meee!!![/I]


Also, Let me show you guys what I followed for XGL, Widescreen and other stuff. 

[http://ubuntuforums.org/showthread.php?t=261856](http://ubuntuforums.org/showthread.php?t=261856) Wide screen tort.
[http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/](http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/) XGL tory

I also used automatix to install the drivers. ^_^
thanks in advanced. 
spence

---

### Post by wieman01 on 2006-09-22
Try this:
> ls -l /etc/X11/xo*
Does the backup file show up somethere?

---

### Post by SpencerStarnes on 2006-09-22
I'll have to wait until I get home at somepoint.

Also, is there anyway I can just fix my xconf, IN the terminal?
Like Gedit wont start. because X wont. :-\

im a newbie at this. this is only my second week of Linux...

---

### Post by wieman01 on 2006-09-22
Yes, try this command first (from the command line).

---

### Post by Foxman2k on 2006-09-22
pico is a pretty easy test editor for command line.

---

### Post by SpencerStarnes on 2006-09-22
does it come pre-installed?

if not, can I Apt-get it in command line?

---

### Post by wieman01 on 2006-09-22
I know "nano" and it is preinstalled. Fairly easy to use. Promise.

---

### Post by tseliot on 2006-09-22
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by wieman01 on 2006-09-22
And by the way... If you need a text-based internet browser, try "links". May turn out to be helpful:
> sudo apt-get install links
Start with "links".

---

### Post by alecjw on 2006-09-22
Try dpkg --reconfigure x-server-core

---

### Post by madc on 2006-09-22
So. I go to the terminal, log in, enter my password.


...and then: sudo dpkg-reconfigure xserver-xorg

that will do...after few answers you'll be in the terminal again, then start x with: startx;)

---

### Post by SpencerStarnes on 2006-09-22
I tried 
```
dpkg --reconfigure x-server
```

didnt work

but when I get home ill try adding -core

---


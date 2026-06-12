---
title: "Screen resolution 640 x 480 issue"
date: 2008-06-03
forum: Desktop Environments
---

### Post by dhew on 2008-06-03
---------------------------------------
| UPDATE: I fixed it!  See several posts below this |
---------------------------------------


Hey

So Im really new to Ubuntu, but managed to get it installed with no problem (8.04).  However, after install, my screen resolution has been 640 x 480 with no option to change it.  I've searched and searched the forums and support docs and can't seem to find a solution to this issue.  When I run "xrandr -q" I am told that the only resolution I can have is 640 x 480.  I am running this on an old dell with integrated intel graphics, and can't seem to find anything on how that changes things.  

I came from XP, so know that this system is beyond capable of running a much higher resolution (like 1280x1024)...I just can't seem to figure out how to force that here.

Any ideas?

PS;
as I mentioned, I'm new, so please go into the details.

Thanks!

---

### Post by lok on 2008-06-03
Hey mate. If you can't use System > Preferences > Screen Resolution
This might be worth a try:

Edit your /etc/X11/xorg.conf file (Don't forget to make a backup)
Go to the Screen section(usually near the end) and in the SubSection "Display" part add the line:

Modes "800x600" "1024x768" "1280x1024"

example:

Section "Screen"
	Identifier "..."
	Device     "..."
	Monitor    "..."
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes     "800x600" "1024x768" "1280x1024"
	EndSubSection
EndSection

X will automatically use the first mode. But for safety's sake it's best to use a small resolution until you know what one is best.

When you have that done. Logout and when the login box comes up hit Ctrl + Alt + Backspace(this restarts X11 and gets it to look over what's in the xorg.conf file)

---

### Post by dhew on 2008-06-03
Ok, so when I do that nothing significant happens.  To start with, my X11.conf file didn't have most of what you posted in it to begin with.  But after a little editing and restarting it edited itself to the following:

Section "Screen"
     Identifier "Default Screen"
     Device      "Configured Video Device"
     Monitor    "Configured Monitor"
     Defaultdepth    24
     SubSection "Display"
                   Depth      24
                   Virtual     640          480
                   Modes                      "640x480@60"
     EndSubSection
EndSection


...And still no ability to change resolution.

---

### Post by the_one on 2008-06-03
So... now we're back to editing the xorg.conf file?
It was bad enough when we had to run "xserver-Xfree86" from a terminal to correct screen resolution problems. Now "xserver-xrog" only configures the keyboard, then quits!
What's up with that???
Why doesn't the Dev team give us a proper GUI screen res changer!!](*,)

---

### Post by dhew on 2008-06-05
Any ideas?

---

### Post by vashwood on 2008-06-05
Add

HorizSync and VertRefresh values to the monitor section

and then

Option "NoDDCValue" "True"

to the device section. This will keep X from reverting back to 640x480.

---

### Post by dhew on 2008-06-06
Hey,

--------
I fixed it!
--------
I'm running the latest stable release of Ubuntu Desktop (8.04 Hardy)

I don't really know how or which item finally did it, but I did several things here.  

First, I edited the hell out of my xorg.conf file.  I've made so many versions of that thing!  I added the 'Option "VideoRam" 7892k"' line under "Device".  I added 'Option "DPMS"', HorizSync, a Modeline I got from the online Modeline generator, and the 'Option "NoDDCValue" "True"' line to "Monitor" section.  In "Screen" section, SubSection "Display", I added a mode with two resolutions for every depth just about.  I previously only had a mode and depth for the default, 24 depth.  Now I have...


```
Depth 1
Modes "1024x768" "1280x1024"
Depth 4
Modes "1024x768" "1280x1024"
Depth 8
Modes "1024x768" "1280x1024"
Depth 16
Modes "1024x768" "1280x1024"
Depth 24
Modes "1024x768" "1280x1024"
```

I also added:

```

Section "DRI"
Mode 0666
EndSection

```

Second, I set up 855resolution

I followed the online guides for this, but they are not very helpful unless you are willing to experiment and figure things out for yourself.  The two I saw were:

[http://ubuntuforums.org/showthread.php?t=27029]("http://ubuntuforums.org/showthread.php?t=27029")

[http://ubuntuforums.org/showthread.php?t=24923]("http://ubuntuforums.org/showthread.php?t=24923")

I had to have both open while I did the 855resolution editing and found myself constantly switching back and forth between them to see what to do next.  Having said that, they were both invaluable to the 855resolution part of the process.  A little update though...I could only get 855resolution from the running 
```
wget http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb
```  
It was the only place I could find it as [http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/) is offline and thats the link everyone else references.

As for 855resolution setup...

You run:
```
sudo 855resolution -l
```

and that outputs a list of modes.  You pick one and then edit the config file to reflect that ONE mode and resolution only using:

```
sudo gedit /etc/default/855resolution
```

One guide says to pick an unreasonably high resolution your monitor can't ever reach, but I found this to be untrue.  If you just set 855resolution to what you want your screen to be (mode 58 in my case), then it will work fine.

Mine looks like this:

```
MODE=58
XRESO=1280
YRESO=1024
```

And, finally, I changed my video driver to "i810" in the Device section.

After all of that I did a restart (NOT a restart of X, but a full system restart) and things worked!  I did numerous "CTRL + ALT + Backspace" restarts of X and none of them worked, but a full system restart did.

Ok, so I think I've included everything I've done.  Its been an uphill battle the whole way, but I finally made it!  I would highly suggest you try what I've posted here before you try updating the BIOS [I almost did...actually, I was trying to update the BIOS with the full system restart but my BIOS disk was make by a fool (read: me) who didn't know how to make it run at startup, so when the computer restarted the BIOS didn't change, but the resolution did from all the changes I made that a restart of X didn't reflect!].

---


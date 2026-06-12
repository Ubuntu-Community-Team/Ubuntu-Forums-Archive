---
title: "Screen Resolution"
date: 2005-12-01
forum: Desktop Environments
---

### Post by purinkle on 2005-12-01
First things first, hello.

I am new to the world of Linux and was recommended by a friend to get started with Ubuntu.

I downloaded and installed the OS yesterday.

I have logged into the system for the first time and the screen resolution is set to 640x480.

I have gone into System > Preferences > Screen Resolution and tried to change this but it only gives me one resolution and on refresh rate of 60Hz.

I have had a look at some of the other posts and have got lost with my newbie-ness.

Please help!

Thanks

---

### Post by prawdapunk on 2005-12-01
1. You should install drivers for your graphical card
2.If that won't act, you should modify xorg.conf 
etc/x11/xorg.conf 

In console sudo gedit /etc/x11/xorg.conf

Salute

---

### Post by purinkle on 2005-12-01
Excuse me, for being a dumbass

But how do I go about installing the correct drivers?

And, failing that, how do I go about modifying xorg.conf?

Thanks
Rob

---

### Post by MDoten on 2005-12-01
What you could do is go to [Ubuntu Guide]("http://ubuntuguide.org/#installnvidiadriver") and do what it says to install the nvidia drivers (hopefully that is what card you have).

---

### Post by _4ace on 2005-12-01
When you run the    sudo gedit /etc/X11/xorg.conf       command in a terminal(located under accessories in the applications meny, the configuration file that you computer runs through when it boots. It tells the system stuff it needs to be reminded of.

somewhere on dewn in the ducument this shows up. For my screen to work I had to manually update the file with the correct Horisontal and vertical refresh rates, called HorizSync and VertRefresh. You'll find these values in the manual for your screen. Also where it said Driver      "nividia", I had to type in nividia because it just said "nv". but I had already installed the nividia driver though a neat little application called Automatix. 

I use a crt screen but if you use LCD maybe all you have to do is get the driver sorted out.


extract from xorg.conf.............


Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31,5-107
	VertRefresh	50-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by purinkle on 2005-12-01
I've tried to installed the drivers by following the instructions in the Starter Guide

When entering the command *sudo apt-get install nvidia-settings* I get the following message

Reading package lists... Done
Building dependency tree... Done
Package nvidia-settings is not available, but is referred to by another package
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-settings has no installation candidate

The rest of the instructions seem to work fine

After restarting I select Applications > System Settings > NVIDIA Settings and get the following error message:

**Cannot launch entry**
Details: Failed to execute child process "nvidia-settings" (No such file or directory)

Where do I go from here?

Thanks
Rob

---

### Post by purinkle on 2005-12-01
Posted twice.

Please ignore this entry but not the one above.

Thanks
Rob

---

### Post by MDoten on 2005-12-01
[QUOTE=purinkle]When entering the command *sudo apt-get install nvidia-settings*[/QUOTE]

I'm sorry, I didn't put in the exact thing you need. The package that you want is nvidia-glx I believe. So the command would be *sudo apt-get install nvidia-glx*. This might install the settings as well, if not, run the first line again and you should be set.

---

### Post by purinkle on 2005-12-01
Yeah, *sudo apt-get install nvidia-glx* is the line before *sudo apt-get install nvidia-settings* and I have gone through the method twice so that doesn't seem to be the fault.

Thanks
Rob

---

### Post by _4ace on 2005-12-01
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

try this.

---

### Post by MDoten on 2005-12-01
Ok, the thing you are going to have to do is edit the xorg.conf file. This is located in /etc/X11/. [COLOR="Red"]MAKE A BACKUP OF THE FILE BEFORE CHANGING IT.[/COLOR] :D Ok, so here goes:

Under the **Section "Module"**, you need to make sure that you have a line that is: *Load "nvidia"*

Next, under the **Section "Device"**, set up your video card, mine looks like this:

Section "Device"
        Identifier      "Nvidia Geforce 4"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection

My BusID is AGP.

Also, you'll have to set up your monitor in the **Section "Monitor"**. Basically you'll have to find specs for your monitor and use those. Mine is:

Section "Monitor"
        Identifier      "Viewsonic"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-200
EndSection

The next section is the **Section "Screen"**, where it all comes together. Mine looks like this:

Section "Screen"
        Identifier      "Viewsonic Screen"
        Device          "Nvidia Geforce 4"
        Monitor         "Viewsonic"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
                ViewPort        0 0
        EndSubSection
EndSection

You take the Device identifier and Monitor identifier that you made above and plug them in for this section. I would leave both Depths the same and change the Modes to the resolutions that you want.

Make sure that in **Section "ServerLayout"**, the screen property is the identifier for the Screen section that you made above.

Once you finish editing it, save it. Log out of Ubuntu and press *ctrl + alt + backspace* (this will restart X).

Hope that helps.

---

### Post by purinkle on 2005-12-01
Okay we may have found the root of the problem

I downloaded and ran Automatix and tried to install the NVIDIA drivers

Automatix then gave me the error message:

Error : Video Card is not detected as NVIDIA

Any ideas?

Thanks
Rob

---

### Post by MDoten on 2005-12-01
What video card do you have?

---

### Post by purinkle on 2005-12-01
I'm not sure.

I think it is an Intel 810

Is there someway I can make sure?

Thanks
Rob

---

### Post by MDoten on 2005-12-01
Go find the specs of the computer online or something.

You could possibly edit xorg.conf and change the display modes that the screen supports.

---

### Post by purinkle on 2005-12-01
Yes it is an Intel 810

What would be the best way to go about editing xorg.conf?

If that is now the best method

Thanks
Rob

---

### Post by [Yatta] on 2005-12-01
[QUOTE=purinkle]I'm not sure.

I think it is an Intel 810

Is there someway I can make sure?

Thanks
Rob[/QUOTE]
Purinkle first thing u need to do is find out the specs of your machine like **MDoten** suggests. Since your not so sure on what u  have u can try 
```
dpkg-reconfigure xserver-xorg 
```
That might do some of the leg work for u.
but HONESTLY find out about ur hardware before u mess it up.

---

### Post by purinkle on 2005-12-01
I ran the xserver thing and it identified the driver as i810 and it recognised my monitor as a Dell E173FPf.

Which, to my knowledge, is correct.

I also found another website with the specification of my Dell Optiplex GX110 and confirmed that it is an Intel 810.

After running the xserver application the problem still remains.

Is there anything else I can try?

Thanks
Rob

---

### Post by purinkle on 2005-12-02
Bump

---

### Post by RAOF on 2005-12-02
Searching for "intel i810 resolution" nets us [this thread]("http://www.ubuntuforums.org/showthread.php?t=61973&highlight=intel+i810+resolution"), which may help you.

---

### Post by RAOF on 2005-12-02
There's also this "[howto change the screen resolution]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=resolution+howto")"

---


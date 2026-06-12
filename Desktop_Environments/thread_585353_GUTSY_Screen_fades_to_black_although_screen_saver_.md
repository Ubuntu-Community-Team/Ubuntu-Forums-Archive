---
title: "GUTSY: Screen fades to black although screen saver is disabled"
date: 2007-10-21
forum: Desktop Environments
---

### Post by tim__b on 2007-10-21
Hi people,

I googled since Gutsy got released for a solution to my problem, without success up to now:
Even though I completly disabled any kind of screensaver or turning of my notebook's monitor it got disabled after about 10 minutes of inactivity. When pressing a key or moving the mouse it is reactivated.
As stated i completly disabled turning of the monitor on inactivity in gnome-power-preferences on both profiles, wired and accumulator. I also tried deactivating DPMS in xorg.conf, but also without any success.

I hope someone can help me on my problem. Thanks in in advance.

my system:
gusty (upgraded from feisty) with compiz on an ati radeon xpress with fglrx.

---

### Post by benfortuna on 2007-10-22
I have a similar problem using restricted drivers on ATI Radeon 9600 (altho I have screensaver enabled but it doesn't work - just get the fade to black issue). Bug here may be related:

[https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/33717](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/33717)

---

### Post by praxis22 on 2007-10-22
same here, added my details to the bug report

---

### Post by ssd008 on 2007-10-22
I have the same issue on my tower.  It even pops up when I am using Mplayer to watch tv and the screensave functions have been doubly disabled.

Very annoying.

---

### Post by tim__b on 2007-10-23
It seems that the options ```
Option "DPMS"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
```in xorg.conf in the section ServerLayout help to keep the monitor alive. never the less gnome-power-preferences settings are still ignored for me.

---

### Post by ssd008 on 2007-10-23
I will try this immeaditely! 

Thanks much for finding a solution.

---

### Post by ssd008 on 2007-10-23
Apparently if you have 

Option "DPMS"

anywhere else in your xorg.conf it will apparently kill x when you open the screensaver options. Or at least thats what i experienced and it stopped after I removed just that line from the ServerLayout section.

Hope that helps!

---

### Post by tim__b on 2007-10-24
Sorry, my fault.```
Option "DPMS"
``` belongs to the section of Monitor, ```
	Option		"BlankTime" 	"0"
	Option		"StandbyTime" 	"0"
	Option		"SuspendTime" 	"0"
	Option		"OffTime" 	"0"
``` to the section of "ServerLayout". Nevertheless I had no problems starting my xserver with DPMS option in the wrong section.

---

### Post by wild_oscar on 2007-10-24
I am experiencing a similar problem.

With Gusty and an ATI Radeon 9500, the screen fades to black after 10 minutes when watching some films in Xine, even though I have the "screensaver reset interval" defined for as low as 1 minute.

---

### Post by jeroenzw on 2007-10-24
I have a similar problem. Don't know if it's the same though:
Using Kubuntu 7.10.

I turn on my laptop (IBM R52), and KDE works like a charm. The screen doesn't go black for hours (which is the expected result, because I've turned off automatic screensaver, and Power Management in system settings, and I changed xorg.conf with the options mentioned above)

I start an OpenGL screensaver manually with the panel applet (lock/logout), still no problem. 
But once I come out of the screensaver, the monitor turns black every five minutes of idle-time, and stays that way until I reboot.

It is a mystery...

---

### Post by jeroenzw on 2007-10-25
Little update: I tried some different settings using xset (like xset -dpms, or xset dpms force on) but to no avail.

---

### Post by likwidsnj on 2007-10-28
> **tim__b said:**
> Sorry, my fault.```
Option "DPMS"
``` belongs to the section of Monitor, ```
	Option		"BlankTime" 	"0"
	Option		"StandbyTime" 	"0"
	Option		"SuspendTime" 	"0"
	Option		"OffTime" 	"0"
``` to the section of "ServerLayout". Nevertheless I had no problems starting my xserver with DPMS option in the wrong section.

Had this same issue on my HP dv6205us. This fixed it for me.

---

### Post by carnageblood on 2007-12-29
maybe this will help you :[http://www.shallowsky.com/linux/x-screen-blanking.html]("http://www.shallowsky.com/linux/x-screen-blanking.html")

---

### Post by Dean96003 on 2008-01-31
Can someone give me a screenshot of what these new entries should look like in the xorg.conf file? REAL NEW!
Thanks

---

### Post by Dean96003 on 2008-01-31
Where does it go in this clip? Thanks

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

---

### Post by praxis22 on 2008-02-01
If you're real new you probably shouldn't be messing with xorg.conf you can easily kill your desktop doing that, and by that I mean you end up with nothing more than a command line on screen.

Before you do anything make sure you take a backup of the original.

That said I got mine working by upgrading from ruby to compiz-fusion and using the latest propreitary ATI drivers. I also reconfigured the kernel, though that may or may not figure into solving the problem.  The one thing I did do however was I ended up recompiling the screensaver from source. 

I'd encourage you to play, but take sensible precautions if you do, should all else fail, run this command if you kill the desktop:

**sudo dpkg-reconfigure xserver-xorg**

This will reconfigure your xorg.conf, you'll probably need to reboot at that point:

** sudo shutdown -h now**

good luck

---

### Post by punkybouy on 2008-02-11
I have a similar problem on a Gutsy upgrade from Feisty.  The web browser is open, I go do something and comeback after 10 minutes to find a black screen and no screen saver.  The PC does not respond to any input.  Neither moving the mouse or clicking mouse buttons or hitting the enter key do anything.  Not even the NUM lock key responds.  I have to push the reset button or power off and on to recover.  This PC has been upgraded to Edgy from Feisty and from Feisty to Gutsy without any issues but I think this is a bug.

---

### Post by punkybouy on 2008-02-12
Does anyone know of any screensavers that don't cause any issues?

---

### Post by Ripfox on 2008-02-16
The first solution in this thread works fine. It is not hard to put these lines in xorg.

---


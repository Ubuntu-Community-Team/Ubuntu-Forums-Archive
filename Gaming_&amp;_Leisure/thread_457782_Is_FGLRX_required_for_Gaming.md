---
title: "Is FGLRX required for Gaming"
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by freefromXP on 2007-05-29
I recently installed Fiesty on a XP2700 1.5g /w ATI 9800 pro.  I disabled FGLRX and use AIGLX when I installed beryl using this post. [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

  I can't get UT2004 to play anymore nor Can I get WOW to play with WINE.  DO I need FGLRX to play game or do I need to get out of my beryl desktop first?  

  Beryl works great including water trail.


  
Here is my xorg.conf 

glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

direct rendering: Yes

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver	"ati"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
        Option  "XAANoOffscreenPixmaps"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Visual Sensa"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true" 
        Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "enable"
EndSection

---

### Post by jimminy_kriket on 2007-05-29
Sorry if im totally off, im noob with linux. 

But fglrx is the ati driver correct? And aiglx just enables x.org to render things? (desktop effects?)

If you uninstalled fglrx, what drivers are you running currently? Aiglx isnt a driver last i checked so yes, you probably need fglrx.

Edit: I read the link and see you are using the default ubuntu drivers. Considering ati's propriatary drivers suck, i assume the default ubuntu ones are even worse for gaming. I suggest you try using xgl + fglrx,  I dont think the author of that guide had gaming in mind.

---

### Post by sloggerkhan on 2007-05-29
FGLRX is the ATI official commericial driver. ATI driver is the open source driver for ATI cards.
Generally speaking, if you have about x700 or x800, you can use the ATI (open source) driver for almost everything.
I have a an ATI x700 and my experience is that it works great with ATI open source driver everything except Warcraft III under wine. It also performs about 7-11% worse. If you game, it will pay to use the FGLRX driver. The main downside is that if you want beryl you'll have to use XGL and AIGLX doesn't work with ati on FGLRX (it does on ATI with ATI). 

So really, if you game, probably want FGLRX. Else, it might make your life easier just to stick with ATI (open source) driver.

---

### Post by cisforcojo on 2007-05-29
I had MASSIVE gaming issues until I switched to fglrx so I'd definitely recommend it.

---

### Post by Sammi on 2007-05-29
If you're serious about Ubuntu/Linux then get a Nvidia next time. ATI haven't made stable Linux drivers yet :(

---

### Post by eye208 on 2007-05-29
Ubuntu's ATI driver is perfectly stable and very easy to install. I use it for gaming and working with Blender every day.

Beryl, on the other hand, is *not* stable. That's why it is not enabled by default. If wobbly Windows are more important to you than 3D performance, stick with the open source Radeon driver.

---

### Post by Rogers on 2007-05-29
FGLRX is the only viable gaming solution.  The open source driver is a good effort but not viable for fragging/leveling.

---

### Post by freefromXP on 2007-05-29
Thanks I will change to ATI drivers.  

   SO here is my Question  I installed asn set up everything from [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

  DO i need to uninstall or undo anything.  I was going to use ENVY to install ATI drivers but didn't know if I need to undo or rmv any drivers or anything first.   

 DO I enable FGLRX or will it get enabled when I install new drivers ?

---

### Post by eye208 on 2007-05-30
I recommend using Ubuntu's restricted drivers manager to install the ATI driver. It worked fine for me.

You can test drive the installation using the Ubuntu Live CD as pointed out here:
[http://ubuntuforums.org/showpost.php?p=2747227&postcount=6](http://ubuntuforums.org/showpost.php?p=2747227&postcount=6)
This will also give you a "clean" xorg.conf file to work with, undoing all previous changes that might conflict with the new driver.

---

### Post by cisforcojo on 2007-05-30
Second the restricted drivers motion. I just did the switch you're doing without incident.
(Don't need to uninstall anything)

System -> Administration -> Restricted Drivers Manager

---

### Post by freefromXP on 2007-05-30
So if I read this right after I get the new Xorg.conf saved to my hard drive I reboot from my HD put in new Xorg.conf then restartX  and install the drivers the same way I did on live Cd?

---

### Post by freefromXP on 2007-05-31
I obviuosly screwed up.  I followed steps above and I could not get the new xorg.conf file on my /etc/X11 while on live CD.  So I restarted machine and copy it over once I was in the I restarted X and now it will not boot problem with xorg.conf. I can login in at black screen.  

  I did copy my original xorg.conf file to one of my partions to save a copy of it but I don't knwo the path to get to once I log in to non gui to move it to my /etc/X11.  

 I already "sudo rm /etc/X11/xorg.conf"    No just need to mv good one over but don't know how to find path. or how to save it there while on live CD

---

### Post by acoustibop on 2007-05-31
I'm using an ATI 9800 GT and, while I have tried several times and several 'fixes' (see the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page")), I've been unable to install the current fglrx 8.36.5 driver successfully.  However, on installing an fglrx driver with the Restricted Drivers Manager, it installed the 8.34.8 driver with no fuss; I simply enabled the driver, rebooted and that was it.  fglrxinfo gets me:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.0.6334 (8.34.8)

Works fine and I didn't even need to edit anything in xorg.conf.  There seems to be a problem in the present fglrx driver with XOrg 7.0 or higher, though.  Maybe the next one will work.

---

### Post by PandaGoat on 2007-05-31
Go to System->Administration->Restricted Drivers.  When it opens, check enabled.  It will download and install fglrx allowing you to take advantage of 3d[hardware] acceleration that your graphics card allows, and most games need.

If it appears already checked run this command and reopen System->Administration->Restricted Drivers
```
sudo apt-get remove fglrx
```

---

### Post by eye208 on 2007-05-31
> **freefromXP said:**
> I obviuosly screwed up.  I followed steps above and I could not get the new xorg.conf file on my /etc/X11 while on live CD.  So I restarted machine and copy it over once I was in the I restarted X and now it will not boot problem with xorg.conf. I can login in at black screen.
To get X running again, login at the console, then enter "sudo dpkg-reconfigure xserver-xorg". Skip automatic detection of the graphics card, choose driver "vesa", make sure the list of resolutions is supported by your monitor, leave everything else at default. When you're done with configuration, enter "startx". This should bring up the graphical desktop again. Use the restricted drivers manager to install fglrx, then reboot.

---

### Post by freefromXP on 2007-05-31
Thanks I got it back up and running.

    Will the restricted drivers work with XGL, beryl

---

### Post by voidmage on 2007-05-31
Even though you seem to have gotten it running, if anything does not work as expected, try running these commands. If purging fglrx fails (since it's already removed), you can remove the config files under the "residual  config files" section in synaptic. The second restores a library fglrx replaced when you installed it.
```

sudo apt-get --purge remove xorg-driver-fglrx
sudo apt-get --reinstall install libglu1-mesa

```

---

### Post by freefromXP on 2007-05-31
Thanks to clerify

   
   I had beryl wroking great on AIGLX but could not play any gmaes.  I installed restricted drivers and now games (ut2004 linux install) play great but no beryl,  I have not yet install XGL.  Beryl is still installed but does nto work.  I am tyring to get beryl to work and still be able to play a  couple games.

---

### Post by sloggerkhan on 2007-05-31
What I do is have seperate sessions for fglrx and fglrx+xgl

If I want games, I use fglrx, if I want beryl, I use fglrx+xgl.

---

### Post by Sammi on 2007-06-01
> **sloggerkhan said:**
> What I do is have seperate sessions for fglrx and fglrx+xgl

If I want games, I use fglrx, if I want beryl, I use fglrx+xgl.
Between friends:
- How's your ATI card?
- It's complicated...

---

### Post by eye208 on 2007-06-01
> **Sammi said:**
> Between friends:
- How's your ATI card?
- It's complicated...
You wouldn't want to run games on a Beryl-enhanced X desktop, even if your card was an Nvidia one.

---

### Post by freefromXP on 2007-06-01
I want to thank everyone for their great inputs and oppions.  I tried and configured my system several ways and I learned a lot.  I figured the best way to really learn linux and how it works is to just get in a experiment and try new things.

  This is what I did to let everyone know.  

**1**. Install Beryl using AIGLX and Beryl looked and ran great.

    If you use a ATI card and want a really smooth looking and running system with Beryl I recommend this way.  Really easy set up and runs great.  
    This is guide I used [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

**2.** Then I went a changed over to the newest ATI drivers using ENVY and games play great. UT2004, etc..
 [http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/]("http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/")
  
   If you are just getting started and want and easy way to install and uninstall Nvidia/ATI drivers to play games and dont' care about, Beryl etc then this is quick and easy way to get good drivers installed.   

**3**. I follwed **eye208's** suggestion-  and followed this guide to install restricted drivers. System ran good and games played with out a hitch.  
[http://ubuntuforums.org/showpost.php?p=2747227&postcount=6]("http://ubuntuforums.org/showpost.php?p=2747227&postcount=6")
   
**4**  I then install Beryl with FGLRX/XGL using this guide.  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")
 
   It worked and I got Beryl installed with FGLRX and XGL. I wasn't has happy with this perfromance as I was with AIGLX.  It did work and I had seperate sessions for gaming.  Gaming was fine but just not real happy with the way Beryl ran.

     I know pretty much everyone told what I came to on my own.  I just had to try deifferent ways and make my own oppion.

  Finally I decided I don't play games a lot so I  wiped HD and made a dual boot system for gaming and I installed fiesty the first way I had it step 1. (yes back to where I started.) System is running great with Beryl and I couldnt' be happier.
 
   

    I want to thank everyone for thier advice and help.;) I like doing and undoing things cause thats how I think I can really understand Linux.  I learned alot from this and to all new user dont' be afraid to get in and try things out.:p

   I am sure I will be back when I screw things up trying something else new. :D


If you are new and don't like spending hours redoing your system listen to these guys.  I just want to experiment and learn things the hard way. :)

---

### Post by sloggerkhan on 2007-06-02
I think most of us have done the some sort of tinkering you did at some point.

---


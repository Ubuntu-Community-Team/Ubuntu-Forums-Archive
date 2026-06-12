---
title: "Running Beryl with x1700 ATI Graphics Card"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by mattmarq on 2007-06-25
I just got an F3Jp ASUS notebook with an ATI Mobility x1700 Graphics Card. I am wondering if anyone knows if it is possible to run Beryl and Desktop Effects with it????

Should i go the XGL root? or is there another way?

---

### Post by jtraub on 2007-06-25
No, for latest ATi cards XGL is only way to get Beryl/Compiz

---

### Post by haden9 on 2007-06-25
Hello there, I would just like to provide some useful websites that helped out a lot, I have an ATI X1400 and I used the latest ATI drivers to get XGL and Beryl working altogether.

For the installation of Ubuntu Feisty:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

For the video card driver installation and additional configuration commands:

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
(In the link above it features out dated ATI drivers, please disregard and use version 8.37.6)

and finally for Beryl and the Emerald theme manager:

[http://wiki.beryl-project.org/wiki/I...FORE_BEGINNING](http://wiki.beryl-project.org/wiki/I...FORE_BEGINNING)

I hope it works out for you as it did for me, good luck!!!!

---

### Post by mattmarq on 2007-06-27
Thank you Haden 9... the second link of the three you posted doesnt seem to go anywhere.... How do i get XGL set up for my x1700 once fglrx,

xorg.conf



Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

---

### Post by Crusher16 on 2007-08-16
> **haden9 said:**
> Hello there, I would just like to provide some useful websites that helped out a lot, I have an ATI X1400 and I used the latest ATI drivers to get XGL and Beryl working altogether.

For the installation of Ubuntu Feisty:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

For the video card driver installation and additional configuration commands:

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
(In the link above it features out dated ATI drivers, please disregard and use version 8.37.6)

and finally for Beryl and the Emerald theme manager:

[http://wiki.beryl-project.org/wiki/I...FORE_BEGINNING](http://wiki.beryl-project.org/wiki/I...FORE_BEGINNING)

I hope it works out for you as it did for me, good luck!!!!

Could you please correct the Wiki Link? 

I too have a F3Jp and want to get Beryl working on it.

---

### Post by Klayy on 2007-08-18
> **mattmarq said:**
> I just got an F3Jp ASUS notebook with an ATI Mobility x1700 Graphics Card. I am wondering if anyone knows if it is possible to run Beryl and Desktop Effects with it????

Should i go the XGL root? or is there another way?

It IS possible, I have that same laptop, it works in Sabayon linux 3.3 x64 (both cd and dvd)

but I didn't have much luck with ubuntu, and I've tried about every guide on the internet

---

### Post by burito on 2007-09-03
I have a F3JP, and allow me to put to rest your fears, for I have got it working.

Ensure your fglrx is working nicely with flgrxinfo, it should look like this...
burito@burito:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6747 (8.40.4)

The easy way to get it going is to use ENVY, available here...
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Envy will tell you that our chip is not supported, don't worry, tell it to do a manual install, luckily, manual install is very automatic. Test it with fglrxinfo, and then a quick run of glxgears, ~3600fps is what you should expect. If you get 60, vsync is on :-)

Now, install XGL following any guide that takes your fancy, for example...
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
I have used several guides on setting up XGL, and all have had total success. It appears to have quite a bit of lee way with our particular chips at least.

Now, in your /etc/X11/xorg.conf, there are a few gotcha's...

Section "Device"
	Identifier	"Generic Video Card"
	Driver	"fglrx"
	Option	"OpenGLOverlay" "off"
	Option	"UseFastTLS" "2"
	BusID		"PCI:1:0:0"
EndSection

Make sure your device section has at least those options. UseFastTLS 2 is optional, and while it does reduce speed (I can't notice it) according to ATI it increases stability, in particular with WINE, which is very noticable.
X will boot without turning off OpenGLOverlay, but the screen will be garbled almost beyond recognition.

Also ensure that you have these at the end of your xorg.conf...

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Now, remove your existing compiz/beryl install, and then add Trevino's repository, and install his magical builds. The line describing his repo for apt/synaptic is...

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

There is a command to install his GPG key, to get rid of those annoying "cannot be authenticated" messages in apt/synaptic, IIRC its on Trevino's site. I recommend finding a guide explaining specifically what packages to install. I've written this to detail the steps needed to make it happy on an F3JP. Taking into account these points, you can follow pretty much any guide to setting up compiz fusion. And if you've decided to rough it with only my guide, "compiz --replace" in a terminal or in your session startup will give you the magic.

One final point to be aware of, the fglrx drivers are not capable of running XGL and OpenGL app's at the same time. Screensavers and glxgears will work, but OpenArena, Nexuiz, or any other game will have corrupt textures. Also the ATI Control Panel will not work under XGL, so you will need to get very well acquainted with your xorg.conf if you want multiple monitors.

Other than that, enjoy!

---

### Post by Crusher16 on 2007-09-12
Cool. Thanks for the info! I'll mess around with it this weekend.

---

### Post by lcadwell on 2007-09-13
Hi, I have an Asus F3JP with ati x1700 and couldnt get the display to work properly when installing Feisty Fawn 7.04. I either just got dumped to text or if I installed fglrx it froze on a black screen. Here is how I solved it:

When attempting to install the desktop CD, it reports it cant start x. 

Type
> sudo pico /etc/X11/xorg.conf

Now find the following sections and make sure they look like this:

> Section "Device"
        Identifier      "Generic Video Card"
        Driver  "vesa"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-72
        Vertrefresh     43-60
EndSection


Now write the file with ctrl and the O key. Then ctrl and X to exit.

Now type startx and enter.

That should start the installation or you can just install with the alternate cd in text mode. When its installed, either install the fglrx driver though the synaptic package manager or through the terminal with:

> sudo apt-get install xorg-driver-fglrx
Followed by
> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Note the captial X!

Now type
> sudo /etc/X11/xorg.conf
Find the section called Screen and change the default depth from 16 to 24. Then save the file with ctrl o and then ctrl x.
Use
> start x
to start the xserver and that should hopefully be working. If not, it&#347; probably my fault because Im typing this all from memory. Please let me know if it works or if there are any errors in my solution.

Others have posted guide to enable 3d acceleration and beryl. I will try those now and see if they work, if not, I will post back here with solution if possible.

Cheers

Cheers

---

### Post by Crusher16 on 2007-09-13
> **lcadwell said:**
> Hi, I have an Asus F3JP with ati x1700 and couldnt get the display to work properly when installing Feisty Fawn 7.04. I either just got dumped to text or if I installed fglrx it froze on a black screen. Here is how I solved it:

When attempting to install the desktop CD, it reports it cant start x. 

Type


Now find the following sections and make sure they look like this:



Now write the file with ctrl and the O key. Then ctrl and X to exit.

Now type startx and enter.

That should start the installation or you can just install with the alternate cd in text mode. When its installed, either install the fglrx driver though the synaptic package manager or through the terminal with:


Followed by

Note the captial X!

Now type

Find the section called Screen and change the default depth from 16 to 24. Then save the file with ctrl o and then ctrl x.
Use

to start the xserver and that should hopefully be working. If not, it&#347; probably my fault because Im typing this all from memory. Please let me know if it works or if there are any errors in my solution.

Others have posted guide to enable 3d acceleration and beryl. I will try those now and see if they work, if not, I will post back here with solution if possible.

Cheers

Cheers

Alright. Keep us updated please.

---

### Post by lcadwell on 2007-09-14
Well, that's it. Beryl and compiz running smoothly!!

i did have to play around with it for a while. I used edgy to install ATI's drivers but then I went back to the restricted driver manager.

After installing xgl using the guide above, I could log in to xgl but had corrupted graphics. So I used ctrl-alt-backspace to restart the xserver and log back in. Then the graphics were fine. I seems you have to do this every boot up but I'll try to find a fix for it.

I tried to install beryl using the synaptic package manager. It installed but I couldn't see the cube and window titlebars didn't display. I uninstalled it and then tried again with a different version of compiz (apparently the wrong one), my graphics slowed down to a crawl but the titlebars showed however it crashed when I clicked on them. 

Next I went to trevino's feisty sources page [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")
and typed 
> sudo gedit /etc/apt/sources.list
and pasted his sources into that. Saved it and then open synaptic and clicked "Edit", "Reload package information". It complained about a couple of keys, I added a few using the instructions included with the page. I then reloaded the list again.

Here's my log from the synaptic package manager from that point onwards:

Commit Log for Fri Sep 14 18:18:06 2007

Completely removed the following packages:
beryl
beryl-core
beryl-manager
beryl-plugins-data
beryl-settings-bindings
emerald
libberyldecoration0
libberylsettings0

Removed the following packages:
beryl-plugins
beryl-settings
beryl-ubuntu
emerald-themes
heliodor
libberylsettings0-gconf
libemeraldengine0

Commit Log for Fri Sep 14 18:22:40 2007


Completely removed the following packages:
compiz
compiz-core
compiz-gnome
libdecoration0

Removed the following packages:
compiz-plugins
desktop-effects
ubuntu-desktop

Commit Log for Fri Sep 14 19:05:25 2007


Installed the following packages:
beryl (0.2.1.dfsg+git20070318-0ubuntu2)
beryl-core (0.2.1.dfsg+git20070318-0ubuntu2)
beryl-plugins (0.2.1-0ubuntu2)
beryl-plugins-data (0.2.1-0ubuntu2)
beryl-settings (0.2.1-0ubuntu1)
beryl-settings-bindings (0.2.1-0ubuntu1)
emerald (0.5.2~git20070911+jbs1)
libberyldecoration0 (0.2.1.dfsg+git20070318-0ubuntu2)
libberylsettings0 (0.2.1.dfsg+git20070318-0ubuntu2)
libdecoration0 (1:0.5.5~git20070911+jbs1)
libemeraldengine0 (0.5.2~git20070911+jbs1)

Commit Log for Fri Sep 14 19:17:21 2007


Installed the following packages:
beryl-manager (0.2.1-0ubuntu1)

Commit Log for Fri Sep 14 20:31:48 2007


Upgraded the following packages:
app-install-data-commercial (7.2) to 7.3
beryl-plugins-data (0.2.1-0ubuntu2) to 0.3.0+git20070404~3v1ubuntu4
cdrecord (9:1.1.2-1) to 9:1.1.2-1ubuntu1
genisoimage (9:1.1.2-1) to 9:1.1.2-1ubuntu1
gimp-python (2.2.13-1ubuntu4.3) to 2.2.13-1ubuntu4.4
gnome-accessibility-themes (2.18.1-0ubuntu1) to 2.19.90-0ubuntu1~pollycoke1
gnome-btdownload (0.0.25-1ubuntu1) to 0.0.28-1~feisty1
gnome-media (2.18.0-0ubuntu1) to 2.18.0-0ubuntu1.1
gnome-media-common (2.18.0-0ubuntu1) to 2.18.0-0ubuntu1.1
gnome-themes (2.18.1-0ubuntu1) to 2.19.90-0ubuntu1~pollycoke1
gpgv (1.4.6-1ubuntu2) to 1.4.6-2ubuntu3~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
lftp (3.5.6-1build1) to 3.5.11-1~feisty1
libgimp2.0 (2.2.13-1ubuntu4.3) to 2.2.13-1ubuntu4.4
libgnome-media0 (2.18.0-0ubuntu1) to 2.18.0-0ubuntu1.1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libnautilus-burn4 (2.18.1-0ubuntu1) to 2.18.1-0ubuntu1.1
libportaudio0 (18.1-4) to 18.1-7~feisty.4477
libpt-1.10.0 (1.10.3-0ubuntu1) to 1.10.7~dfsg1-5~feisty.4490
libpt-plugins-alsa (1.10.3-0ubuntu1) to 1.10.7~dfsg1-5~feisty.4490
libpt-plugins-v4l (1.10.3-0ubuntu1) to 1.10.7~dfsg1-5~feisty.4490
libpt-plugins-v4l2 (1.10.3-0ubuntu1) to 1.10.7~dfsg1-5~feisty.4490
libspeex1 (1.1.12-3) to 1.2~beta2-3~feisty.4110
mkisofs (9:1.1.2-1) to 9:1.1.2-1ubuntu1
nautilus-cd-burner (2.18.1-0ubuntu1) to 2.18.1-0ubuntu1.1
shared-mime-info (0.20-0ubuntu4) to 0.21-1
tango-icon-theme (0.7.2+cvs07.02.06-0ubuntu1) to 0.8.0~cvs070515-0ubuntu1~pollycoke1
thunderbird-locale-en-gb (1:1.5.0.10ubuntu0-1) to 1:2.0.0.0+1-0ubuntu1~feisty1
vino (2.18.1-0ubuntu1) to 2.18.1-0ubuntu1.1
wodim (9:1.1.2-1) to 9:1.1.2-1ubuntu1

Commit Log for Fri Sep 14 21:09:12 2007


Installed the following packages:
compiz (1:0.5.5~git20070912+3v1ubuntu0)
compiz-core (1:0.5.5~git20070911+jbs1)
compiz-fusion-plugins-main (0.5.2~git20070912+jbs0)
compiz-gnome (1:0.5.5~git20070911+jbs1)
compiz-plugins (1:0.5.5~git20070911+jbs1)
desktop-effects (0.7.1-0ubuntu4)
gnome-compiz-manager (0.10.3-0ubuntu1)
libcompizconfig0 (0.5.2~git20070909+jbs1)
libgnome-compiz-manager0 (0.10.3-0ubuntu1)


So that's it. There's probably a couple of redundant steps in there but, to summarize:

[LIST]
[*]Install ATI drivers
[*]Install XGL and add script files (using ctrl-alt-backspace to restart X)
[*]Update sources list
[*]Install beryl and compiz
[/LIST]

If it doesn't work properly, try completely uinstalling beryl and compiz and reinstalling them. Failing that, double check you've got the right ati driver running.

Cheers

---


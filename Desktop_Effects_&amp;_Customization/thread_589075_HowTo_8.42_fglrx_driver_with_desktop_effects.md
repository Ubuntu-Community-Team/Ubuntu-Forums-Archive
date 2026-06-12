---
title: "HowTo: 8.42 fglrx driver with desktop effects"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by angryfirelord on 2007-10-23
First, grab it from here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")
***For 64-bit users:*** Grab this package as well:
[http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2]("http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2")

Next, run:
```
sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/7.10
```
***For 64-bit Users***
For 32-bit, the debs should build fine, but on my 64-bit machine, they failed to do so at first.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325]("https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325")
> For those with Ubuntu 64-bit problems, below is a link to the updated Ubuntu packaging scripts done by Aric Cyr, which will be found in fglrx 8.43 (along with other updates I imagine). It fixes the 64-bit problem.

[http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2](http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2)

Extract it to /etc/ati/custom-package and then with the 8.42 package run --buildpkg custom-package/7.10 (or 7.04 for Feisty)
Basically, when you exact the tarball, you must create an /etc/ati/custom-package directory first. Then, move the contents of the Ubuntu folder from the extracted tarball (but not the Ubuntu folder itself) into the custom-package folder. *whew* I hope I made that clear enough. Then, cd back into the folder where the ati installer is and run it again like this:
```
sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg custom-package/7.10
```
The next steps can be taken from here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually")

Ok, so after you've done that, run **fglrxinfo** in a terminal. If you get "mesa" for whatever reason, then re-run these commands:
```
sudo depmod -a
```
```
sudo mkdir /lib/modules/$(uname -r)/volatile
```
```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```
Reboot and the proper modules should be loaded.

Now, the exciting part, AIGLX! 3D should be working, so now open up your xorg.conf and add this stuff:
Change Option "Composite" to say:
```
Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```
Under Section "ServerLayout", add this:
```
Option "AIGLX" "True"
```
Save it and then open up this:
```
sudo nano /etc/xdg/compiz/compiz-manager
```
Add the following:
```
WHITELIST="fglrx"
```

Restart X and now you should have desktop effects!

If that doesn't work, then try this:
[QUOTE=rbmorse]open a root permission text editor and open

/usr/bin/compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add

fglrx

to the end of the line of drivers, inside the close quote mark.

Check the next section to make sure your card is not blacklisted.[/QUOTE]

If I made a mistake anywhere or if I wasn't clear in a certain spot, please let me know. Hopefully fglrx won't be a pain in the butt anymore when the updated driver hits the repository.

---

### Post by djuniah on 2007-10-23
Used this guide and it severely crippled my system.  I'm running a mobility radeon 200m.  I had the default compiz that comes with gutsy running flawlessly with whatever the default was.  I had installed the config app and added the cube and some other things, but i still got a REALLY nice frame rate.  Then i figured i should upgrade to these new supposedly amazing drivers, but now the system run VERY slowly.  Like 1 frame every 3 seconds slowly.  However when typing this message and doing non-composite related tasks it runs at normal speed.  Also, when i try to run fglrxinfo X restarts itself before printing anything.  The first time i tried it right after the install i did get those weird messages mentioned in the above post, but now i cant even get it to do that.  Any ideas why this might be?

p.s. if there is no apparent way to fix this, how can i roll back the driver to whatever the default gutsy install used?

UPDATE: after trying a few things i think i got it installed.  fglrxinfo now shows:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

```

but after following the final steps in the guide, i still can not enable compositing.  In the desktop effects menu i select "custom" like i had it before, and it just throws an error after a few seconds saying that it could not be enabled.  Any idea why this is?

---

### Post by Alarictric on 2007-10-24
angryfirelord:  i followed that method and i am still unable to get desktop effects running. I still get the error: "Desktop effects could not be enabled"

I'm a running 32 bit Gutsy on a 64 bit proc, ATI X800XT with a LCD using DVI.
Is anybody able to help?

---

### Post by davim on 2007-10-24
Don't forget that if you had XGL previously enabled you need to disable it.

to disable Xgl:

```

mkdir ~/.config/xserver-xgl

``` 

```

touch ~/.config/xserver-xgl/disable

```

---

### Post by changty on 2007-10-24
Warning: /etc/ati/custom-package/ati-packager.sh is missing or not a script.
The distribution 'custom-package' is not supported
Removing temporary directory: fglrx-install.Qt8634


What is this? :O I have succesfully installed previous drivers, also these too, but in a different way. I was using the manuall install guide back then.
Doh, im an idiot, i don't have a 64bit system :)

Next problem: 

My X keeps crashing if i try fglrx or glxinfo. 
lsmod | grep fglrx
fglrx                1415660  0 
agpgart                35016  2 intel_agp,fglrx

dmesg
[  155.044000] [fglrx] PCIe has already been initialized. Reinitializing ...
[  155.080000] [fglrx:firegl_unlock] *ERROR* Process 6090 using kernel context 0

---

### Post by Mosse on 2007-10-24
Warning: /etc/ati/custom-package/ati-packager.sh is missing or not a script.
The distribution 'custom-package' is not supported
EDIT: Ah Yeah, I missread the moving part, you should move the contents of the packages/Ubuntu/ to custom-package/

I got the driver installed now and CCC load s and everything but I still get "Mesa" in fglrxinfo...

The step when you do:
```
sudo mkdir /lib/modules/$(uname -r)/volatile
```
I had that dir from the start and this is a fresh install of ubuntu...
anyway so that part doesnt work, dir exsist error...
and:
```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```
this work and creates a symbolic link to fglrx.ko in the volatile dir, but after a reboot its gone :confused:

EDIT2: hmm.. whatever I do to that folder volatile it resets after each boot...

---

### Post by zsouthboy on 2007-10-24
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.KI8534

:(

---

### Post by qbein on 2007-10-24
Looks like you're missing the debhelper package. Try:

sudo apt-get install debhelper

---

### Post by rbmorse on 2007-10-24
> **Alarictric said:**
> angryfirelord:  i followed that method and i am still unable to get desktop effects running. I still get the error: "Desktop effects could not be enabled"

I'm a running 32 bit Gutsy on a 64 bit proc, ATI X800XT with a LCD using DVI.
Is anybody able to help?

open a root permission text editor and open 

/usr/bin//compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is not blacklisted.

---

### Post by adam on 2007-10-24
You have to extract the *contents* of the **ubuntu** folder to the custom-package directory.

That said, I've done that, it installed correctly, and I still can't get it working. Enabling the fglrx driver causes me to boot to a black screen. I then have to reboot into recovery and manually edit xorg.conf to enable the radeon driver and reboot.

---

### Post by Neo4 on 2007-10-24
with this driver the efects are very slow!

---

### Post by ubuntu dave on 2007-10-24
> **zsouthboy said:**
> cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.KI8534

:(

That error is the error you get if you don't follow the extra instructions for the 64bit package 'fix' posted by in the OP. Follow the instructions correctly to solve the problem.

---

### Post by ubuntu dave on 2007-10-24
> **Mosse said:**
> Warning: /etc/ati/custom-package/ati-packager.sh is missing or not a script.
The distribution 'custom-package' is not supported

I get this also and I am on a 64 system,

I have exracted the "package" dir to /ect/ati/custom-package/
like this if i am gonna find the "gutsy" folder i go /ect/ati/custom-package/package/Ubuntu/dists/gutsy/ 
is this the way it is suppose to be?

I have the installer in my home dir if that is any diffrence

If you explore the 'fix' package posted you should be able to figure out how to extract the files correctly to fix the problem. The instructions aren't clear, you shouldn't simply extract the 'fix' package to /etc/ati/custom-profile - you should extract simply which part you need from the fix package. Explore it a little and it should be obvious what to unzip where. (roughly: within the 'Ubuntu' folder of the 'fix package' you downloaded is ati-packager.sh ....)

---

### Post by rcamanda on 2007-10-24
Will this work for a clean install?

---

### Post by Alarictric on 2007-10-24
> **rbmorse said:**
> open a root permission text editor and open 

/usr/bin//compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is not blacklisted.

that works, thanks a bunch.

Now i have an issue where i cant see videos in Totem, Mplayer, or VLC.  if i turn off the effects, i can see videos fine, its only when the effects are running.

i can hear the audio perfectly fine, and occasionally a frame will flash up in the video window, especially while moving the window.

---

### Post by angryfirelord on 2007-10-24
[QUOTE=rbmorse]open a root permission text editor and open 

/usr/bin//compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is not blacklisted.[/QUOTE]
Thanks for pointing that out! I added it to my original post.

Yeah, sorry for the custom-package mixup. You have to dump the contents of the Ubuntu folder in there, but don't actually put the Ubuntu folder itself inside of it. Otherwise, the ATI installer doesn't know where to look for the script.
[QUOTE=Mosse]Warning: /etc/ati/custom-package/ati-packager.sh is missing or not a script.
The distribution 'custom-package' is not supported
EDIT: Ah Yeah, I missread the moving part, you should move the contents of the packages/Ubuntu/ to custom-package/

I got the driver installed now and CCC load s and everything but I still get "Mesa" in fglrxinfo...

The step when you do:
Code:
sudo mkdir /lib/modules/$(uname -r)/volatile
I had that dir from the start and this is a fresh install of ubuntu...
anyway so that part doesnt work, dir exsist error...
and:
Code:
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
this work and creates a symbolic link to fglrx.ko in the volatile dir, but after a reboot its gone 

EDIT2: hmm.. whatever I do to that folder volatile it resets after each boot...[/QUOTE]
Run **sudo depmod -a** first, then run the other 2 commands.
[QUOTE=Alarictric]Now i have an issue where i cant see videos in Totem, Mplayer, or VLC. if i turn off the effects, i can see videos fine, its only when the effects are running.[/QUOTE]
That's probably a bug with Compiz-Fusion itself since both C-F & the media player are figting for 3D usage. Try this link: [http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/]("http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/")

Oh and thanks for the other posters who helped with answers!

---

### Post by rcamanda on 2007-10-25
Will these instructions work with a clean install?  If not could someone direct me to a thread for installing this ati driver after a clean install?

---

### Post by Mosse on 2007-10-25
> **angryfirelord said:**
> 

Run **sudo depmod -a** first, then run the other 2 commands.



Yeah was was doing that aswell, but didnt got it to work...
So I installed a new fresh install of 7.10 64bit and first thing I removed all the old drivers then installed like the guide...

all worked out fine and the Volatile folder wasnt there now so I could be created, I was also able to make the link and after a reboot it was still there... but still fglrxinfo says "Mesa"

when I try to rerun the steps now first command goes fine, second and third is now "file exist" and "file exist" since they where created before... and I dont know what to do now...
```
matte@matte-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

matte@matte-desktop:~$ sudo depmod -a
[sudo] password for matte:
matte@matte-desktop:~$ sudo mkdir /lib/modules/$(uname -r)/volatile
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists
matte@matte-desktop:~$ sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/volatile/fglrx.ko' to `/lib/modules/2.6.22-14-generic/misc/fglrx.ko': File exists
```

---

### Post by angryfirelord on 2007-10-25
> **Mosse said:**
> Yeah was was doing that aswell, but didnt got it to work...
So I installed a new fresh install of 7.10 64bit and first thing I removed all the old drivers then installed like the guide...

all worked out fine and the Volatile folder wasnt there now so I could be created, I was also able to make the link and after a reboot it was still there... but still fglrxinfo says "Mesa"

when I try to rerun the steps now first command goes fine, second and third is now "file exist" and "file exist" since they where created before... and I dont know what to do now...
```
matte@matte-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

matte@matte-desktop:~$ sudo depmod -a
[sudo] password for matte:
matte@matte-desktop:~$ sudo mkdir /lib/modules/$(uname -r)/volatile
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists
matte@matte-desktop:~$ sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/volatile/fglrx.ko' to `/lib/modules/2.6.22-14-generic/misc/fglrx.ko': File exists
```
Hmm, did you remember to initialize the driver afterwards? Make sure your xorg.conf has fglrx for a driver, then:
```
sudo aticonfig --initial
```
```
sudo aticonfig --overlay-type=Xv
```

---

### Post by Mosse on 2007-10-25
> **angryfirelord said:**
> Hmm, did you remember to initialize the driver afterwards? Make sure your xorg.conf has fglrx for a driver, then:
```
sudo aticonfig --initial
```
```
sudo aticonfig --overlay-type=Xv
```

yes I did, and I got it as driver on one of the "device"
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

but on the other one its "vesa" is that maybe the problem?

here is my whole xorg.conf
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "P70"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "P70"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
 
```

---

### Post by angryfirelord on 2007-10-25
Wow Mosse, I've never seen it do that before. In that case, simply delete this section:
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection
```
X will always pick whatever comes first in the xorg.conf file, so in this case, it's loading the vesa driver rather than the fglrx driver.

Now, in th event that *still* doesn't work, run this command (remember to select fglrx as your driver):
```
sudo dpkg-reconfigure xserver-xorg
```
Then run those aticonfig commands again.

---

### Post by Mosse on 2007-10-25
> **angryfirelord said:**
> Wow Mosse, I've never seen it do that before. In that case, simply delete this section:
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection
```
X will always pick whatever comes first in the xorg.conf file, so in this case, it's loading the vesa driver rather than the fglrx driver.

Now, in th event that *still* doesn't work, run this command (remember to select fglrx as your driver):
```
sudo dpkg-reconfigure xserver-xorg
```
Then run those aticonfig commands again.

dont know what to say, When I deleted the code it failed to see what card I had so it wanted to boot into low ress mode,
so thats no good

did:
```
sudo dpkg-reconfigure xserver-xorg
```
next and completed it, rebooted and did the aticonfig commands
```
matte@matte-desktop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
matte@matte-desktop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3
matte@matte-desktop:~$ 

```

and after a reboot fglrx still show me Mesa

here is how my xorg.conf is looking now
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "P70"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI RADEON X1950"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X1950"
	Monitor    "P70"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

ANyway it seams like ubuntu 64 got big problems with my card (ASUS X1950pro), a bit strange but I am not that good at linux. Strange thing is that amdcccle did see what card I have and clocks and so on...

Well I am downloading Ubuntu 32bit now and is going to see if it work there...

---

### Post by angryfirelord on 2007-10-25
Ok, but before you do that, see if the module is loaded:
```
sudo modprobe -l | grep fglrx
```

---

### Post by Mosse on 2007-10-25
> **angryfirelord said:**
> Ok, but before you do that, see if the module is loaded:
```
sudo modprobe -l | grep fglrx
```
When I do that i get
```
matte@matte-desktop:~$ sudo modprobe -l | grep fglrx
/lib/modules/2.6.22-14-generic/misc/fglrx.ko
```

---

### Post by HaMMeReD on 2007-10-25
I've tried to install the driver and my xorg looks right and my monitor is set correctly, but when I do the modprobe -l | grep fglrx, it appears the module isn't loaded. Any ideas?

---

### Post by RavanH on 2007-10-25
> **rbmorse said:**
> open a root permission text editor and open 

/usr/bin//compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is not blacklisted.

WOW! Thanks you guys, the how-to with 64bit patch and the tip above finally made it work :) I am now without xserver-xgl and very happy ;)

TIP: I had to change the part below WHITELIST too -- as suggested. Apparantly, my Radeon Xpress 200M was hidden in those codes... Not knowing which one, I simply changed line 63 to 
```
BLACKLIST_PCIIDS=""
```

I am not planning on changing my laptop motherboard-integrated graphics soon ;) so I suppose this will not yield any dangers?

---

### Post by studo77 on 2007-10-26
I am using restricted drivers and xgl on my X1600. Should I disable restricted drivers before doing this, or not? Does it matter?

Shure would be nice to loose xgl on the desktop.

---

### Post by aldeby on 2007-10-26
angryfirelord, thankyou very much for your tutorial on these new drivers, 
unfortunately I also can't get rid of MESA OpenGL software emulation
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

and don't know how to get rid of mesa...
all setup steps completed successfully and also additional tips provided proved useless for me..

my device is 	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
attached is my xorg.conf

---

### Post by compwiz18 on 2007-10-26
> **RavanH said:**
> WOW! Thanks you guys, the how-to with 64bit patch and the tip above finally made it work :) I am now without xserver-xgl and very happy ;)

TIP: I had to change the part below WHITELIST too -- as suggested. Apparantly, my Radeon Xpress 200M was hidden in those codes... Not knowing which one, I simply changed line 63 to 
```
BLACKLIST_PCIIDS=""
```

I am not planning on changing my laptop motherboard-integrated graphics soon ;) so I suppose this will not yield any dangers?

Same thing over here, but it was easy to fix.

Now, however, Firefox is lagging when I scroll and the screensaver lags, but glxgears run just fine...

Any suggestions?

(btw, thanks for that 64bit patch, works like a charm)

---

### Post by ElbertF on 2007-10-26
Worked for me at the first try, thanks. :)

---

### Post by ricosrealm on 2007-10-26
Thanks for the HOW-TO!  DRI and AIGLX are enabled on my X700 ATI laptop.  However I can also confirm that firefox scrolling performance is very bad.  Everything worked much better with the old fglrx and XGL enabled in terms of performance.  Any thoughts on how to tweak this?

I can provide my xorg.0.log and xorg.conf if that helps for comparison sake.

---

### Post by jsully1 on 2007-10-26
Disabling compiz/desktop effects will speed your firefox scroll back to normal, so the driver is certainly capable of solid 2D performance.  I think we just need to hold off for a new release - they've been pumping them out so hopefully it won't take too long.

---

### Post by dustorm on 2007-10-28
> **Alarictric said:**
> that works, thanks a bunch.

Now i have an issue where i cant see videos in Totem, Mplayer, or VLC.  if i turn off the effects, i can see videos fine, its only when the effects are running.

i can hear the audio perfectly fine, and occasionally a frame will flash up in the video window, especially while moving the window.

I have the same issue, as well as some corruption when I run fglrx gears and some gl programs. Has anyone been able to resolve this? (I can see it working but the bottom half of the window has some black blocky corruption seems to disappears when the window is maximized.). 

Otherwise the compiz seems to work great.

- on an All-In-Wonder 9800 pro.

---

### Post by kshane on 2007-10-28
Hey!  *angryfirelord!*  ***_IT WORKS!!!_***

I almost bought a new video card, but couldn't afford the Nvidia I wanted, so in my frustration, I drank a twelve and sat down at the computer and **LO AND BEHOLD!**  I got the new driver to install!  And I followed your How-to just now and it works!  It's a little squirrlie, but it works!  

Thanks!

Kevin

---

### Post by opferstad on 2007-10-28
I guess I'm too much of a noob to understand this HowTo. I've got a Mobility Radeon x1300 and a completely fresh install of Ubuntu 7.10. Anyways, I want to try out some of the advanced desktop effects but I can't seem to get it working and it's getting a bit frustrating. Haven't activated the restricted driver for my graphics card yet as I've heard there's some problems with it.
I wish there was an easier way to do this.

---

### Post by kshane on 2007-10-29
> **opferstad said:**
> I guess I'm too much of a noob to understand this HowTo. I've got a Mobility Radeon x1300 and a completely fresh install of Ubuntu 7.10. Anyways, I want to try out some of the advanced desktop effects but I can't seem to get it working and it's getting a bit frustrating. Haven't activated the restricted driver for my graphics card yet as I've heard there's some problems with it.
I wish there was an easier way to do this.

Unfortunately, ATI has not been too awful supportive of Linux with their driver, however, it CAN be done, and it's not that hard if you have the right advice, etc.  I've only been using Linux (Ubuntu) as my primary desktop OS since the end of May of this year.  I finally just this week got it going how I want.  It's a little unstable, but that isn't Ubuntu, it's ATI, but, like I said it works!

Just get the new ATI driver, 8.42.3, installed and as stable as you can get it, then worry about Compiz or whatever frills you want to add.  The ATI driver was my biggest hang-up...

Kevin

---

### Post by mayo2000 on 2007-10-30
> **Mosse said:**
> ...
```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```
this work and creates a symbolic link to fglrx.ko in the volatile dir, but after a reboot its gone :confused:

EDIT2: hmm.. whatever I do to that folder volatile it resets after each boot...

Damn, I'am also affected by this. I had to create symlinks every reboot.

---

### Post by frankpolo on 2007-10-30
I am new to Ubuntu, but not computers so I understand the basics. I installed  Kubuntu as an extended partition as created a home partition, a swap partition and the root out of the extended partition. This will be my second time trying to get the desktop cube working with my ATI X1950 Pro. The first time I built the driver using the ati 8.43 instructions and fglrxinfo shows ATI as the driver and xorg shows fglrx under ATI. The open GL screensavers open up properly to. I can't remember the command but I ran the spinning gears in a cube test and it worked properly and quickly. I installed the compiz that is under add/remove programs but the desktop effects box is empty. I finally had to add compiz xserver-fgl. I could not get the cube to work and it disabled my hardware acceleration. Upon trying to get the cube to work last night my video got all jacked up and I ended up reinstalling Kubuntu during which I reformatted my extended partitions, so this is a new install. I built the ATI drivers and it came out as mesa. I followed another post in this forum and got my fglrx info to show my ATI card. I added the compiz from Add/Remove programs but it is still blank. I verified that open gl screen savers are working properly. Every article I look at says just installing compiz from add remove programs should get your cube running and enable all the effects. What do I need to do to get compiz installed properly and working with fglrx instead of xgl? Thanks for your time.

Frank

---

### Post by Ub1476 on 2007-10-30
Any way to remove this drivers?:lolflag:

---

### Post by flamarro on 2007-10-31
HI guys
just to say that i have a Acer Desktop T160 ( AMD 64 3700+ with ATI X1300 ) and the way i made it work was, with a fresh install of 7.10, the simple way was immediately install Envy, it installs now 8.42 driver, and the driver worked. Then change, like some said,  /etc/xdg/compiz/compiz-manager and added WHITELIST=”nvidia intel ati radeon i810 fglrx”.... It didn't work, couldn't have compiz working, only when i did this
> **rbmorse said:**
> open a root permission text editor and open 

/usr/bin//compiz

scroll down to around line 54 and look for the line that lists whitelisted drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is not blacklisted.
It worked....... So nice..... Like some said before, watching movies, in windows mode, it shows some corruption, but in full screen, plays fine. Other thing i have is Tv Out. When i installed the driver for the firs time, my monitor turned off :confused: but i knew that all was working, i could, blindly, put my user and password, hear the starting sound but no monitor.... I've unplugged the tv cable, restarted gdm and is the only way it works...... no tv OUT....
It's the nexrt chapter i think, now that all works, tv out doesn't..... starting to read this chapter now in this amazing book that is our forum.... :)

---

### Post by angryfirelord on 2007-10-31
[QUOTE=frankpolo]I installed the compiz that is under add/remove programs but the desktop effects box is empty. I finally had to add compiz xserver-fgl. I could not get the cube to work and it disabled my hardware acceleration. Upon trying to get the cube to work last night my video got all jacked up and I ended up reinstalling Kubuntu during which I reformatted my extended partitions, so this is a new install. I built the ATI drivers and it came out as mesa. I followed another post in this forum and got my fglrx info to show my ATI card. I added the compiz from Add/Remove programs but it is still blank. I verified that open gl screen savers are working properly. Every article I look at says just installing compiz from add remove programs should get your cube running and enable all the effects. What do I need to do to get compiz installed properly and working with fglrx instead of xgl? Thanks for your time.
[/QUOTE]
Are you using 7.10? It comes with compiz-fusion installed by default. All you need to do is right click in the desktop, select properties-->Visual Effects. Enable them. If nothing happens, then make sure your xorg has the composite & aiglx options enabled along with the fglrx driver in the whitelist for compiz-fusion.

Then, install compizconfig-settings-manager so you can enable the cube and other good stuff.
> Damn, I'am also affected by this. I had to create symlinks every reboot.
First, make sure that Ubuntu's default fglrx module is blacklisted. Otherwise it will replace your symlinks. Then, try running:
```
sudo depmod -a
```
```
sudo modprobe fglrx
```
The modprobe fglrx does the same thing as creating the symlinks.
> Hey! angryfirelord! IT WORKS!!!
Happy to hear that! :D

---

### Post by frankpolo on 2007-10-31
Firelord,

I did install 7.10. The composite and AIGLX options are enabled in my xorg. I have tried adding fglrx to my compiz file but my system isn't finding the compiz file. I do not see  visual effects under properties.

Frank

---

### Post by Brazilian Joe on 2007-11-01
I am on Kubuntu 7.10. I have followed the advice on this thread, glxinfo and fglrx tell me that fglrx is being used and in working order, 3D and all.
I have Composite enabled on extensions, and AIGLX on ServerLayout.

I have edited /etc/xdg/compiz/compiz-manager to add fglrx to the whitelist,
and even edited the compiz script to ad it by hand too.

Nevertheless, compiz is still not running.
I have an ATI Mobility x1600 (TravelMate 8210)

If I run compiz --replace & from the command line, I get:

```
compiz --replace &
[1] 7830
tfreire@rainforest:~$ Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

[1]+  Exit 1                  compiz --replace
```

---

### Post by Zakk Walid on 2007-11-02
well, the driver is ok, but i have problems with 3d. 
when i play a game or use google earth, i see black flashes. how can i fix that? ?
and movies dosent work. 
i opend a mvideo and the desktop effects were disabled S: 

tnx.

---

### Post by Zakk Walid on 2007-11-02
when i turn off the compiz desktop effects everything works gr8 
do some1 knows how to solve it?

---

### Post by Myron81 on 2007-11-02
bump

---

### Post by Myron81 on 2007-11-02
Same here using Mobility X1800.

When I was using XGL  the 2D performance is moderate, 3D full performance is extremely poor. 
(etc when watching screen saver list animation its ok, but when switching to full screen mode the 3D performance is very slow). No direct rendering method appears to be available.

Having removed server-XGL lib does resolve much issues,
When Desktop effects are disabled everything runs smoothly. Screen savers in window and full screen mode run extremely fast. Movies play fine, Firefox scrolling is fast etc.
However, when enabling desktop effects:

A) Watching movies is tricky.
You have to use X window system (No Xv) which is ok if you are watching movies in window mode but when switching to full screen watching movies is unbearable. 

B) 3D effects in full screen or windowed are flashing. The screen appears to be refreshing or just to blink every 2-3 seconds.

C) Mozilla scrolling is extremely slow.

I think the above summarize most ATI - users problems.

I've tried various settings on xorg.conf Device params such as:

	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option 	    "UseFastTLS" "2"
        Option     "XaaNoOffscreenPixmaps" "true"

Extensions composite enabled or disabled.

None of them did the trick. 

If anyone find a solution to the above issues please post to enlight us.

---

### Post by Digitallysick on 2007-11-02
cant get it to work =( 

Generating package: custom-package/7.10
./packages/custom-package/ati-packager.sh: 180: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.Z22031


ive created /etc/ati/custom-package

then extracted the file, opened the ubuntu folder and moved the contents to /etc/ati/custom-package,

---

### Post by RavanH on 2007-11-03
> **rbmorse said:**
> open a root permission text editor and open 

/usr/bin/compiz

scroll down to around line 54 and look for the line that lists **whitelisted** drivers and add 

fglrx

to the end of the line of drivers, inside the close quote mark. 

Check the next section to make sure your card is **not blacklisted**.

Pfff, I found that you have to re-do these two things after each compiz update !!! Soooo glad with this thread :) Thanks all.

AngryF, could you please insert this tip from rbmorse into your original how-to? Without it, it will not work for a lot of people...

---

### Post by diskotek on 2007-11-06
```
Created directory fglrx-install.c21575
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3
.....................................................................................
 ATI Technologies Linux Driver Installer/Packager 
==================================================
The distribution 'custom-package' is not supported
Removing temporary directory: fglrx-install.c21575

```

i got this error with my feisty box (with ati radeon x200 graphic card. any idea why?

---

### Post by angryfirelord on 2007-11-07
> **RavanH said:**
> AngryF, could you please insert this tip from rbmorse into your original how-to? Without it, it will not work for a lot of people...
Added. :) I would've done it sooner except I've been a little busy.
[QUOTE=diskotek]i got this error with my feisty box (with ati radeon x200 graphic card. any idea why?[/QUOTE]
First, make sure that folder is in */etc/ati/custom-package*. Next, make sure that when you unzip the patch, you dump the contents of the Ubuntu folder, _but not the Ubuntu folder itself_ into custom-package.

---

### Post by extrabigmehdi on 2007-11-07
Hi,
I'm frustrated. I tried every tutorial / method, 
each times I end up when I do fglrxinfo I get a message saying "Mesa".
And I  tried at least 4  method:
1 ) running directly the script from ati 
2) compiling/installing  from my desktop following instruction described and from the link to the wiki mentionned
3) using the "Envy" script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
4) installing an other linux distribution "sabayon" already including latest ati drivers.

Oh well, each time I restored a "relatively fresh" install using acronis true image
when playing with Ubuntu.

In fact I already once installed the "proprietary" drivers suggested by ubuntu,
but disabling them before installing ati driver doesn't make a difference.

I  get error "libGL.so.1 is missing"  or something like that when running  fglrxinfo for  first time. I solved  this by making a link to the file libGL.so.1.2

My system is 32 bits so obviously I didn't followed instructions involving the custom-package folder.

What else ? When I do
 >  sudo mkdir /lib/modules/$(uname -r)/volatile
it says:
```
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists
```

And after all, what I find weird is that the "ATI Control Center" is installed, and running.
I can play with the gamma for instance.
When I go to the information panel of  "ATI Control Center",
they confirm that I use an ATI RADEON 9800 Pro,
that the driver "8.42.3" is installed.
However they add
OpenGL provider: Mesa project: [www.mesa3d.orgO](www.mesa3d.orgO)
OpenGL renderer: Mesa GLX indirect
OpenGL version: 1.4 (2.01 Mesa 7.01)

So I'm really fedup, 
see in attachement my xorg.conf file (rename in txt for upload)
and screenshot of what I get in "ATI Control Center"

Can someone help ? thanks

---

### Post by luis.alves@lafaspot.com on 2007-11-07
*** IT WORKS ***

I updated the ati wiki here
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

to describe how to enable desktop effects on ubuntu and kubuntu gutsy.

works fine on my desktop.

---

### Post by angryfirelord on 2007-11-07
[QUOTE=extrabigmehdi]And after all, what I find weird is that the "ATI Control Center" is installed, and running.
I can play with the gamma for instance.
When I go to the information panel of "ATI Control Center",
they confirm that I use an ATI RADEON 9800 Pro,
that the driver "8.42.3" is installed.
However they add
OpenGL provider: Mesa project: [www.mesa3d.orgO](www.mesa3d.orgO)
OpenGL renderer: Mesa GLX indirect
OpenGL version: 1.4 (2.01 Mesa 7.01)

So I'm really fedup,
see in attachement my xorg.conf file (rename in txt for upload)
and screenshot of what I get in "ATI Control Center"[/QUOTE]
When I get that, I re-run these commands:
```
sudo depmod -a
```
```
sudo modprobe fglrx
```
Log out and log back in.
[QUOTE=luis.alves@lafaspot.com]*** IT WORKS ***

I updated the ati wiki here
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

to describe how to enable desktop effects on ubuntu and kubuntu gutsy.

works fine on my desktop.[/QUOTE]
Thanks, I'll update the link. :)

---

### Post by extrabigmehdi on 2007-11-07
hi 
I applied what angryfirelord
said i.e

[COLOR="DarkGreen"] sudo depmod -a
 sudo modprobe fglrx[/COLOR]

but it changes nothing.
The fglrx  driver is currently active ,  but for any reason , I can't get any 3D (with my ATI 9800 Pro)
The command :[COLOR="DarkGreen"] lsmod | grep fglrx[/COLOR]
gives the results:
[COLOR="Blue"]fglrx                1487340  3 
agpgart                35016  2 fglrx,intel_agp[/COLOR]

Maybe I should wait for Hardy Heron release. Or change my graphic card :mad:

---

### Post by Mosse on 2007-11-08
> **extrabigmehdi said:**
> hi 
I applied what angryfirelord
said i.e

[COLOR="DarkGreen"] sudo depmod -a
 sudo modprobe fglrx[/COLOR]

but it changes nothing.
The fglrx  driver is currently active ,  but for any reason , I can't get any 3D (with my ATI 9800 Pro)
The command :[COLOR="DarkGreen"] lsmod | grep fglrx[/COLOR]
gives the results:
[COLOR="Blue"]fglrx                1487340  3 
agpgart                35016  2 fglrx,intel_agp[/COLOR]

Maybe I should wait for Hardy Heron release. Or change my graphic card :mad:

I got the exact same problem, cant get the drivers to run properly even after loads of reinstalls and diffrent way to install them... But the CCC says that the driver is installed and finds what graphic card I got (asus x1950pro)

strange all this

---

### Post by angryfirelord on 2007-11-08
Ok, perhaps the wiki isn't that clear. After you install your debs (all of them) and blacklist the fglrx driver from the linux-restricted package, here's what I do:
```
sudo m-a a-i fglrx
```
```
sudo depmod -a
```
```
sudo dpkg-reconfigure xserver-xorg
```
I select fglrx as my driver. 
```
sudo modprobe fglrx
```
```
sudo reboot
```
Computer reboots. fglrxinfo shows that I have Mesa for 3D rendering.
```
sudo depmod -a
```
I notice that this depmod takes a little more time to complete.
```
sudo modprobe fglrx
```
Press Ctrl+Alt+F1 to restart X. I log back in and fglrxinfo shows the proper 3D renderer. 

That's how I set it up, but if the 8.42 is still giving you trouble, then you may just have to revert to the older ATI driver in the repos. Hopefully when 8.04 comes out, this will all be automatic, thus rendering this thread obsolete. :)

---

### Post by extrabigmehdi on 2007-11-13
Well,
I tried an alternative distribution "PCLinuxOS",
and got my driver for 9800 pro working for 3D.
Unfortuantely, this doesn't seem compatible with desktop effects.
Strangely, I could make some of these effects (not the 3d ones)  work before I installed the driver.

---

### Post by melenor on 2007-11-28
I have an X1800 and i used this guide and it worked well mostly.
everything was sluggish and when every i minimized something or maximized something it would turn the screen black, any idea why that might be?
thank you for your help.

---

### Post by melenor on 2007-11-28
[Sorry my internet went weird]

---

### Post by melenor on 2007-11-28
[Sorry my internet went weird]

---

### Post by ShAdEd_PaSt on 2008-02-25
I've followed your whole guide but im still getting

$ compiz --replaceChecking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:7183 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by compwiz18 on 2008-02-25
Try following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and use Method 2.  It contains instructions for the latest drivers.

---

### Post by ShAdEd_PaSt on 2008-02-25
> **compwiz18 said:**
> Try following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and use Method 2.  It contains instructions for the latest drivers.

Yeah that's how i did it...

---

### Post by ShAdEd_PaSt on 2008-02-26
> **ShAdEd_PaSt said:**
> Yeah that's how i did it...

anyone have any suggestions...

---

### Post by compwiz18 on 2008-02-26
You're probably best off to make a new thread in a different forum; more people are likely to see it. :)

---


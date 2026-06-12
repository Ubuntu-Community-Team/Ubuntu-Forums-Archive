---
title: "Which 3D Desktop guide applies to my 9550?"
date: 2007-01-24
forum: Desktop Environments
---

### Post by phayke on 2007-01-24
Yesterday I figured that I would try and install a 3D desktop on Ubuntu Edgy. I had already played around with it a little on the Mandriva 'One' disk. It was Compiz with AIGLX. It ran near perfect on my ancient 1Ghz machine with 512 ram, but I really didn't care for the whole Mandriva feel, also I hated all of the attempts to get me to join a club, it reminded me alot of my WinXP experience, where much of my software is trying to persuade me to spend money. I also loved the Ubuntu and Kubuntu look, very slick and fashionable. Anyway, that's off the topic.

I must have had about 30 or more pages and google searches opened on my firefox, and all of them were telling me different things. 'Use Compiz', 'use Beryl', 'use AIGLX for radeon cards', 'only XGL works with ATI', 'edit your xorg file' 'careful, editing your xorg file will crash your computer' Not only that, but all of these guides were written all for different chipsets and cards and distros and window managers, some pointed to other guides or redirected me places or expected me to know what to do next. I installed Beryl, fiddled with my xorg file, and uninstalled the fglrx or whatever drivers off of my computer and rebooted to a black screen. :( 

So I spent a day trying to do things the quiet observant way and ended up confused. I had to fresh reinstall and figured this would be the best time to ask for help, seeing as my drive is a blank slate. I have no preferences with the setup, but if I could get Ubuntu acting like Mandriva did, that would be awesome.

Again I have a Radeon 9550 AGP. The drivers are the default Edgy install.

---

### Post by CowzRule on 2007-01-24
With the default drivers that Edgy installs it's rather easy to use AiGLX and Beryl. The info I'm giving here is what works for me.

First we need to modify your xorg.conf file.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```Look for the following in your file and make it look similar to mine. The items in red are what I added or changed.```
Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
[Color=Red]	Driver		"radeon"
	Option	   "DRI" "Enable"
	Option          "AGPMode" "8"
	Option          "ColorTiling" "on"	
	Option          "AccelMethod" "XAA"
	Option          "EnablePageFlip" "on"
	Option	   "XAANoOffScreenPixMaps"
	Option	   "RenderAccel" "true"[/color]
	BusID		"PCI:1:0:0"
EndSection
``````
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
[color=red]	Option		"AIGLX" "true"[/color]
EndSection
``` and add the following to the bottom of the file```
[color=red]Section "Extensions"
  Option "Composite" "Enable"
EndSection
```[/color]Save and close the file.
Now you need to restart the X server to use your new xorg.conf settings. Log out then hit Ctrl+Alt+Backspase and log back in.
Now in the terminal put```
glxinfo | grep render
```and look for "direct rendering: Yes". If you got that, you're good to go for Beryl.
Now we need to add the Beryl repositories to your sources.list file```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```Add the following to the bottom of the file```
## Beryl
deb http://ubuntu.beryl-project.org/ edgy main
```Save and close the file.
Now you need the key. In the terminal put```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
Now update the package list```
sudo apt-get update
```
Now put```
sudo aptitude install beryl
```
When it's finished installing, put```
beryl-manager
```If all goes well, Beryl should throw out a splash screen, and your window borders will change to an Emerald theme and the windows will become wobbly when you move them. 
If you want Beryl to start automatically at log in, just add "beryl-manager" to Preferences-Sessions-Startup Programs.
Good Luck :)

---

### Post by phayke on 2007-01-24
Score! That got it working. Thank you for the help!

---

### Post by avihappy on 2007-02-01
Hadn't worked. I fail the direct rendering test. I have the same card as the OP! I use edgy with all updates. Help :( .

---


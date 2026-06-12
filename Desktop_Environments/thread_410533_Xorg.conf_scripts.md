---
title: "Xorg.conf scripts"
date: 2007-04-15
forum: Desktop Environments
---

### Post by dthomasdigital on 2007-04-15
I have a problem, I have two xorg.conf files one for duel screens and one for a single screen.
I want to create a button or a drop down list that will allow me to chose the one I want to run then restart X automatically.....so my question how do I even start a project like this?

---

### Post by hackerssidekick on 2007-04-16
The really really simple way of doing this is to symlink the config file to xorg.conf each time you wish to switch.

Suppose you have xorg.conf.single and xorg.conf.dual, and no xorg.conf (if you do, back it up now!), and in this case you want the dual conf, do this:

```
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
```

For the single conf, just replace the word dual above with the word single.

How would you do this graphically? For something that is easy to hack together, take a look at zenity. For example:
```
zenity --list --text="Select an xorg.conf" --column="Index" --column="Config" --hide-column=1 1 'Dual Monitor' 2 'Single Monitor'
```
This will display a list dialog, and if the user selects the first entry it will return 1 (the second entry will return 2). From this it is trivial to check the return value inside a bash (or other) script, and create the symlink depending on the return value. You need to run the script as root, which is also easy, just call the script (from a panel button, say) with gksudo.

Good luck!

---

### Post by dthomasdigital on 2007-04-16
This is perfect, but I'm a still pretty new at all this. Any details on creating and saving the scripts?

---

### Post by dthomasdigital on 2007-04-16
I think I'm getting close....

```
#!/bin/bash

SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="config" --hide-column=1 1 "Single Monitor" 2 "Duel Monitor"`


if [ $SCREEN = "1" ]; then 
zenity --error --text="single Monitor"
else
if [ $SCREEN = "2" ]; then
zenity --error --text="Duel Monitor"
else
zenity --error --text="Nevermind"
fi
fi
```


What do you think?

---

### Post by hackerssidekick on 2007-04-16
Yup looks good, although a couple things:
[LIST]
[*] It's **dual** not **duel** :D
[*] You should check if $SCREEN is defined first. This will stop those errors from coming up in the terminal.
[/LIST]

I've re-jigged the script to reflect the changes, take a look:
```
#!/bin/bash

SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="config" --hide-column=1 1 "Single Monitor" 2 "Dual Monitor"`

if [ -z $SCREEN ]; then
    zenity --error --text="Nevermind"
    exit
fi

if [ $SCREEN = "1" ]; then 
    zenity --info --text="Single Monitor"
elif [ $SCREEN = "2" ]; then
    zenity --info --text="Dual Monitor"
fi
```

Apart from that, it's looking good! I'd be keen on using myself when it's done :D

---

### Post by dthomasdigital on 2007-04-16
This is working just like I want it to except for one thing, how do I make it use gksudo so it runs as root from a panel button?

Here is the code:

```
#!/bin/sh
SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="Config" --hide-column=1 1 'Single Monitor' 2 'Dual Monitor'`
if [ $SCREEN = "1" ]; then
zenity --info --text="switching to Single Monitor X will restart"
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg.conf.single /etc/X11/xorg.conf
sudo killall Xorg
else
if [ $SCREEN = "2" ]; then
zenity --info --text="switching to Dual Monitor X will restart"
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
sudo killall Xorg
else
zenity --info --text="Nevermind"
fi
fi

```

Once I have it completely working right I'll put some credits on it and give you billing.....
What do you think? Oh and thanks for all the help.

---

### Post by elchato on 2007-04-16
Hi guys

Im completly new to Ubuntu and to Linux (just migrated today!) and I'm trying to make my laptop (toshiba, single Nvidia video card with 2 outs) work with 2 monitors, and I'd like to be able to switch from the 2 monitors to 1 monitor (can't carry an screen with the laptop!).

I was messing around with xorg.conf... and ended up unable to go back to the graphic interphase and having to reformat and reinstall since I didn't know what else to do...

any help for the n00b?

---

### Post by hackerssidekick on 2007-04-17
> **elchato said:**
> Hi guys

Im completly new to Ubuntu and to Linux (just migrated today!) and I'm trying to make my laptop (toshiba, single Nvidia video card with 2 outs) work with 2 monitors, and I'd like to be able to switch from the 2 monitors to 1 monitor (can't carry an screen with the laptop!).

I was messing around with xorg.conf... and ended up unable to go back to the graphic interphase and having to reformat and reinstall since I didn't know what else to do...

any help for the n00b?

You should start a new topic, that way more people will be able to see your issue (and give you a hand!).

---

### Post by hackerssidekick on 2007-04-17
> **dthomasdigital said:**
> This is working just like I want it to except for one thing, how do I make it use gksudo so it runs as root from a panel button?

Here is the code:

```
#!/bin/sh
SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="Config" --hide-column=1 1 'Single Monitor' 2 'Dual Monitor'`
if [ $SCREEN = "1" ]; then
zenity --info --text="switching to Single Monitor X will restart"
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg.conf.single /etc/X11/xorg.conf
sudo killall Xorg
else
if [ $SCREEN = "2" ]; then
zenity --info --text="switching to Dual Monitor X will restart"
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
sudo killall Xorg
else
zenity --info --text="Nevermind"
fi
fi

```

Once I have it completely working right I'll put some credits on it and give you billing.....
What do you think? Oh and thanks for all the help.

I think the best thing is to run the entire script under sudo (that way you can get rid of the sudos in the script itself). Basically, on the button you make, set **Command** to be **gksudo <path to script>**.

---

### Post by dthomasdigital on 2007-04-17
Make a set command - exactly what would that look like or what would be the steps for that.

I told you I'm flying blind here. But I sure am learning, again thanks for all the help. I got all these ideas for new scripts now.

---

### Post by hackerssidekick on 2007-04-17
Sorry, I should have been more clear :D

Right-click on the panel where you want to put the button (which launches the script), and click "Add to Panel". In the "Add to Panel" window that appeared, click on the button called "Custom Application Launcher". In the "Create Launcher" window that appeared, fill in the details as necessary, and pick a suitable icon. For example:

[[IMG]http://img249.imageshack.us/img249/9530/xorgswitcherlauncherlx4.th.png[/IMG]](http://img249.imageshack.us/my.php?image=xorgswitcherlauncherlx4.png)

The gksudo bit in the launcher properties will mean that when you click on the button, it will come up with a password dialog, and then run the script.

Give it a whirl :)

---

### Post by dthomasdigital on 2007-04-17
That did it!!! It works perfect....let me clean it up a bit and I will post the finished script here....thanks big time, your so rock.

---

### Post by dthomasdigital on 2007-04-17
Finished script - I think this is the finished version. Unless you have a better idea.

```
#!/bin/sh
#Xorg switcher by dthomasdigital and hackerssidekick
#This script will allow you to choose between two xorg.conf files

SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="Config" --hide-column=1 1 'Single Monitor' 2 'Dual Monitor'`
if [ $SCREEN = "1" ]; then
zenity --info --text="Switching to Single Monitor X will restart"
rm /etc/X11/xorg.conf
ln -s /etc/X11/xorg.conf.single /etc/X11/xorg.conf
killall Xorg
else
if [ $SCREEN = "2" ]; then
zenity --info --text="Switching to Dual Monitor X will restart"
rm /etc/X11/xorg.conf
ln -s /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
killall Xorg
else
zenity --info --text="Nevermind"
fi
fi

```

---

### Post by hackerssidekick on 2007-04-18
Looks good to me :D

Now all I have to do is configure the dual monitor Xorg!

---

### Post by dthomasdigital on 2007-04-18
Would you like to see my two xorg.conf files? I have an ati card if that helps.

---

### Post by dthomasdigital on 2007-04-23
One screen two screen we all scream for a screen.
Xorg Switcher Documentation:

There is a small issue in the way which Ubuntu handles the ati graphics (specifically the Radeon X600)  card running 3d or opengl applications on a two screen configuration. It has a tendency to run those types of applications either  very slowly or not at all.   However, when configured to run on a single screen setup, opengl and 3d accelerated applications run with absolutely no limitations. 

Why run dual screen if you encounter no limitations on a single screen configuration? For certain tasks such as desktop publishing, web or application development a dual screen configuration is invaluable, but if your playing the latest first person shooter  game like Doom3 or Prey, a fast 3D accelerated graphics card is a must.

The solution was to create two separate xorg.conf files, one for a single screen set up and one for a dual screen set up. Creating the two separate xorg.conf files was relatively simple.

Here are the two sample files.
 	technical note: all files need to be located in \etc\X11\


xorg.config.single

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file) 
# 
# This file was generated by dexconf, the Debian X Configuration tool, using 
# values from the debconf database. 
# 
# Edit this file with caution, and see the xorg.conf(5) manual page. 
# (Type "man xorg.conf" at the shell prompt.) 
# 
# This file is automatically updated on xserver-xorg package upgrades *only* 
# if it has not been modified since the last upgrade of the xserver-xorg 
# package. 
# 
# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Files" 
	Fontpath	"/usr/share/fonts/X11/misc" 
	Fontpath	"/usr/share/fonts/X11/cyrillic" 
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/Type1" 
	Fontpath	"/usr/share/fonts/X11/100dpi" 
	Fontpath	"/usr/share/fonts/X11/75dpi" 
	# path to defoma fonts 
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
	Load		"i2c" 
	Load		"bitmap" 
	Load		"ddc" 
	Load		"dri" 
	Load		"extmod" 
	Load		"freetype" 
	Load		"glx" 
	Load		"int10" 
	Load		"vbe" 
EndSection 

Section "InputDevice" 
	Identifier	"Generic Keyboard" 
	Driver		"kbd" 
	Option		"CoreKeyboard" 
	Option		"XkbRules"	"xorg" 
	Option		"XkbModel"	"pc105" 
	Option		"XkbLayout"	"us" 
	Option		"XkbOptions"	"lv3:ralt_switch" 
EndSection 

Section "InputDevice" 
	Identifier	"Configured Mouse" 
	Driver		"mouse" 
	Option		"CorePointer" 
	Option		"Device"	"/dev/input/mice" 
	Option		"Protocol"	"ImPS/2" 
	Option		"ZAxisMapping"	"4 5" 
	Option		"Emulate3Buttons"	"true" 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"stylus" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"eraser" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "Device" 
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Driver		"fglrx" 
	Busid		"PCI:1:0:0" 
EndSection 

Section "Monitor" 
	Identifier	"DELL 1707FP" 
	Option		"DPMS" 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Monitor		"DELL 1707FP" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	1 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	4 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	8 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	15 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	16 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	24 
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
  screen "Default Screen" 
	Inputdevice	"Generic Keyboard" 
	Inputdevice	"Configured Mouse" 
	Inputdevice	"stylus"	"SendCoreEvents" 
	Inputdevice	"cursor"	"SendCoreEvents" 
	Inputdevice	"eraser"	"SendCoreEvents" 
EndSection 

Section "DRI" 
	Mode	0666 
EndSection 
Section "Extensions" 
	Option		"Composite"	"0" 
	Option		"Composite"	"0" 
EndSection
```


The second file you will need is:

xorg.config.dual

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file) 
# 
# This file was generated by dexconf, the Debian X Configuration tool, using 
# values from the debconf database. 
# 
# Edit this file with caution, and see the xorg.conf(5) manual page. 
# (Type "man xorg.conf" at the shell prompt.) 
# 
# This file is automatically updated on xserver-xorg package upgrades *only* 
# if it has not been modified since the last upgrade of the xserver-xorg 
# package. 
# 
# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Files" 
	Fontpath	"/usr/share/fonts/X11/misc" 
	Fontpath	"/usr/share/fonts/X11/cyrillic" 
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/Type1" 
	Fontpath	"/usr/share/fonts/X11/100dpi" 
	Fontpath	"/usr/share/fonts/X11/75dpi" 
	# path to defoma fonts 
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
	Load		"i2c" 
	Load		"bitmap" 
	Load		"ddc" 
	Load		"dri" 
	Load		"extmod" 
	Load		"freetype" 
	Load		"glx" 
	Load		"int10" 
	Load		"vbe" 
EndSection 

Section "InputDevice" 
	Identifier	"Generic Keyboard" 
	Driver		"kbd" 
	Option		"CoreKeyboard" 
	Option		"XkbRules"	"xorg" 
	Option		"XkbModel"	"pc105" 
	Option		"XkbLayout"	"us" 
	Option		"XkbOptions"	"lv3:ralt_switch" 
EndSection 

Section "InputDevice" 
	Identifier	"Configured Mouse" 
	Driver		"mouse" 
	Option		"CorePointer" 
	Option		"Device"	"/dev/input/mice" 
	Option		"Protocol"	"ImPS/2" 
	Option		"ZAxisMapping"	"4 5" 
	Option		"Emulate3Buttons"	"true" 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"stylus" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"eraser" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
	# /dev/input/event 
	# for USB 
EndSection 

Section "Device" 
	Identifier	"0 ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Driver		"fglrx" 
	Busid		"PCI:1:0:0" 
        Screen          0 
EndSection 

Section "Monitor" 
	Identifier	"Dell 1707FP" 
	Option		"DPMS" 
EndSection 


Section "Device" 
	Identifier	"1 ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Driver		"fglrx" 
	Busid		"PCI:1:0:0" 
        Screen          1 
EndSection 

Section "Monitor" 
	Identifier	"Dell 1707FP" 
	Option		"DPMS" 
EndSection 

Section "Screen" 
	Identifier	"Main Screen" 
	Device		"0 ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Monitor		"Dell 1707FP" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	1 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	4 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	8 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	15 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	16 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	24 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
EndSection 

Section "Screen" 
	Identifier	"Second Screen" 
	Device		"1 ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" 
	Monitor		"Dell 1707FP" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	1 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	4 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	8 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	15 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	16 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth	24 
		Modes		"1280x1024"	"800x600"	"640x480" 
	EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
   Screen               0 "Main Screen" 
   Screen               1 "Second Screen" RightOf "Main Screen"  
	Inputdevice	"Generic Keyboard" 
	Inputdevice	"Configured Mouse" 
	Inputdevice	"stylus"	"SendCoreEvents" 
	Inputdevice	"cursor"	"SendCoreEvents" 
	Inputdevice	"eraser"	"SendCoreEvents" 
        option          "Xinerama" 
EndSection 

Section "DRI" 
	Mode	0666 
EndSection 
```


Now the not so fun part, to switch back and forth between these two set-ups is a real pain. First you have to be root to change the xorg.conf file. Then you have tp rename the  setup file you want to use to xorg.conf while making sure you don't copy over any of your other .conf files. On more than one occasion I corrupted the configuration file and had to install the xorg.conf file by hand in the terminal from a backup. There had to be a better way.


Scripts to the rescue. Xorg Switcher is a Linux script that with the help of zenity makes the task of switching back and forth between different xorg configurations as easy as pressing a button. 

Here is the script:

```
#!/bin/sh 
#Xorg switcher by dthomasdigital and hackerssidekick 
#This script will allow you to choose between two xorg.conf files 

SCREEN=`zenity --list --text="Select an xorg.conf" --column="Index" --column="Config" --hide-column=1 1 'Single Monitor' 2 'Dual Monitor'` 
if [ $SCREEN = "1" ]; then 
zenity --info --text="Switching to Single Monitor X will restart" 
rm /etc/X11/xorg.conf 
ln -s /etc/X11/xorg.conf.single /etc/X11/xorg.conf 
killall Xorg 
else 
if [ $SCREEN = "2" ]; then 
zenity --info --text="Switching to Dual Monitor X will restart" 
rm /etc/X11/xorg.conf 
ln -s /etc/X11/xorg.conf.dual /etc/X11/xorg.conf 
killall Xorg 
else 
zenity --info --text="Nevermind" 
fi 
fi 
```

Don't forget that you will need to make the script executable.

Once you create the script, you will need to place it in a directory. I create a directory called scripts in the home directory. This is just for easy reference and you can place it any where you would like.

The next step is to add a launcher to the panel

First right mouse click on the panel
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic1.png[/IMG]

Click Add to panel and you will see the next window:

[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic2.png[/IMG]

Click Custom application Launcher

You will see the next screen:
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic3.png[/IMG]

Enter the following information
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic4.png[/IMG]

A little explanation:

Type: well is an application.
Name: Name of the application (you can call it what ever you want.
Command: gksudo  is a great command. When you run the script it will ask you for the root password, (like stated earlier you must have root access to change the xorg.conf file) <full path> is the path where your script is located.
Comment: Add what you would like
Press the No Icon button and select an icon.

Now run the script.

Click on the panel launcher you just created.
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic5.png[/IMG]

Once you do, you will be asked to enter the root password.

You should then see this window.
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic6.png[/IMG]

If you click cancel you will see this window
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic7.png[/IMG]

Click on the desired configuration you want and click the OK button.
[IMG]http://www.mediamax.com/dthomasdigital/Hosted/xorgpic8.png[/IMG]

You will then see this window. Beware if you click the X to cancel the script will still run (might fix that in a later version)

Once you click the OK button, X will restart. You log back into Gnome and your new xorg.conf will be running.


So that's it, this is all you need to make switching your xorg.conf file as easy as pressing a button. I'd like to thank hackerssidkick from the Ubuntu forums for showing me how to rename the files and turning me on to zenity. If you would like to contact me please email me at [email]dthomasdigital@gmail.com[/email] and visit the web site http:\\myweb.cableone.net\dthomas 


Look for more script howtos coming soon......

---

### Post by madx80 on 2007-04-25
can i change xorg to have two options single and dual, and let it detect the single/dual option at startup and set that.

---


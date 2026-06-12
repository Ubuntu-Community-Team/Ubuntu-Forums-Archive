---
title: "Howto get Dell BT Travel Mouse set up (with side scroll buttons)"
date: 2008-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RobertH on 2008-07-11
I hope this will will help you get your bluetooth mouse working with all of its buttons. My original problem was that the side scrolling buttons weren't working.

I have a Dell Bluetooth Travel Mouse ("D P/N PU705" written on the bottom of the mouse" I got it working with this config. First make sure imwheel is NOT installed. Then you need to run the command
```
cat /proc/bus/input/devices
```
Find our what number event it is. This is under "Handlers" in the "Dell BT Travel Mouse" section of the output of this command. My number was "event12"
Backup your /etc/X11/xorg.conf file (I suggest you time and date stamp your backup).
For example:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-9:13pm-12.7.08
```
Then go to your Configured Mouse section
I had:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"explorerPS/2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```
And you want to replace this with your new section using the evdev driver (making sure you use the appropriate device name) - you have to use the event one, not the mouse one!
In my case (M1530 & Dell BT Travel Mouse Dell Part Number PU705 [written underneath after "D P/N"]) This is my new mouse section:
```
Section "InputDevice"
	Identifier "evdev Mouse"
	Driver 		"evdev"
	Option 		"Name" "Dell BT Travel Mouse"
	Option          "evBits"  "+1-2"
	Option          "keyBits" "~272-287"
	Option          "relBits" "~0-2 ~6 ~8"
	Option          "Pass"    "3"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/event12"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "9"
EndSection
```
There are a few important points before you go and restart X in your newfound glee. You have to do a couple more edits to your xorg.conf file.
You need to go down to the "ServerLayout" section
(Mine originally looked like this)
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse" "Corepointer"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
```
And change the line that refers to the "Configured Mouse". Since we changed the identifier of this to "evdev Mouse" we need to change it down here too or else X will not start properly :(, so mine became this:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"evdev Mouse" "CorePointer"
	Inputdevice	"Synaptics Touchpad"
EndSection
```
(I removed all the Wacom tablet stuff in my xorg.conf becuase I don't have, or plan on buying, a Wacom tablet. You don't need to: It just was ticking me off ;))

I think it would be possible to just add the "evdev Mouse" section instead of replacing the "Configured Mouse" section and add the line above without deleting the old one, but I only use my touchpad and this Dell BT mouse so I haven't tried it. I chose to replace it so that my BT mouse is always using the right driver (I have heard that after suspends and stuff the mouse might come back using a different driver if there is another section left that might also work)
There is a bug with the evdev drivers that means that the DGA extension does not work properly. I don't know what the extension is or does but without this fix the cursor will jump around the screen in fullscreen OpenGL/SDL apps such as games. (The whole reason I wanted all my buttons working was for Enemy Territory: Quake Wars) so you have to disable it in you xorg.conf (or u can fix the problem in some games using a runtime option that you can find through a Google search) but this seems to fix it for all programs.

Go down to the "Module" Section.
Mine looked like this:
```
Section "Module"
	Load		"glx"
EndSection
```

And add in the line to disable the DGA extension
Tada:
```
Section "Module"
	Load		"glx"
        SubSection  "extmod"
             Option    "omit xfree86-dga"   # don't initialise the DGA extension
        EndSubSection
EndSection
```

When you go to restart X, I suggest that you logout and switch to Virtual Terminal 1 (Ctrl + Alt + F1) and login here. Then kill gdm:
```
sudo pkill gdm
```
and then start x manually:
```
startx
```
This way you can easily make the changes using gedit and then when u need to test them you can kill X (Ctrl + Alt + Backspace) (or logout if you're feeling patient) and restart X by running:
```
startx
```
again. 
The reason I recommend this way is because you get command line feedback if X doesn't start properly and you don't get that annoying failsafe X that rewrites all of you settings for fun :). And if you can't fix the problem from the command line feedback you just copy back one of your your backup files (because you *did* make them this time, didn't you?) :p and you are no worse off than when you started.

If you need to restore your original xorg.conf file just use the cp command.
For example:
```
sudo cp /etc/X11/xorg.conf-9:13pm-12.7.08 /etc/X11/xorg.conf
```

I will copy in my final xorg.conf and attach the before and after xorg.conf file for you to look at. Just remember that we have different laptops with different screens and graphics cards so just copy the input sections. My xorg.conf file also has a good example (good for me at least) of the touchpad configurations section if you are interested.

If you have been playing around with xmodmap just set everything back to their original defaults. (info in the xmodmap man page)

It is quite late at night for me now so if you think something I have written doesn't look quite right ask me or someone about it tomorrow.

These are the links I used to do this:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons")
[http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working#Installing_the_evdev_Drivers]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working#Installing_the_evdev_Drivers")

Good Luck and remember that you can always switch over to a Virtual Terminal and copy back your old config if something goes wrong.

PLEASE NOTE- Sometimes the mouse will connect as a different mouse and event #. With this configuration this means that the mouse will not work. The device option in the xorg.conf has to be correct. It is supposed to be possible for evdev to corectly find the mouse (or you can use the /dev/input/by-id/ entries) but I have not had any luck in getting these to work. Maybe you can duplicate the section with a different identifier and a different device name if your mouse always seems to be one of two device locations. If you do this you will have to add the "InputDevice" line in the "ServerLayout" section for the new input device - Goodluck


Final xorg.conf file:
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

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TripleBuffer"	"True"# Experimental
	Option		"BackingStore"	"True"# Experimental
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"OnDemandVBlankInterrupts"	"true"
	Option		"CoolBits"	"1"
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
	Identifier "evdev Mouse"
	Driver 		"evdev"
	Option 		"Name" "Dell BT Travel Mouse"
	Option          "evBits"  "+1-2"
	Option          "keyBits" "~272-287"
	Option          "relBits" "~0-2 ~6 ~8"
	Option          "Pass"    "3"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/event12"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "9"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"120"
	Option		"RightEdge"	"830"
	Option		"TopEdge"	"120"
	Option		"BottomEdge"	"650"
	Option		"FingerLow"	"14"
	Option		"FingerHigh"	"15"
	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"110"
	Option		"ClickTime"	"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"	"0.6"
	Option		"MaxSpeed"	"0.8"
	Option		"AccelFactor"	"0.080"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
	Option		"SHMConfig"	"true"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"evdev Mouse" "CorePointer"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
        SubSection  "extmod"
             Option    "omit xfree86-dga"   # don't initialise the DGA extension
        EndSubSection
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


```
NB- I copied this from a post I made in another thread once I realized that it was in the archive section :rolleyes:.

---

### Post by PinkFloyd102489 on 2008-07-12
I just paired mine and started using it with no configuration. Side buttons and rocker wheel worked also.

---

### Post by RobertH on 2008-07-13
Well my configuration didn't even have xev output when the side scroll buttons were pressed. The /dev/input/mouse# device had no output for these buttons either and since I presume the /dev/input/mice device is made from those ii didn't work. I guess I should try just canging the device to the /dev/input/event# one with the default mouse driver. What is your Dell Part number? (written after "D P/N" under the mouse) and what laptop are you using? So you had all "9" buttons working? ... Interesting!

---

### Post by PinkFloyd102489 on 2008-07-13
Part number is PU705.

---

### Post by RobertH on 2008-07-13
Can you please post your xorg.conf and what laptop you are using plus any other information you think might be relevant. Just out of curiosity did you do a fresh install or an upgrade to Hardy?

---

### Post by PinkFloyd102489 on 2008-07-13
I did a fresh install. Just got this thing Tuesday. Here's the specs on it:


Inspiron 1720
Vista Home Premium
Intel Core 2 Duo 2.4Ghz 800Mhz FSB 3MB cache
4GB Shared dual channel DDR2 RAM @ 667Mhz
320GB SATA HD 5400RPM
Nvidia GeForce 8600M GT 256MB
SoundBlaster Audigy HD SE
Dell 1505 Draft A/G/B/N Wireless Mini-Card
Built in webcam
Bluetooth
DVD-RW


I hate the partition scheme that Dell lays out. Vista is on sda3 270GB, Ubuntu is on sda6, 30GB.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

File hasnt been hand altered, only what the Nvidia site driver configuration has done.

---

### Post by RobertH on 2008-07-13
I'll try that config (very simple!)

Here is my partition table (I redid most of the partitions) this allows me to use the Dell media direct button to boot windows (which I hardley ever do) and the power button to boot Ubuntu.
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        7838    62910342+  d7  Unknown
/dev/sda3   *        7839        9796    15727635   83  Linux
/dev/sda4            9797       38913   233882302+   5  Extended
/dev/sda5            9797       37347   221303376   83  Linux
/dev/sda6           37870       38913     8385898+  82  Linux swap / Solaris

```

There are other steps to get it booting like this, here is some more information:

Here are some links about using the Dell Media Direct button to boot
Linux (just swap the partition numbers when you run the command on the
Media direct install CD if you want to use the Power button for Linux
and the Media Direct button for Windows)

[http://forum.notebookreview.com/showthread.php?t=182495](http://forum.notebookreview.com/showthread.php?t=182495)
[http://forum.notebookreview.com/showthread.php?t=180795](http://forum.notebookreview.com/showthread.php?t=180795)
[http://ubuntuforums.org/showpost.php?p=3113451](http://ubuntuforums.org/showpost.php?p=3113451)

---

### Post by RobertH on 2008-07-13
I tried this and there was no xev output from the side scroll buttons. I will do a fresh install eventually but I have spent so many hours setting this laptop ut just right :)

---

### Post by PinkFloyd102489 on 2008-07-14
Honestly, it had to be the most painless install Ive ever done. Everything worked right off, even installing the wireless was smooth.

---

### Post by RobertH on 2008-07-14
Oh yeah the install was smooth sailing, but setting up my volume control on the XPS properly and customizing the xorg.conf to make it work well with compiz fusion took a while. The volume response was not linear so I wrote a program in C++ to scale that and then used ivman to trigger the program from the hal events generated by the key presses. (because Gnome cannot grab them whe you are in fullscreen apps)

 I spent hours with powertop too! Lowering power consumption was probably the most time-consuming. (but now I run the -rt kernel for games anyway :))

---

### Post by TimDaniels on 2008-07-21
> **PinkFloyd102489 said:**
> I just paired mine and started using it with no configuration. Side buttons and rocker wheel worked also.

Great!! I'm in the right place because I'm dual-booting Ubuntu 7.10 from the Dell Ubuntu .iso download, and I can't get my BT Travel Mouse to work on Ubuntu.  Now... what does "paired" mean, and how does one do it?  (Thanks for any help, as I'm a Linux newbie.)

*TimDaniels*

---

### Post by TimDaniels on 2008-07-21
> **PinkFloyd102489 said:**
> Honestly, it had to be the most painless install Ive ever done. Everything worked right off, even installing the wireless was smooth.

Fantastic!  I can't get my WiFi to work under Ubuntu 7.10.  How did you do it?

*TimDaniels*

---

### Post by TimDaniels on 2008-07-21
> **TimDaniels said:**
> I can't get my BT Travel Mouse to work on Ubuntu...
BTW, "lspci" reveals that the Broadcom chip is BCM4312.

*TimDaniels*

---

### Post by PinkFloyd102489 on 2008-07-21
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)


Check the link at the beginning of the post too. I actually used that instead of the forum post.

---

### Post by TimDaniels on 2008-07-21
> **PinkFloyd102489 said:**
> [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)


Check the link at the beginning of the post too. I actually used that instead of the forum post.

Thanks.  It seems to have worked for a lot of other people, too.  Is that the fix for both Bluetooth and Wi-Fi, or just for one of them?

*TimDaniels*

---

### Post by PinkFloyd102489 on 2008-07-21
Bluetooth should work out of the box. Mine did at least. Make sure the Wifi-Catcher is turned on because it controls both Wifi and BT radios by default.

---

### Post by RobertH on 2008-07-21
Well I have and XPS m1530 so I have an Intel Wireless chip so it works out of the box. My mouse worked out of the box too; all this drama was just to get the last two buttons working (For quake wars). In the end I just went back to the plain old "mouse" driver because the mouse connects more easily. Everything pretty much works out of the box because the m1530 is just the bigger brother m1330. If your bluetooth is working fine but you are just having trouble pairing it up these are the steps I take to reconnect my BT travel mouse if it is playing up.

1. Flip my bluetooth off and wait 5 seconds
2. Flip it on again (if u don't have a hardware switch just unload and reload the modules)
3. Flip your mouse off and on again
4. Go to you bluetooth manager (in the notification bar) > preferences
5. Click on the "services" tab
6. Click on "Input sevice"
7. Go down to the box at the bottom of the window
8. Remove any devices that are listed
9. Go to add
10. Push the blue button on your mouse
11. Wait until it (hopefully) shows up and hit Connect

If you are ever asked for a security code it would be 0000 ( I have never been asked)

---

### Post by PinkFloyd102489 on 2008-07-21
If I had a problem with mine, I just issued these commands:

```

hcitool scan

*This will give a MAC address. Ex: 1a:2b:3c:4d*

sudo hidd --connect MACADDRESS
```

Obviously replace the MACADDRESS with the one from the output of the first command.

---

### Post by PinkFloyd102489 on 2008-07-21
EDIT: Accidental double post.

---

### Post by RobertH on 2008-07-22
Yeah I used to pair it with the command line, but after configuring it with the GUI it picks it up every time I boot.

---

### Post by PinkFloyd102489 on 2008-07-22
Mine doesnt always, I still have to use that command some times.

---

### Post by TimDaniels on 2008-07-23
> **PinkFloyd102489 said:**
> Bluetooth should work out of the box. Mine did at least. Make sure the Wifi-Catcher is turned on because it controls both Wifi and BT radios by default.

I feel my Bluetooh should work right out of Dell's Ubuntu 7.10 .ISO file, too, since the Bluetooth icon is showing.  First, I checked that the Wireless Switch was in the "1" position, then I turned on the Travel Mouse and pressed its broadcast button and its blue LED began flashing, and then I rt-clicked the Bluetooth icon and selected Browse Device.  "Dell BT Travel Mouse" was the only menu entry - which I selected - and then I clicked Connect.

An error box popped up with the error msessage:

"'obex://[00:07:61:b8:36;e3]' is not a valid location
Please check the spelling and try again."

In Vista, when I rt-click the Bluetooth icon and select Show Bluetooth Devices, the Devices tab shows "Dell BT Travel Mouse" as the only entry.  Selecting that entry and clicking the Properties button brings up a panel that shows the above location as the address of the BT Travel Mouse.  For Vista, there is something there that links to the BT Travel Mouse, and for Ubuntu it's an "invalid location".  Does that suggest what's keeping the Bluetooth Travel Mouse from working with Ubuntu?

*TimDaniels*

---

### Post by RobertH on 2008-07-23
You have to go to preferences > services > input
and click add.

The menu you are in is for browsing devices and there is no reason to browse the files of a mouse because it doesn't have any.

---

### Post by TimDaniels on 2008-07-23
> **RobertH said:**
> Well I have and XPS m1530 so I have an Intel Wireless chip so it works out of the box. My mouse worked out of the box too; all this drama was just to get the last two buttons working (For quake wars). In the end I just went back to the plain old "mouse" driver because the mouse connects more easily. Everything pretty much works out of the box because the m1530 is just the bigger brother m1330. If your bluetooth is working fine but you are just having trouble pairing it up these are the steps I take to reconnect my BT travel mouse if it is playing up.

1. Flip my bluetooth off and wait 5 seconds
2. Flip it on again (if u don't have a hardware switch just unload and reload the modules)
3. Flip your mouse off and on again
4. Go to you bluetooth manager (in the notification bar) > preferences
5. Click on the "services" tab
6. Click on "Input sevice"
7. Go down to the box at the bottom of the window
8. Remove any devices that are listed
9. Go to add
10. Push the blue button on your mouse
11. Wait until it (hopefully) shows up and hit Connect

If you are ever asked for a security code it would be 0000 ( I have never been asked)

Well, I did basically that, and now the cursor moves and the right and left buttons work!  The trick was unchecking the "Input service" and then checking it again to bring up the "Add" window.  But the left/right "wobble" on the spin wheel doesn't do anything, and the Forward/Back buttons do something other than forward/back.  You mentioned "pairing" to get these functions to work - what does "pairing" mean, what is the procedure?

Thanks for the help, Guys!

*TimDaniels*

---

### Post by RobertH on 2008-07-23
To get the wobble (tilt-scroll) working you have to do all the stuff in the very first post of the thread, but I wouldn't bother becuase it's not worth it. It's really unreliable when set up with the evdev driver becuase it isn't always recognized.

After setting my mouse up with all of the buttons working perfectly I put it back to the way you have it now because it is just not worth it.

To remap the buttons use xmodmap, but you will have to do a search to find out about that because I don't know much about it. Actually the buttons might just be what your z or w axis is set to in your xorg.conf file.

---

### Post by PinkFloyd102489 on 2008-07-23
> **RobertH said:**
> To get the wobble (tilt-scroll) working you have to do all the stuff in the very first post of the thread, but I wouldn't bother becuase it's not worth it. It's really unreliable when set up with the evdev driver becuase it isn't always recognized.

After setting my mouse up with all of the buttons working perfectly I put it back to the way you have it now because it is just not worth it.

To remap the buttons use xmodmap, but you will have to do a search to find out about that because I don't know much about it. Actually the buttons might just be what your z or w axis is set to in your xorg.conf file.


Rocker wheel (side to side) worked fine for me without any configuration. Weird huh?

---

### Post by TimDaniels on 2008-07-23
> **RobertH said:**
> To get the wobble (tilt-scroll) working you have to do all the stuff in the very first post of the thread, but I wouldn't bother becuase it's not worth it. ...

I'll go with that.  I'm dual-booting Ubuntu 7.10 with the pre-installed Vista, and the Ubuntu 7.10 was taken from the Dell website's downloadable .iso file for my XPS-M1330 laptop.  In the near future, I'll either download Dell's 8.04 .iso file (if Dell makes it available) or I'll do the upgrade thing from the Ubuntu website, and I don't want to go through all this hardware angst again.  Do you expect that Hardy Heron, as it comes from Ubuntu, would have better drivers for Bluetooth and Wi-Fi devices?

*TimDaniels*

---

### Post by RobertH on 2008-07-23
I had pretty much the same hardware support between 7.10 and 8.04 except for sound. You can now use the digital mic with no screwing around. (m1530 for me) Oh and the screen brightness indicator is a bit better.

---

### Post by TimDaniels on 2008-07-24
> **RobertH said:**
> I had pretty much the same hardware support between 7.10 and 8.04 except for sound. You can now use the digital mic with no screwing around. (m1530 for me) Oh and the screen brightness indicator is a bit better.

Thanks for the preview.  I think I'll clone 7.10 (now in a Primary partition) to logical partitions, then upgrade the clone to 8.04 and have it use a common swap partition with 7.10.  Then on to virtualization...

*TimDaniels*

---

### Post by RobertH on 2008-07-24
You use a seperate home partition right? It makes life sooooooooooo much easier!

---

### Post by TimDaniels on 2008-07-25
> **RobertH said:**
> You use a seperate home partition right? It makes life sooooooooooo much easier!

No, I have just one partition for Ubuntu and one for swap.  I spent a few days researching recommended partitioning for Linux,
and I got a (virtual) headache.  I finally admitted to myself that I'm mostly just experimenting with Linux/Windows dual-booting and learning how to set up Linux, and for that I could do without all the separate partitions.  If I ever get into the development mode with Linux, of course, or it I make Linux my main OS for personal tasks, I'll tease out the file structure into several partitions.  As an illustration of my current view, even with Windows I have just one partition.

*TimDaniels*

---

### Post by RobertH on 2008-07-25
Well when you do your reinstall just make yourself a seperate home partition. Then when you login for the first time just copy the data over from your old home folder from your old installation if you want all of your data and settings (themes, desktop, toolbars, etc.).

---

### Post by TimDaniels on 2008-07-27
> **RobertH said:**
> Well when you do your reinstall just make yourself a seperate home partition. Then when you login for the first time just copy the data over from your old home folder from your old installation if you want all of your data and settings (themes, desktop, toolbars, etc.).

Thanks for that comment.  I just thought /home was a convenient place for a user's data.  It didn't occur to me that various settings were contained there as well.  Is there still a way to put /home in a separate partition without re-installing?

*TimDaniels*

---

### Post by RobertH on 2008-07-27
Well I have never done it but there is an explanation here that looks quite good:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by PinkFloyd102489 on 2008-07-27
I think I figured out why. Change the CorePointer under the Server Layout to the mouse, probably Mouse0. In order to get my touchpad working correctly, I have to change the CorePointer to "Synaptics Touchpad". But then the BT mouse doesnt work. Changing the CorePointer to "Mouse0", which is my BT, makes the mouse work again but then the touchpad stops functioning like it should.


I wish there was some way to make them both work.

---

### Post by RobertH on 2008-07-28
Well, have a look at my "before" xorg.conf
Because that is basically what I am using now and it works fine.

---

### Post by TimDaniels on 2008-07-29
In regards to moving /home to another partition:

> **RobertH said:**
> Well I have never done it but there is an explanation here that looks quite good:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

Gleep!  That seems to be about 2 dozen procedures, some of which work.  Since I haven't really started doing much with my Feisty installatin, I think I'll just re-nstall it with /home in a new partition instead of trying to move it.  Thanks for the link, though.  I see lots of people found it useful.

*TimDaniels*

---

### Post by TimDaniels on 2008-08-01
> **PinkFloyd102489 said:**
> I think I figured out why. Change the CorePointer under the Server Layout to the mouse, probably Mouse0. In order to get my touchpad working correctly, I have to change the CorePointer to "Synaptics Touchpad". But then the BT mouse doesnt work. Changing the CorePointer to "Mouse0", which is my BT, makes the mouse work again but then the touchpad stops functioning like it should.


I wish there was some way to make them both work.

Have you tried puting:
Option   "SendCoreEvents"   "true"
in the touchpad section?  According to the "man" pages:

       Option "AlwaysCore"  "boolean"

       Option "SendCoreEvents"  "boolean"
              Both of these options are equivalent, and when enabled cause the input device to always report core events.  This can be used, for example,
              to allow an additional pointer device to generate core pointer events (like moving the cursor, etc).


I have:
"Option "corepointer"
    in my BT mouse section, and
Option "SendCoreEvents"  "boolean"
    in my touchpad section, and both devices work concurrently, although I still have the problem of the Fore/Back buttons and the "tilt" buttons not working.

*TimDaniels*

---


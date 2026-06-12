---
title: "Graphics card is killing me max res of 800x600"
date: 2008-02-10
forum: Desktop Environments
---

### Post by drubin on 2008-02-10
I am new to linux, 

So far  i am liking most of it, applications are working. But i have NO idea how to set up my graphics card.(Most important thing)

I have searched the forums, I tried  'envy'  (it  downloaded allot of stuff) then configured things, and then when i re-started my computer. Ubuntu told me my graphics were at a very low res and i need to re configure them.

Here is the set up.
19'  Lcd Wide screen (LG) (would like to be my primary)
19' CRT  (Philips)

My graphics card is a 
MSI
NX7300GS-TD 
Nvidia GeForce 
256mb DDR2


I have had them on dual screen on windows for ages. the LCD is my primary monitor, but i cant seem to get Ubuntu to  use it, (I unplugged the CRT and then the MAX res i could get was 800x600 sis!!)

I have searched the forums but i am not exactly sure what i am looking for or even what relates to me.... :)  


Please if there is any thing else i can give/ commands i can run to give more information please let me know. But i am dieing at a res or 800x600.

Thanks

---

### Post by Tommaso on 2008-02-10
Please post your Xorg.conf and check if in the "screen" section are listed the possible resolution like mine:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"nVidia 7900 Gs"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia 7900 Gs"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600"    <---here
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"


```

bye....Tommy

---

### Post by PmDematagoda on 2008-02-10
Install the driver manually:-

1) Install the required prerequisites for the Nvidia installer using:-
```
sudo apt-get install build-essential
```

2) Download the Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run
```

3) Make a few changes to the "DISABLED_MODULES" line of a modules file using:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Note:- From this point on you will be using the CLI(Command Line Interface) where you will have to be completely dependent on commands.

4) Kill the X-Server using:-
```
sudo /etc/init.d/gdm stop
```

5) Execute the Nvidia installer using:-
```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

6) After the installation is successful reconfigure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
choosing the driver as "nvidia" and any other options you may need.

7) Restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

---

### Post by drubin on 2008-02-10
sudo /etc/init.d/gdm stop 

Tried that line, but my screen goes, blank (well apart from some text) but i wasnt sure where to type the rest of the CMD's in..... also am i suppose to still have all the windows/web pages open so that i can read the cmd's to type in, or do i need to print them out?

---

### Post by PmDematagoda on 2008-02-10
You must print the commands since you cannot view pages using web browsers such as Firefox while using the CLI.

Concerning the blank screen, when you execute the command to kill the X-Server press Ctrl+Alt+F1 which will bring you to a tty where you can login and enter the rest of the commands.

---

### Post by drubin on 2008-02-10
mmmmmmm thanks for ponting that out...  I thought the CLI meant  i could juts use the terminal pompt.... 

Maybe something to remember when posting to newbies

---

### Post by drubin on 2008-02-10
Thanks for that, I did all that.  (wasn't as hard as i thought).

Now that worked fine for my old philips 17" crt, But i cant get the thing to use my LCD as the default for any res higher the 800x600.
LCD is
19" Wide screen
LG


I even tried re-doing all of those steps but why my CRT unpluged.. same issue, when i save the config. and restart the GUI it comes up with  Ubuntu's settings are ........ and then i have to re-configure it to use 800x600.

I am not sure if this makes a difference but my crt uses the VGA port on my graphics card and the LCD uses the DVI.

thanks for all the  help, just hoping we can get this to work, because if I cant at least have a screen that i can use i am going to have to go back..... :( :(

---

### Post by PmDematagoda on 2008-02-10
Did you try opening nvidia-settings using:-
```
gksudo nvidia-settings
```
and then doing the necessary changes?

---

### Post by drubin on 2008-02-10
Havent tried that...... but it allows me to change the settings, it saves them. 

But when i re-login to Ubuntu it tells me graphics error...... 

Does this mean that i have to try another distro?? cuz i just got into licking ubuntu.

---

### Post by drubin on 2008-02-10
Does linux normaly have a problem with DVI? in stead of VGA?

---

### Post by tcommbee on 2008-02-10
the problem is possibly that your graphics card internally uses the crt as primary device and lcd second. i know there is an option to set the order of outputs in xorg.conf, but i can't recall right now.. it must have to to with xrandr ... maybe google knows the exact option

---

### Post by vociferous666 on 2008-02-10
im having a very similar problem.  im on a laptop with an LCD panel that has a max res of 1280x800 with an s-video out connector.

my lcd screen always displayed at 1280x800 and never failed.

today i tried to enable the svideo connection as a secondary display by selecting a screen in the dropdown menu
this was done with the screens and graphics applet in the administration menu.
i tried to enable the screen but when i did i wasnt able to click the test button or the ok button.
then i restarted my laptop and i couldnt get my LCD to display in its native res. and my s-video still doesnt work.

i ran nvidia settings with sudo in terminal and it didnt give me the error writing file error when i hit save settings orwhatever the button is.

---

### Post by drubin on 2008-02-11
Hi guys i have tried every thing, almost every button. every cmd i can find still nothing.
[http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)
[http://ubuntuforums.org/showthread.php?t=693090&highlight=xrandr](http://ubuntuforums.org/showthread.php?t=693090&highlight=xrandr)
[http://www.causticmango.com/?p=27](http://www.causticmango.com/?p=27)

I just don't know where to turn any more.

Is it really this hard to get  LCD monitor working, i will even setting for not having dual for if it means i can use something more then 800x600.

also as tcommbee said i should change my internal config but i am NOT sure how/ where to do that. 

i have run  xrandr   this is what i get.

```
rubin@linuxpc:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600       100.0* 
   640x480       100.0  
```

xorg.conf
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

Section "Files"
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
	Identifier	"nVidia Corporation G71 [GeForce 7300 GS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Thank you for taking the time to help me, but surely Ubuntu cant be this hard to get my sceen working?

Rubin sitting staring at GIANT blocks (that juts happen to be pixels)

---

### Post by drubin on 2008-02-11
Not sure if this makes a difference but i found --verbose. 

```
 xrandr --verbose
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 (0x42) normal (normal) 0mm x 0mm
        Identifier: 0x41
        Timestamp:  162870460
        Subpixel:   no subpixels
        Clones:    
        CRTC:       0
        CRTCs:      0
  800x600 (0x42)   48.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   60.0KHz
        v: height  600 start    0 end    0 total  600           clock  100.0Hz
  640x480 (0x43)   30.7MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   48.0KHz
        v: height  480 start    0 end    0 total  480           clock  100.0Hz
```

---

### Post by drubin on 2008-02-13
Guess i am just going to have to change to a differnt distro of linux/ or back to windows?

Please any one else have  the same graphics card as me??  and gotten it to work? with a LCD on a DVI port?

---

### Post by incen on 2008-02-14
Mine is Nvidia GeForce 7600.
I have pretty much the same problem with setting up dual-screen. Now I'm still struggling with it. I posted one thread one or two days ago. You can search for that. Well... but it's not solved yet. I think it's not so good... :(

---

### Post by drubin on 2008-02-14
Hey could you get it to work with single screen  DVI ? (LCD) instead of VGA CRT?

---

### Post by incen on 2008-02-14
Hi, I followed PmDematagoda's instruction and it worked for me! Well... it's not at the first sense. However, trying to do what he said, then I got only single Analog Viewsonic VX922 screen working but with the right resolution finally! And then, I just went to Screen and Graphic to set it up again. It would ask you to log out. Then, I got two independent monitors working!!! It's quite a pain, I know, when not knowing how to do... :( I was checking with my friend's Suse machine with dual-screen for a long time.

---


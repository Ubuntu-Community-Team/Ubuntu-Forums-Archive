---
title: "Please save me from a reinstall"
date: 2006-08-04
forum: Desktop Environments
---

### Post by navymom on 2006-08-04
I had a problem with nothing showing up in the Add/Remove feature as available for my system.  I found out what that problem was.  It was an error on my part.  I *thought* I was only configuring updates and disselected everything in that menu except for security features.  When I went back and changed that, I could then install/remove applications again.  However, I'm still having a few quirky issues since installing updates.

What I am trying to do is get my system exactly like I want it then doing a complete system back up so in the invent I ever do have to restore my computer, I won't have to go through a ton of downloads again.

1. I am still unable to get Blender to work when it was working before.  This is the only program at the moment keeping me from a full switch from XP to Ubuntu.  When I click on the icon to start the program, nothing happens...I don't even get the little hour glass cursor letting me know it's even trying to open the program.  I have removed it and reinstalled it a few times.  This doesn't help.  This program does work on my system and I have used it in Ubuntu since I installed Ubuntu.

2.  When I attempt to download a file from a site, Firefox opens the dialog box asking me where I want to save it to.  I click the appropriate repsonses then the save button.  The dialog box closes and that's it.  Nothing more happens.

3.  I have no screensavers.  Prior to updates, they all worked.  Now none do.  This isn't a huge issue for me because my monitor just turns off after 20 mins idle.  But still it's something wrong and I would really like it corrected.

Any help would be appreciated.

Barbi

---

### Post by ardchoille on 2006-08-04
> **navymom said:**
> I had a problem with nothing showing up in the Add/Remove feature as available for my system.  I found out what that problem was.  It was an error on my part.  I *thought* I was only configuring updates and disselected everything in that menu except for security features.  When I went back and changed that, I could then install/remove applications again.  However, I'm still having a few quirky issues since installing updates.

What I am trying to do is get my system exactly like I want it then doing a complete system back up so in the invent I ever do have to restore my computer, I won't have to go through a ton of downloads again.

1. I am still unable to get Blender to work when it was working before.  This is the only program at the moment keeping me from a full switch from XP to Ubuntu.  When I click on the icon to start the program, nothing happens...I don't even get the little hour glass cursor letting me know it's even trying to open the program.  I have removed it and reinstalled it a few times.  This doesn't help.  This program does work on my system and I have used it in Ubuntu since I installed Ubuntu.

2.  When I attempt to download a file from a site, Firefox opens the dialog box asking me where I want to save it to.  I click the appropriate repsonses then the save button.  The dialog box closes and that's it.  Nothing more happens.

3.  I have no screensavers.  Prior to updates, they all worked.  Now none do.  This isn't a huge issue for me because my monitor just turns off after 20 mins idle.  But still it's something wrong and I would really like it corrected.

Any help would be appreciated.

Barbi

1. Run blender from a terminal and see if there is any output. Many times, running an app from a term can yield error output that helps solve the problem. I'm wondering if the problem here is with one of the user settings in the blender configs in your home folder.

2. If the file that Firefox downloads is small, or if you have a fast connection, that's all there will be. You need to open a file manager (nautilus?) and browse to the location where it saved the download. If you're not sure where the downloads are bing held.. open Firefox, click on Edit -> Preferences, go to the Downloads section and look in the Download Folder area to see where Firefox is downloading files. I have noticed that when I download small files, or from a fast server, the downloads dialog box doesn't even open up.. but the downloaded files was actually downloaded.

3. I'm not sure about screensavers, I don't use them.

---

### Post by navymom on 2006-08-04
1.  I don't know how to run blender from terminal...what's the commands for that?

2.  It was a large file and I am on dialup.  It would have remained open for at least 10 mins.  I've tried editting the preferences and have checked the d/l folder.  It's not putting anything there.  The only things I can save in Firefox are pictures by right clicking on them and saving the picture.  Downloading just does not work.

3.  I don't use them either but  my kids do.  So I'm trying every thing I can to make Ubuntu as wonderful to them as Windows.

---

### Post by ardchoille on 2006-08-04
> **navymom said:**
> 1.  I don't know how to run blender from terminal...what's the commands for that?

2.  It was a large file and I am on dialup.  It would have remained open for at least 10 mins.  I've tried editting the preferences and have checked the d/l folder.  It's not putting anything there.  The only things I can save in Firefox are pictures by right clicking on them and saving the picture.  Downloading just does not work.

3.  I don't use them either but  my kids do.  So I'm trying every thing I can to make Ubuntu as wonderful to them as Windows.

1. Try this: Open a term and type "which blender" (without the double quotes) and if that is the name of the binary, then the full path will be returned.. possibly something like /usr/bin/blender. Then take that path and type it into the terminal and hit the enter key.

2. You can always try closing Firefox, renaming ~/.mozilla to ~/.mozilla.bak, open Firefox again and set it up again, maybe the problem is messed up configs or something.. that has happened to me before.

3. Kudos to you for trying to make your kids' Ubuntu experience as enjoyable as possible :)
Good job!

---

### Post by navymom on 2006-08-04
Okay, here is what I get when I try the terminal thing:

```
barbi@ubuntu:~$ which blender
/usr/bin/blender
barbi@ubuntu:~$ /usr/bin/blender
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window
barbi@ubuntu:~$

```

so what can i do to fix it?

---

### Post by ardchoille on 2006-08-04
I think this may be of use to you:

[http://www.linuxquestions.org/questions/showthread.php?t=200313](http://www.linuxquestions.org/questions/showthread.php?t=200313)

If not, open Firefox, go to: [http://www.google.com/linux?hl=en&lr=&q=%22extension+%22GLX%22+missing+on+display+%22%3A0.0%22.%22&btnG=Search](http://www.google.com/linux?hl=en&lr=&q=%22extension+%22GLX%22+missing+on+display+%22%3A0.0%22.%22&btnG=Search)

Whenever I get any kind of error, the first thing I do is google it.

---

### Post by thingy on 2006-08-04
This is a common question on the forums...

> Xlib:  extension "GLX" missing on display ":0.0".

The above error simply means:

> 

If you are getting this error it means that the glx extension is not enabled in /etc/X11/xorg.conf. GLX allows blender to access your 3d card and draw to the screen, but some distributions ship with GLX disabled. It likely means that you just haven't got OpenGL installed or properly configured on your system. (It is also a symptom that you should review your 3D card setup in general).




All the above is simply saying is that the 3D drivers for your graphics card are not installed/setup on your system.



A) Do you know what type of graphics card is in you system? Is its manufacturer either NVIDIA or ATI? If you don't know then you can find out by doing this:

> 
lspci > ~/pci-devices.txt


The above will create a text file in your home directory called pci-devices.txt. Please attach it to your reply and someone here will tell you what graphics card you've got



B) If you do know what graphics card you have, and its either an ATI or NVIDIA card, then look at this to find out how to install its drivers:

The easy way of doing it:

1. Use EasyUbuntu to install the ATI or NVIDIA graphics driver. I.e. pick one of the following two options in EasyUbuntu:

- Nvidia: install the official driver to enable 3D on Nvidia graphics cards
- ATI: install the official driver to enable 3D on ATI graphics cards

Download EasyUbuntu from:
[http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html")


The official way of doing it:

[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")

jin

---

### Post by navymom on 2006-08-04
my computer doesn't have a graphics card.  it uses SIS integrated drivers.

---

### Post by thingy on 2006-08-04
Some SiS cards do support 3D...do you know which model you have? Look at the lspci output...it may say the graphics card model in there.


by the way...can you confirm that you did manage to run blender on this computer in the past? i.e. in linux

---

### Post by navymom on 2006-08-04
i can run blender in windows and i have ran it in ubuntu as well until i installed the updates.  since you mentioned the graphics card thing i believe now that is also what's causing the screensavers not to show up.  you know i can probably fix this with a lot of research but the next time i update the same crap is going to happen.  not only does it make it frustrating but it makes you dread updates for fear of hours of reconfiguring again.  yes, i could turn off the updates or just not download them but that isn't a solution either.  updates are necessary to ensure a secure system.  to me, this seems to be a problem that really needs to be addressed because not everyone is as stubborn as i am and would struggle with it.

here's the output:

```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:10.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

---

### Post by thingy on 2006-08-04
Assumption:

If the updates modified your /etc/X11/xorg.conf file, it will have made a backup of the file before modifying it...can you do a

> ls -l /etc/X11 

and paste the output...

I'm expecting one or more files that start with the letters "xorg.conf" (following by stuff)

---

### Post by navymom on 2006-08-04
here ya' go:

> barbi@ubuntu:~$ ls -l /etc/X11
total 76
drwxr-xr-x  2 root root  4096 2006-07-29 07:51 app-defaults
drwxr-xr-x  3 root root  4096 2006-07-29 07:36 config
drwxr-xr-x  2 root root  4096 2006-07-29 07:51 cursors
-rw-r--r--  1 root root    14 2006-08-02 06:17 default-display-manager
drwxr-xr-x  5 root root  4096 2006-07-29 07:34 fonts
lrwxrwxrwx  1 root root     6 2006-07-29 07:44 gdm -> ../gdm
-rw-r--r--  1 root root 17371 2005-12-21 20:00 rgb.txt
lrwxrwxrwx  1 root root    13 2006-07-29 07:39 X -> /usr/bin/Xorg
drwxr-xr-x  3 root root  4096 2006-07-29 07:46 xinit
drwxr-xr-x 10 root root  4096 2006-07-29 07:38 xkb
-rw-r--r--  1 root root  4314 2006-07-29 07:39 xorg.conf
drwxr-xr-x  2 root root  4096 2006-05-28 15:35 Xresources
-rwxr-xr-x  1 root root  3911 2006-03-20 07:29 Xsession
drwxr-xr-x  2 root root  4096 2006-08-02 22:25 Xsession.d
-rw-r--r--  1 root root   234 2006-03-20 07:29 Xsession.options
-rw-------  1 root root   614 2006-07-29 07:34 Xwrapper.config
barbi@ubuntu:~$


---

### Post by thingy on 2006-08-04
The xorg.conf file has last been modified on the 29/7/2006...

Is that when you had performed the update?

I also don't see any backup files!

Can you attach the /etc/X11/xorg.conf file to your reply please!

---

### Post by navymom on 2006-08-04
The updates I did over a course of a few days.  I'm not certain exactly what was updated on what day.  I'm on dialup (I know I know...but it's all we have available) so I had to do them a few at the time.  Here's a copy of the xorg.conf

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MX70"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	47-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Monitor		"MX70"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by thingy on 2006-08-04
SiS chipsets are difficult to get 3d working on...and most of them don't support it. You've confirmed that it was working before and so I will assume that its stopped working because of a config file change.

My suspicions are that:

a) The display/colour depth values in the config file could be causing a problem as res/depth eats up too much of the shared memory.

b) The sis driver may need options passed to it to get DRI and hence GLX to work.

I'll look at this problem again tom. morning/afternoon when I wake up...its 4.30am and i cant think at the moment!

Can you please attach the following files to your reply as I will need to look at them to find out what the X server is saying and what updates were installed.

Files: 

/var/log/Xorg.0.log
/var/log/dpkg.log
/var/log/dmesg


jin

---

### Post by navymom on 2006-08-05
thanks thingy...i really appreciate you trying to help but i just went ahead and reformatted and reinstalled.  everything is working like it should now and it taught me a valuable lesson.  in the future i will be more careful about the things i update....besides i guess it wasn't that much of a difficulty because i really hadn't installed that many things to ubuntu yet other than the updates and there were other things i had updated and installed that i didn't know how to get rid of...anyway, it's all looking good and i'm feeling a lot better now.

---

### Post by msandersen on 2006-08-05
> **navymom said:**
> I had a problem with nothing showing up in the Add/Remove feature as available for my system.  I found out what that problem was.  It was an error on my part.  I *thought* I was only configuring updates and disselected everything in that menu except for security features.  When I went back and changed that, I could then install/remove applications again.  However, I'm still having a few quirky issues since installing updates.
So, did you in effect uninstall something you shouldn't have?

> **navymom said:**
> 1. I am still unable to get Blender to work when it was working before.  This is the only program at the moment keeping me from a full switch from XP to Ubuntu.  When I click on the icon to start the program, nothing happens...I don't even get the little hour glass cursor letting me know it's even trying to open the program.  I have removed it and reinstalled it a few times.  This doesn't help.  This program does work on my system and I have used it in Ubuntu since I installed Ubuntu.

2.  When I attempt to download a file from a site, Firefox opens the dialog box asking me where I want to save it to.  I click the appropriate repsonses then the save button.  The dialog box closes and that's it.  Nothing more happens.

3.  I have no screensavers.  Prior to updates, they all worked.  Now none do.  This isn't a huge issue for me because my monitor just turns off after 20 mins idle.  But still it's something wrong and I would really like it corrected.

Any help would be appreciated.

Barbi
You do have GLX enabled, and seem to use the right driver, though I have no idea of its capability. You said it worked before though.
If you try this in the terminal
```
glxinfo | grep rendering
```
does it say **direct rendering: Yes** or produce errors? My guess is it complains. I'm not an expert however on how to fix it. You could try checking everything is upgraded and configured:
```
sudo apt-get upgrade && sudo dpkg --configure -a
```
I know it's supposed to resolve dependencies, but maybe there's something else. 
I had a problem when I upgraded which seem to have been fixed with the dpkg configure line, so you could try that on its own if you don't want to download lots of updates.
```
sudo dpkg --configure -a
```

---

### Post by navymom on 2006-08-05
Blender alive and well on my system after reinstall and no updates:

---


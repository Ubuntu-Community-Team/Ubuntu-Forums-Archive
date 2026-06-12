---
title: "N-Trig Digitizer Working (Partially)"
date: 2008-10-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ionman on 2008-10-03
I am so excited! I installed the latest beta of Intrepid on my Latitude XT today to find that the N-Trig digitizer is recognized and partially working. When I hover the pen over the screen, the cursor moves with it.

I need help getting a couple of things to work right, so I was hoping you tablet experts out there could help me. If I understand this right, although the tablet is not really a Wacom tablet, it still uses Wacom drivers. So, the question is, how do I configure this thing? In the older versions of Xorg there was always tablet stuff in my xorg.conf file, but in the beta of Intrepid, it's not there.

Here's what I need to change:

When the pen taps the screen no left-click is registered, and the cursor halts. I have to move the pen out of range of the screen and bring it back into range before the cursor moves again.

If I hold down the bottom button on my pen (normally does a right-click in Windows) and tap the screen it pastes from the clipboard. What's up with that!? Anyway, this is really coming along nicely. It just needs to be fine tuned a bit. Any help would be really appreciated.

Thanks!

- ionman

---

### Post by superm1 on 2008-10-03
> **ionman said:**
> I am so excited! I installed the latest beta of Intrepid on my Latitude XT today to find that the N-Trig digitizer is recognized and partially working. When I hover the pen over the screen, the cursor moves with it.

I need help getting a couple of things to work right, so I was hoping you tablet experts out there could help me. If I understand this right, although the tablet is not really a Wacom tablet, it still uses Wacom drivers. So, the question is, how do I configure this thing? In the older versions of Xorg there was always tablet stuff in my xorg.conf file, but in the beta of Intrepid, it's not there.

Here's what I need to change:

When the pen taps the screen no left-click is registered, and the cursor halts. I have to move the pen out of range of the screen and bring it back into range before the cursor moves again.

If I hold down the bottom button on my pen (normally does a right-click in Windows) and tap the screen it pastes from the clipboard. What's up with that!? Anyway, this is really coming along nicely. It just needs to be fine tuned a bit. Any help would be really appreciated.

Thanks!

- ionman
There is a patch out there for the wacom X driver that adds more support, but it's not perfect.

---

### Post by ionman on 2008-10-03
> **superm1 said:**
> There is a patch out there for the wacom X driver that adds more support, but it's not perfect.

Thanks. Any link/instructions? I have tried researching extensively already and not come up with much.

Thanks!

- ionman

---

### Post by nkri on 2008-10-05
If your tablet uses a Wacom digitizer, would you mind testing [_this_]("http://ubuntuforums.org/showthread.php?t=765915") howto in Intrepid and post results?  It would be a great help to me and I'm sure many other tablet users who want to make sure it works before they upgrade:)

Thanks!
-nkri

---

### Post by ionman on 2008-10-05
> **nkri said:**
> If your tablet uses a Wacom digitizer, would you mind testing [_this_]("http://ubuntuforums.org/showthread.php?t=765915") howto in Intrepid and post results?  It would be a great help to me and I'm sure many other tablet users who want to make sure it works before they upgrade:)

Thanks!
-nkri


Do you mean go through the whole recompile too? I am pretty sure Intrepid already has the latest version of wacom-tools, and usb-utils. I tried messing around with the xorg.conf file, but then it didn't want to show me a desktop anymore. :( That's why we always backup that file before we start changing it. Anyway, if I have some time later, I might try changing it again. I will let you know what I get.

Thanks!

- ionman

---

### Post by superm1 on 2008-10-05
Don't follow that howto for  intrepid.  Intrepid uses FDI files to enable devices not xorg.conf.  Also this is *NOT* a wacom digitizer.  It just happens to be similar and partially work with the wacom driver.

Here is the patch that partially enables wacom support further:
[http://ofb.net/~rafi/linuxwacom-0.8.1-3.ntrig_hack.patch](http://ofb.net/~rafi/linuxwacom-0.8.1-3.ntrig_hack.patch)

---

### Post by nkri on 2008-10-05
> **superm1 said:**
> Don't follow that howto for  intrepid.  Intrepid uses FDI files to enable devices not xorg.conf.  Also this is *NOT* a wacom digitizer.  It just happens to be similar and partially work with the wacom driver.

Here is the patch that partially enables wacom support further:
[http://ofb.net/~rafi/linuxwacom-0.8.1-3.ntrig_hack.patch](http://ofb.net/~rafi/linuxwacom-0.8.1-3.ntrig_hack.patch)

Do you think it would work for my Toshiba M400 Tablet PC which does have a Wacom digitizer?  That howto worked for me in Hardy, and I don't wanna upgrade until I'm sure it'll work in Intrepid.  Any suggestions?

Thanks!
-nkri

---

### Post by superm1 on 2008-10-05
> **nkri said:**
> Do you think it would work for my Toshiba M400 Tablet PC which does have a Wacom digitizer?  That howto worked for me in Hardy, and I don't wanna upgrade until I'm sure it'll work in Intrepid.  Any suggestions?

Thanks!
-nkri
Grab the intrepid beta live CD and try :)  That way you won't have to wipe anything.

---

### Post by ionman on 2008-10-30
Well, I actually worked on this a bit today and made some progress. I can now get the tablet pen to tap and right click if I follow the guide posted here: [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting).

The only trouble is, now I can't do desktop composition. I think after I modified the xorg.conf file, it no longer uses the ATi accelerated driver. Here is my full xorg.conf file:

```

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	#Disable	"dri2"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"      
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

```

Is there a way that I can use an FDI file for this info so I can keep using device autodetect? I think that is what is messing it up. I could be wrong on that though. Thanks for any help you can offer!

- ionman

---

### Post by ionman on 2008-10-30
Ok, I discovered my compiz problems were completely unrelated, so I am working on that separately.

What I did discover is that when I move the pen over the screen (with the above xorg.conf) the cursor does not track with the pen. I can move then pen left, and the cursor moves left, but at a different speed. Sometimes it's slower, and sometimes it's faster. Also when the pen comes near the screen the cursor jumps to some seemingly unpredictable location on the screen.

Does anyone have any suggestions as to how to fix this? I am about out of ideas.

Thanks!

- ionman

---

### Post by m_sarna on 2008-11-07
Hi, I'm trying to run N-trig's digitalizer for few days now. 
My touch screen is working fine with pen (speed is ok) but without any buttons and no hand touching. 

My xorg.conf for Dell Latitude XT

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Option		"Mode" "Absolute"
    Identifier	"touch"
    Option     	"Type" "touch"
    Option        	"ForceDevice" "ISDV4"               # Tablet PC ONLY
    Option 		"Device" "/dev/input/event3"
#    Option 		"Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
    Option 		"TopX" "0"
    Option 		"TopY" "0"
    Option 		"BottomX" "9600"
    Option 		"BottomY" "7200"
    Option 	"USB"  "on"
#    Option	"Button0"	"0"
#    Option	"Button1"	"1"
#    Option	"Button2"	"2"    
#    Option	"Button3"	"3"    
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option	"Mode"	"Absolute"
#    Option "Device" "/dev/input/event3"
  Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option 		"TopX" "0"
    Option 		"TopY" "0"
    Option 		"BottomX" "9600"
    Option 		"BottomY" "7200"
    Option 	"USB"  "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option       	"Type"          "eraser"
    Option		"Mode"	"Absolute"
    Option        	"ForceDevice" "ISDV4"               # Tablet PC ONLY
#    Option "Device" "/dev/input/event3"
    Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
    Option 		"TopX" "0"
    Option 		"TopY" "0"
    Option 		"BottomX" "9600"
    Option 		"BottomY" "7200"
    Option 	"USB"  "on"
EndSection
                
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0

        InputDevice    "touch"  "SendCoreEvents"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "extmod"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

For some more help look at: 
[http://ofb.net/~rafi/latitude_xt.html](http://ofb.net/~rafi/latitude_xt.html)
and
[http://linuxwacom.sourceforge.net/index.php](http://linuxwacom.sourceforge.net/index.php)

All best.

---

### Post by indvdoom on 2008-11-11
Have the same exact problem on my XT. Somebody please hack the damn thing already! :) people need ya!

---

### Post by swissmade on 2008-11-17
Hi,

I made it work. You can follow these informations on [http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77]("http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77") this website has been updated.

You can also use the french wiki [http://doc.ubuntu-fr.org/dell_latitude_xt]("http://doc.ubuntu-fr.org/dell_latitude_xt")

Have fun

---


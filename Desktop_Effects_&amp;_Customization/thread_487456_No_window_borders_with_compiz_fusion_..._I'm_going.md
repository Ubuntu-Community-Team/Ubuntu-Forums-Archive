---
title: "No window borders with compiz fusion ... I'm going crazy"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by dwebb86 on 2007-06-29
Ok....
I've been screwing with this for about 2 days now trying to get Compiz Fusion to work, getting a huge headache. 
I have both Compiz Fusion and Emerald installed. I can access the CompizConfig Settings Manager and the Emerald Theme Manager in my preferences menu.

When I enter the command **compiz --replace c- emerald &** into the terminal, I get this.

Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: ''Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'c-'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing minimize options...done

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)
Initializing move options...done
Initializing place options...done

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8107): Wnck-WARNING **: Unhandled action type (nil)
Initializing resize options...done
Initializing wobbly options...done
Initializing zoom options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done
Active Plugin List update

... and the terminal hangs. 
I can enter this in an ALT+F2 box as well though and don't have to use a terminal. 

when I do this, it turns on Compiz Fusion, and I can enter the CCSM and play with the effects... as far as I know all of them work fine. 
my problem is I have no window borders. 
I can navigate through windows using the panels and key shortcuts, but I can't move/drag them or resize them, the borders just are not there. 

I've tried doing the commands separately as **compiz --replace** and **emerald --replace &** and nothing happens. The only way I've ever been able to get compiz to actually load is using **compiz --replace c- emerald &** and it won't even load if I put this in my Sessions manager and restart. 

Since yesterday I've been scouring the forums here on ubuntu and in opencompositing.org and can't find any solution that works. 
If you need any more info about how certain commands react when entered or whatever, just ask.

---

### Post by hyperair on 2007-06-29
I believe the command is "compiz --replace -c emerald &" as opposed to "c-". Anyway emerald seems to have loaded, based on the output you have given. And what do you mean by the terminal hangs? Try pressing enter and see what happens?

Also you might want to update. I reckon I'm using the most up to date version from Trevino's repository and I certainly don't have the "couldn't load plugin c-" and "couldn't load plugin emerald"

After you run the command what happens? Is compiz running? Try pressing Alt and scrolling down on a window. Does the opacity change? Can you drag the windows around with Alt+Click-drag? Can you resize the windows with Alt+MiddleButton-drag?

You don't have window borders.. Could you try "emerald --replace &" on a terminal and see if it has any effect? Also please post the output of "emerald --replace &" here.

---

### Post by dwebb86 on 2007-06-29
I know I've read all over the place that the command is **compiz --replace -c emerald &**... but this does not work for me. When I use the command with c- instead... Compiz immediately loads and I can go into the options and screw with them... rotate the cube, draw fire on my screen, wobble windows, etc. etc. ... but there are no window borders.
So yes, using c- seems to work just fine. 

Also, I installed compiz and emerald yesterday, so they are the most recent ones.

yes, I can drag the windows around with Alt+Click-drag. the other alt+ commands seem to work (except I have no middle button because I'm not using a usb mouse yet)... but still no window borders. 

running **emerald --replace &** in the terminal gives me this message about 20 times, and nothing else:
(emerald:7288): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by catanzag on 2007-06-29
I've got a similar problem (though I got it with gconf backend and with the default gtk-window-decorator), which was solved upgrading the libdecoration0 with the last version (I think from the same 3vin0 repository) as suggested in one of 3vin0 blog comments:

```
$sudo apt-get install libdecoration0
```

regards

catanzag

---

### Post by dwebb86 on 2007-06-29
this just gives me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdecoration0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libsoundtouch1c2 libjack0.100.0-0 libgsm1 libcdaudio1 libmpcdec3
  libmms0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


so, my libdecoration0 is already the most recent. 
I installed all this stuff yesterday so none of it should be out of date.

---

### Post by catanzag on 2007-06-29
oops, sorry, that was enough for me, and I had the same symptoms you had.

I can suggest only another possible check; have you already had installed Compiz or Beryl before and they works fine? A friend of mine got a similar problem with Beryl due to depth set to 16 instead of 24 (as it is correct) in xorg.conf

---

### Post by dwebb86 on 2007-06-29
nah, no need to apologize for trying to help. 
anyways,  I just got this computer a week or so ago and just installed Compiz yesterday, and have never installed beryl. 
I already read multiple threads about the 16 > 24 thing and have tried it both ways. it's set to 24 now (what it was at originally) and I'm still looking for a solution.

Anyone else want to take a shot at it? this is really annoying me, I'll try anything.

---

### Post by dwebb86 on 2007-06-29
nah, no need to apologize for trying to help. 
anyways,  I just got this computer a week or so ago and just installed Compiz yesterday, and have never installed beryl. 
I already read multiple threads about the 16 > 24 thing and have tried it both ways. it's set to 24 now (what it was at originally) and I'm still looking for a solution.

Anyone else want to take a shot at it? this is really annoying me, I'll try anything.

---

### Post by robertc36 on 2007-06-29
I had the same problem myself.
The workaround for me was to remove emerald from startup.
Strange thing when i restarted i had borders and emerald was there as well.
I was quite prepared to live without it and it worked anyway.

---

### Post by dwebb86 on 2007-06-29
nah, no need to apologize for trying to help. 
anyways,  I just got this computer a week or so ago and just installed Compiz yesterday, and have never installed beryl. 
I already read multiple threads about the 16 > 24 thing and have tried it both ways. it's set to 24 now (what it was at originally) and I'm still looking for a solution.

Anyone else want to take a shot at it? this is really annoying me, I'll try anything.

---

### Post by mid_night gypsy on 2007-06-29
dwebb86,
 I wonder if you have your xorg.conf setup right and you video driver installed(e.g. ati,nvidia), also try installin' libdecoration0-dev. You do have emerald and emerald theme manager install? Sometimes it's the simple things that we forget. Hope this helps,gypsy
 ```
sudo apt-get install libdecoration0-dev
```

---

### Post by dwebb86 on 2007-06-29
nah, no need to apologize for trying to help. 
anyways,  I just got this computer a week or so ago and just installed Compiz yesterday, and have never installed beryl. 
I already read multiple threads about the 16 > 24 thing and have tried it both ways. it's set to 24 now (what it was at originally) and I'm still looking for a solution.

Anyone else want to take a shot at it? this is really annoying me, I'll try anything.

---

### Post by Bluecube on 2007-06-29
I had conflict problems between the new version of CompizFusion and an old version I had. I loaded up Synaptic and was able to filter out any broken packages (cause there was a Broken option in the side window) and completely remove them. A quick apt-get for compizfusion and bingo! I was sorted. Of course, if you've no broken packages then this is no use!

---

### Post by hyperair on 2007-06-29
Let's see.. you're sure you're using Compiz Fusion right? Installed from Trevino's repository? And Emerald? Is your Emerald installed and up to date from there too?

Your emerald should be version: 0.3*
And your Compiz should be version: 0.5*
And you should have all the compiz-fusion* packages installed.

---

### Post by dwebb86 on 2007-06-29
oops. I was having superslow internet problems and hit refresh a few too many times on that "post reply" page. 

anyways... I have changed my xorg.conf file a few different ways. None of them did anything for me, I think. I'll post the file here... let me know if you guys see anything I should change that will help. 

also, yes, I have emerald and the theme manager installed. this commands returns:
[B]emerald --version                                     
emerald: emerald version 0.3.0-svn
[/B]
and I can open the theme manager and screw with options, even though I can't seem to get it to do anything by itself. 

**sudo apt-get install libdecoration0-dev** returns:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdecoration0-dev

and here's my xorg.conf file for your viewing pleasure:

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"
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
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Hopefully someone can solve this, I do hope it's one of the easy things.

---

### Post by hyperair on 2007-06-29
AHa! So that's where the problem is (I think). These two lines:
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```

They belong in the Screen section, not the Device section. Change it and restart your X server.Hopefully that works =)

---

### Post by dwebb86 on 2007-06-29
To answer the above post... my compiz is version 0.5.1 as you can see in the command entered in the terminal below:      -even though I have no idea why the emerald warnings-

XXX@XXX:/XXX/XXX# compiz --version
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: ''Checking for nVidia: present. 
Checking for Xgl: not present. 
compiz 0.5.1
XXX@XXX:/XXX/XXX# 
(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11618): Wnck-WARNING **: Unhandled action type (nil)


also, the post I made above this one has the results of the **emerald --version** command, which is also current. 

also, I did a search for 'compiz' in synaptics package manager and I have everything installed that I can with the name compiz in it. 

any other ideas? (please read all my posts in this thread before proposing an idea)
thanks for any attempts to help, it seems my installation of compiz fusion will be brimming over into at least 2 full days now... lol.

---

### Post by hyperair on 2007-06-29
Meh. I suppose you didn't see my previous post? The one about the arg glx visuals thing in xorg.conf? Look again, willya.

---

### Post by kpolice on 2007-06-29
The warnings can be safely ignored and won't prevent Compiz from running.

---

### Post by mid_night gypsy on 2007-06-29
howdy,
 I just got off work, and readin' the post here. Still no luck, darnnit. I look at my xorg.conf and takin' a guess I think your two options are cancelling each other out and emerald is fighting a losing battle. Please, In your xorg.conf comment out with a # in front of the option line like so....The # in front of a line means it's not read or ran, and yes these options do belong in your device section it tells in your case your Nvidia card what to do not your monitor. Also, sometimes when you have problems these options will be under screen section, just re-edit when that happens. hope this helps,good luck
```
#Option "AddARGBVisuals" "True"
```

---

### Post by dwebb86 on 2007-06-29
hey guys, 
thanks so far to all who've tried to help, yet, still no luck.

I tried adding those options to my xorg.conf like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
        Option "AddARGBVisuals" "True"
        Option "AddARGBGLXVisuals" "True"
	Defaultdepth	24

and that didn't work.

I also tried commenting out **Option "AddARGBVisuals" "True"** with #
that didn't work either. I'm about to go remove the options from my screen menu and keep the other option commented out and restart my X ... but I don't think that'll work. I'll post again in 5 minutes if it does, and if I don't post again, I'm still having problems. 

any other ideas? 

it's getting to the point where I've screwed around enough with compiz on and no window borders that I am getting used to navigating around without them. 
If I can't figure this out, I might just do that... but there has to be a solution for it...

---

### Post by mid_night gypsy on 2007-06-29
dwebb86,
 Man I'm stupid, it took a couple of times lookin' at your xorg.conf. But I think I got it Clyde, Please try this...
Remove this or comment it out # .....I don't have it.
 ```
Section "DRI"
Mode 0666
EndSection

```
 and add this line in it place at the bottom.
 ```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```
 again good luck,gypsy

---

### Post by dwebb86 on 2007-06-29
nope, no luck.
wow this is a headache. I wish some super compiz wizard would just come along and say "poof, your compiz is fixed!"

anyways, I tried the above. My xorg.conf looks like this now:
(I un-commented that line back in since it didn't do anything to remove it)


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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"
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
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

you think maybe it's not the xorg.conf? 
it might be, I have no idea really, it seems I've tried everything except exactly what will fix it.
any ideas (or a straight out solution) will be appreciated.

---

### Post by dwebb86 on 2007-06-30
anyone? c'mon, there has to be a solution.. . someone out there knows what I need to do...

---

### Post by Mr Greencastle on 2007-06-30
This may sound stupid, but I had the same problem as you, and I fixed it by doing these two separate in startup sessions.

Name: Compiz
Command: compiz --replace

Name: Emerald
Command: emerald --replace  (notice the no '&' thing? that might be something, I don't know)

That was THE ONLY thing that worked for me, hope that helps you!

Good luck,

Mr Green

Another stupid question: Have you checked that you have the 'Window Decorations' option enabled in CCSM?

---

### Post by Stir on 2007-06-30
I had the same problem. Fixed it by adding:

Section "Extensions"
Option "Composite" "Enable"
EndSection


My xorg.conf

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2223W"
    HorizSync       31.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: 1280x1024 +1680+0; DFP-0: 1400x1050 +0+0, DFP-1: nvidia-auto-select +1400+0; DFP-0: 1280x1024 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1024x768 +0+0, DFP-1: nvidia-auto-select +1024+0; DFP-0: 832x624 +0+0, DFP-1: nvidia-auto-select +832+0; DFP-0: 800x600 +0+0, DFP-1: nvidia-auto-select +800+0; DFP-0: 640x480 +0+0, DFP-1: nvidia-auto-select +640+0"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by swoll1980 on 2007-06-30
> **dwebb86 said:**
> nah, no need to apologize for trying to help. 
anyways,  I just got this computer a week or so ago and just installed Compiz yesterday, and have never installed beryl. 
I already read multiple threads about the 16 > 24 thing and have tried it both ways. it's set to 24 now (what it was at originally) and I'm still looking for a solution.

Anyone else want to take a shot at it? this is really annoying me, I'll try anything.

I just had the the same problem I was trying to figure this out forever turns out I had the window decoation box unchecked I don't think  anybody else is as dumb as me, but just in case.  :p

---

### Post by vishnu on 2007-06-30
**Where would I find the window decoration box.**  I'm pulling my hair out here.  Had 3d working perfectly and decided to re-install feisty.  I don't see window borders when I enable 3d effects.  I've not installed beryl and don't want to.  I want to use the standard built in effects.  

**Do I need Emerald installed cos I don't have it installed right now.**  But that tick box might my answer if I kenw where to find.  Any help would be greatly appreciated.  

**Here's my xorg.conf**  (I tried the Composite true thing and no luck so I took it out.

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
	Load		"extmod"deb file
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
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option          "AllowGLXWithComposite" "true"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
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

---

### Post by hyperair on 2007-06-30
I'd suggest removing the DRI thing. Also remove the AddARGBVisuals line. the AddARGBGLXVisuals, shift it to your "scrreen" section instead. 

Also, if it helps, these two commands work for me (starting from scratch):
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig --add-argb-glx-visuals

```

---

### Post by vishnu on 2007-06-30
No luck I get the same results.  Where's the above mentioned Windows Decoration tick box?
Here's the new Xorg.conf

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

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
#Section "DRI"
#	Mode	0666
#EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "AddARGBGLXVisuals" "True"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by hyperair on 2007-06-30
Go to CompizConfig Settings Manager. In the search box, type decoration. Make sure that plugin is enabled. Also, for the command, put "emerald --replace" without quotes.

---

### Post by swoll1980 on 2007-06-30
lllllll

---

### Post by Kubunteando on 2007-06-30
Have you tried to install gnome-compiz-manager?

[http://compiz.org/Gnome_Compiz_Manager](http://compiz.org/Gnome_Compiz_Manager)

I have only problems with white borders in maximized windows.
I had the same issue with Beryl. If I start compiz using gnome-compiz-manager (right-clicking on the icon and enabling the desktop GL) I have the borders right.

But unfortunately, the setting do not seem to work, I have only the default settings.

---

### Post by vishnu on 2007-06-30
YES!! Installing Gnome-compiz-manager worked!!  Many thanks

---

### Post by dwebb86 on 2007-06-30
hey again all.

here's some more shoot-downs for potential solutions to my problem. 

I already tried using       compiz --replace 
and                                    emerald --replace   (both with and without the &)
on my sessions startup.
didn't work.

I also DO have the window decorations on, so that's not it.

and, someone told me to add:
Section "Extensions"
Option "Composite" "Enable" 
or whatever to my xorg.conf... and if they had looked up a couple posts, it's already in there. 

anyways, I'm going to try the gnome compiz manager thingy, haven't tried that one yet, my apt-get update is running right now, I'll post again in a minute if it does the trick.

otherwise, keep throwing ideas out there.

someone should compile all the solutions (there's so many) in this thread as a sticky and throw them on the main Desktop Effects & Customization page,.. alot of people seem to have this problem.

ok so... here we go ::crosses fingers::

---

### Post by dwebb86 on 2007-06-30
gnome compiz manager didn't work. 

we're running out of options here... any other ideas?

I'm about to start using compiz without window borders, this is getting tiring.

---

### Post by mpeters on 2007-06-30
> **dwebb86 said:**
> nope, no luck.
wow this is a headache. I wish some super compiz wizard would just come along and say "poof, your compiz is fixed!"

anyways, I tried the above. My xorg.conf looks like this now:
(I un-commented that line back in since it didn't do anything to remove it)


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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"
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
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

you think maybe it's not the xorg.conf? 
it might be, I have no idea really, it seems I've tried everything except exactly what will fix it.
any ideas (or a straight out solution) will be appreciated.

I know you've tried lots of things so far, so apologies if I'm repeating something you've already tried, but here's what solved the problem for me. In your "Device" Section, comment out/remove the lines:

Option		"AddARGBVisuals"	"True"
Option		"AddARGBGLXVisuals"	"True"

And add the following to your "Screen" section after the line "Defaultdepth	24":

    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True" 

Restart X, log in and run compiz-manager. Note:  AddARGBGLXVisuals not AddARGBVisuals (or at least that's what works for me)

I hope this helps

---

### Post by dwebb86 on 2007-06-30
hey guys, 
yeah, so before I read that last post, I decided to re-install my OS and compiz and everything, to see if I could get it to work. (didn't have anything on this computer anyways, just got it a week ago)

so, I'm in the middle of sudo apt-get upgrade, and I'm going to start again... I'll try everything posted here all over again.

if anyone read all the previous posts and has any new ideas for me, go ahead and shoot.

wow, I've never had one application be such a pain in the *** to install.
linux surely does have a bit of a learning curve.

---

### Post by vishnu on 2007-07-01
How do I get the windows to not stick to the gnome panels and the sides of teh screen.  really annoying.

---

### Post by dwebb86 on 2007-07-02
heyyyyy guys. 
so yeah. I got it working. 
this is what I did in order... not sure exactly what made it all fit together (actually, it's still not perfect, but I'll get to that)

I re-installed Ubuntu 7.04
updated my nvidia-glx driver (which screwed up a few times, but works now)
rebooted
added the stuff for compiz to sources.list
did sudo apt-get update
installed emerald
installed compiz
edited /usr/bin/compiz to say "emerald" where highlighted (I just made this step up myself, didn't get it from any forum)
................
####
# Starts one decorator per screen
function start_decorators
{
	if ( [ -z "$DECORATOR" ] && [ -z "$RUNNING_COMPDECORATOR" ] ); then
	case "$DE" in
		KDE)
			DECORATOR="kde-window-decorator"
			DECORATORARGS="--replace"
		;;
		GNOME)
			DECORATOR="gtk-window-decorator"
			DECORATORARGS="--replace"
		;;
		*)
			DECORATOR="**emerald**-window-decorator" #emerald?
			DECORATORARGS="--replace"
		;;
**######....................and**
        if ! (xdpyinfo | grep -q "^focus:[ ]\+PointerRoot$"); then
		WMRUNNING="true"
	fi

	STD_COMPDECORATORS="**emerald**-window-decorator kde-window-decorator emerald yald"

	for deco in $STD_COMPDECORATORS; do
		if pidof $deco &> /dev/null; then
			RUNNING_COMPDECORATOR="$deco"
			break;
		fi

and went into CCSM and went to "Window Decoration" and changed **command** to **emerald-window-decorator**

then ran **sudo apt-get upgrade**

then ran **emerald --replace c- emerald &**

AND IT WORKED!

yeah, so it works now. except for the fact that I can't go into the "Animations" button on my CCSM, I think it's a bug, I click on it and it gets rid of all the Icons in the window and doesn't go into the Animations options area.

also, I can't get compiz to run on startup, I haven't searched alot for this on forums yet, but maybe you guys can help.... compiz --replace and emerald --replace or compiz --replace c- emerald &  added to the sessions manager don't work.

thanks for all your help guys... compiz rocks.

---

### Post by hyperair on 2007-07-02
Firstly, it was never "compiz --replace c- emerald". It was "compiz --replace -c emerald". Secondly, instead of changing the compiz wrapper script, you should just add "emerald --replace" to the command for the window decorator in window decorator plugin in CompizConfig Settings Manager. Your way works of course, but it's very hack-ish.

After the above steps then you can just add "compiz --replace" to your sessions manager. Emerald should automatically start itself up.

---

### Post by dwebb86 on 2007-07-02
"Firstly", I've said many times in this forum that **compiz --replace -c emerald &** doesn't work for me and I've had to use **c-** (don't ask me why, it just works, and the other way doesn't)

"Secondly", nobody has told me once to add **emerald --replace** in the command entry in Window Decoration of CCSM, so I made my own way.

Also, I said in the post right before yours that **compiz --replace** and the other commands (read the post) didn't work with Sessions manager.

Thanks for all your help though.
Thanks to everyone... 
someone should make a sticky thread for possible solutions of the "No Window Borders" topic because so many people have it in different ways.

---

### Post by Scotty Bones on 2007-07-03
Hi guys,
I've been having the exact same problem, but after reading through this thread my issue is now resolved.
The solution for me:

1. Xorg.config -added

Section "Device"
Option "AddARGBGLXVisuals" "True"

and

Section "Extensions"
Option "Composite" "Enable" 

2. CCSM

Window Decoration was already enabled.  Just changed the GTK to Emerald (emerald --replace)

3. Resatarted X, and sweet, my 4 day and 2 reinstall ordeal is now over.

Thanks a lot for the great info.  You guys have helped a ton.

---

### Post by dwebb86 on 2007-07-03
Heh, glad this thread helped more people out, I said it a couple times that they should make this one a sticky, or at least compile a list of the solutions we have here and sticky that so people can find them easy, it seems like 10% or so of all the threads on this place are "My window borders won't show up" stuff. 
how would I get this to be a sticky? or can someone else do it?

---

### Post by dwebb86 on 2007-07-04
bumping this thread up since alot of people seem to be asking questions about this topic.

---

### Post by thor27 on 2007-07-07
Even trying most of what is written here, it seems it still doesnt works on my computer.


Anyway, I could make beryl works with borders setting in beryl-manager (freely translated from portuguese) "Advanced beryl options" -> "renderization path" -> "copy"

and them the borders shows up (aquamarine)

but I don't know where to set this in compiz....any ideas?

---

### Post by hyperair on 2007-07-08
The command to start Compiz.. Instead of using ```
compiz --replace
``` use ```
compiz --replace --use-copy
```. If you use the code that starts emerald with it, ```
compiz --replace -c emerald
``` use this instead: ```
compiz --replace --use=copy -c emerald
```.

---

### Post by lenaubry on 2007-07-08
> **hyperair said:**
> Go to CompizConfig Settings Manager. In the search box, type decoration. Make sure that plugin is enabled. Also, for the command, put "emerald --replace" without quotes.


Thanks alot! that solved my problem

[And this thread for ATI users]("http://ubuntuforums.org/showthread.php?t=488385&highlight=install+compiz")

---

### Post by firmwire on 2007-07-08
lenaubry and anyone else that can help :-),

> **lenaubry said:**
> Thanks alot! that solved my problem

[And this thread for ATI users]("http://ubuntuforums.org/showthread.php?t=488385&highlight=install+compiz")

Hey... do you happen to know if you had the same error as below, before you fixed your issue?

> **rax_m said:**
> Hi, 

Some automatic updates came through for compiz fusion recently and since then whenever I start it I lose my window borders and title bars. Running from the terminal I get the following:

```

rmistry@rmistry-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

```

Anyone know how this could be fixed? I already have AddARGBGLXVisuals in my xorg.conf file. 

Thanks
Rax


I will be doing a fresh install tonight, and if I need to I will try that decorations option. I KNOW I haven't done that one yet or the --use=copy option.  Hopefully I can get compiz fusion to work again with no issues.

---

### Post by thor27 on 2007-07-09
> **hyperair said:**
> The command to start Compiz.. Instead of using ```
compiz --replace
``` use ```
compiz --replace --use-copy
```. If you use the code that starts emerald with it, ```
compiz --replace -c emerald
``` use this instead: ```
compiz --replace --use=copy -c emerald
```.

With --use-copy, I receive: 

/usr/bin/compiz.real (core) - Warn: Unknown option '--use-copy'

and with --use=copy, I receive

/usr/bin/compiz.real (core) - Warn: Unknown option '--use=copy'

---

### Post by hyperair on 2007-07-09
Strange. I hear it worked sometime back. Now it doesn't. Anyway why are you so sure you need the use copy?

---

### Post by thor27 on 2007-07-09
I'm not sure...

I'm just saying that the only way that worked here was changing this option (with beryl).... without that I get no borders at all...

I've already tryed many different decoration engines, did many changes in xorg.conf and everything else I could find in this thread with no luck....

---

### Post by DaveTRG on 2007-07-11
I had this same problem and changing my color depth fixed it.  I changed the following in /etc/X11/xorg.conf

DefaultDepth     16

to

DefaultDepth     24

After this is changed you'll want to restart gdm by going to a terminal session (Ctrl + Alt + F2 for example), and typing the following:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

In Kubuntu, use kdm in place of gdm there.

Hopefully this helps someone.

---

### Post by KyleYankan on 2007-07-12
I have this same issue on Gutsy Gibbon. However, I do not have emerald installed. It won't install either

```


The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not going to be installed
E: Broken packages


```


Any clue? I' really like to have my 3D cube. I miss it :-(

---

### Post by hyperair on 2007-07-12
I use Feisty at the moment, but could you try posting the output of ```
sudo apt-get install libwnck18
```

---

### Post by flexer on 2007-07-12
Here is a fix that worked for me:

UBUNTU > SYSTEM > PREFERENCES >   GL DESKTOP > Uncheck: USE METACITY THEME

Also try:

UBUNTU > SYSTEM > PREFERENCES > Compiz Config Settings > check: Place WIndows 
(in Place Windows settings select: Placement Mode - Centered)

---

### Post by KyleYankan on 2007-07-12
> **hyperair said:**
> I use Feisty at the moment, but could you try posting the output of ```
sudo apt-get install libwnck18
```

Sure. Here's the good stuff:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck18: Depends: libwnck-common (< 2.19) but 2.19.5-0ubuntu3 is to be installed
E: Broken packages

```

---

### Post by hyperair on 2007-07-12
Hmm, Ubuntu Gutsy is certainly fascinating. Dependency problems eh? Could you go to Synaptic Package Manager and see if you can lock the version of libwnck-common at 2.18-** and then install libwnck18?

---

### Post by KyleYankan on 2007-07-12
> **hyperair said:**
> Hmm, Ubuntu Gutsy is certainly fascinating. Dependency problems eh? Could you go to Synaptic Package Manager and see if you can lock the version of libwnck-common at 2.18-** and then install libwnck18?

that worked for installing libwnck18, and emerald installed.

However, a few of my icons are missing now (power-manager). I'll work on that later.

However, Compiz still does not work.

---

### Post by hyperair on 2007-07-12
Ok, so what's the problem this time? While you're at it please tell me the version of your Emerald:
```

apt-cache policy emerald

```
and
```

emerald --version

```

---

### Post by KyleYankan on 2007-07-12
> **hyperair said:**
> Ok, so what's the problem this time? While you're at it please tell me the version of your Emerald:
```

apt-cache policy emerald

```
and
```

emerald --version

```

Here it is:

> 
kyle@Brandy:~$ apt-cache policy emerald
emerald:
  Installed: 0.3.0+git20070621~3v1ubuntu0
  Candidate: 0.3.0+git20070621~3v1ubuntu0
  Version table:
 *** 0.3.0+git20070621~3v1ubuntu0 0
        500 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
        100 /var/lib/dpkg/status
kyle@Brandy:~$ emerald --version
emerald: emerald version 0.3.0-svn
kyle@Brandy:~$ 


I forgot that I added the tuxfamily.org repository, so I checked it out and there is no emerald packages in Gutsy of Fiesties repositories for me.

---

### Post by jaffamuffin on 2007-07-18
Hi all


Running Gutsy Gibbon here, 2 screens (twinview) and nvidia 7800GTX and was having problems getting Window Decorations working with Compiz. Also the keyboard kept not working forcing me to hard reset (i can't ssh in at the moment)


NOT ANYMORE!  YAY!

After adding 
Section "Device"
 Option "AddARGBGLXVisuals" "True"
 
Section "Extensions"
 Option "Composite" "Enable" 

to xorg.conf
and

then restarting X, logining in and typing (as normal user)

compiz --replace  (gave me compiz with normal borders)
and then emerald --replace (gave me funky emerald awesomeness)

Just to set it up default now. I have ubuntu and KDE installed here not tried in Gnome yet.

Here's my xorg conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:56:28 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 121.0
    VertRefresh     48.0 - 160.0
    ModeLine       "1920x1200" 232.6 1920 1984 2184 2456 1200 1202 1206 1263 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    Option 	   "AddARGBVisuals" "True"
    Option	   "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1920x1200_75 +0+0, DFP: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
     Option  	   "Composite" "Enable"
EndSection




```


One thing I ask though:

This error/warning:
```

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Is it serious and will it prevent me from doing anything (video related, watching movies / video editing?)


edit to add I'm using only the repos that come setup with gutsy, I haven't added anything. My setup is stock. Even my xorg conf was generated by nvidia-settings (bar my above additions) Ubuntu really does seem to be 99.5% GUI so far. Excellent.

Cheers all

---

### Post by hyperair on 2007-07-18
Doubt it. Try playing a video just to be sure. Use MPlayer or Totem.

---

### Post by jaffamuffin on 2007-07-18
Nah, works fine no problems at all. Fusion is sweeeeet.  Forgot to mention I'm running 64 bit Ubuntu, I think some peeps were having probs with 64 bit builds.

---

### Post by misfitpierce on 2007-07-18
I took 64 bit off but now that I hear its running on 64 bit I may format back to 64 bit when gutsy releases... But yes im very happy with fusion so far seems to run smoother than Beryl

---

### Post by puppy on 2007-07-18
Hmm, just dist-upgraded to Gutsy but obviously had to remove all but the standard repos. 

The problem I'm having is that Emerald is nowhere to be found, although compiz-fusion is an official package - therefore I get no window borders because no emerald package is available... 

Does anyone know whether it's disappearance is temporary or am I supposed to use another solution?? Is there an unofficialy gutsy repo containing emerald somewhere??

Cheers for any advice

---

### Post by jaffamuffin on 2007-07-18
I may have to hold my hand up here, I think my emerald package may have came from a build I did my self using the most recent snapshot script on this page:

[http://gitweb.opencompositing.org/?p=users/3v1n0/compiz-fusion-debian;a=summary](http://gitweb.opencompositing.org/?p=users/3v1n0/compiz-fusion-debian;a=summary)

How can I tell WHERE a package came from (i.e. location it was installed from).

Woops

All I can say is the compiile went so well I forgot about it. I did remove all these packages at one point but apt may still have had them in it's cache.

---

### Post by hyperair on 2007-07-18
I reckon emerald will eventually pop up in the final release of Gutsy, but until then... god knows. You could try compiling from source right?

@jaffamuffin: ```
apt-cache policy PACKAGENAME
```
You could check your apt's cache at this location on your file system: "/var/cache/apt/archives"

---

### Post by jaffamuffin on 2007-07-18
```

root@jigglypuff:/home# apt-cache policy emerald
emerald:
  Installed: 0.3.0+git20070621~3v1ubuntu0
  Candidate: 0.3.0+git20070621~3v1ubuntu0
  Version table:
 *** 0.3.0+git20070621~3v1ubuntu0 0
        100 /var/lib/dpkg/status
root@jigglypuff:/home#     

```

```

root@jigglypuff:/home# ls /home/user/compiz-fusion-debian-builder-032d102cd665acb30d1f0692bbb46f3f4872340e/users/3v1n0/compiz-fusion-debian-builder/debs/ | grep emerald
emerald_0.3.0+git20070621~3v1ubuntu0_amd64.deb
emerald-themes_0.3.0+git20070323~3v1ubuntu0_all.deb
libemeraldengine0_0.3.0+git20070621~3v1ubuntu0_amd64.deb
libemeraldengine-dev_0.3.0+git20070621~3v1ubuntu0_amd64.deb

```

```
root@jigglypuff:/home# ls /var/cache/apt/archives | grep emerald
root@jigglypuff:/home#   
```


I don't think any packages from the official place will have 'git in their name.?'

---

### Post by hyperair on 2007-07-19
Actually they do. All of mine are from Trevino's reppository and their names are similar to yours. Anyway it sounds to me that you made your own debs using Trevino's script, so, by right it should be fine.

Also, for the moment, the "official place" for Compiz Fusion packages is Trevino's repository.

---

### Post by Mongo5000 on 2007-09-05
Still can't get the window borders going after trying everything in this and other threads.  Seems compiz fusion works, just no borders.  I got emerald installed but it wont even load gtk ones.

Tried everything but I think it might have to do with my xorg.conf file.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +1680+0; CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0; CRT: 1280x960 +0+0, DFP: nvidia-auto-select +1280+0; CRT: 1280x800 +0+0, DFP: nvidia-auto-select +1280+0; CRT: 1152x864 +0+0, DFP: nvidia-auto-select +1152+0; CRT: 1024x768 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 832x624 +0+0, DFP: nvidia-auto-select +832+0; CRT: 800x600 +0+0, DFP: nvidia-auto-select +800+0; CRT: 640x480 +0+0, DFP: nvidia-auto-select +640+0"
#    Option         "XAANoOffscreenPixmaps" "true"
    Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Anybody?

UPDATE.  I installed the latest updates and now my compiz manager won't even load.  Shows in my system list, but it won't run.

---

### Post by hyperair on 2007-09-05
What's the output of ```
compiz --replace -c emerald
```?

---

### Post by Mongo5000 on 2007-09-05
> **hyperair said:**
> What's the output of ```
compiz --replace -c emerald
```?

One quick update hyperair.

I completely removed all traces of compiz and reinstalled.  Guess what, IT WORKS!  I did however use gtk in the compiz options and it loaded but I entered what you suggested hyperair and emerald is now working great!

One thing im noticing though.  effects like desktop cude are really choppy and not smooth.  They were very smooth and quick with beryl, but now very slow.

Any suggestions?

EDIT: Its only choppy and laggy when the transparency is set.  If I leave it at 100, smooth as silk

---

### Post by victorgreen on 2007-09-12
THANK YOU THATS ALL I COULD GET TO WORK TOO!

> **Mr Greencastle said:**
> This may sound stupid, but I had the same problem as you, and I fixed it by doing these two separate in startup sessions.

Name: Compiz
Command: compiz --replace

Name: Emerald
Command: emerald --replace  (notice the no '&' thing? that might be something, I don't know)

That was THE ONLY thing that worked for me, hope that helps you!

Good luck,

Mr Green

Another stupid question: Have you checked that you have the 'Window Decorations' option enabled in CCSM?

---


---
title: "GDM font size"
date: 2005-03-30
forum: Desktop Environments
---

### Post by vaskark on 2005-03-30
My fonts are extraordinarily big in my GDM window. Is there any way to make them smaller? I couldn't find anything in the Login Screen Setup window. Thanks.

---

### Post by Buffalo Soldier on 2005-03-30
My problem is the opposite. It's too tiny. Seeing that I only boot once in a while, it's something that I ignore. But would be nice to know how to change the font size though.

---

### Post by maqi on 2005-03-30
Have a look in /usr/share/gdm/themes. Then go into the directory with the same name as your login theme and take a look at the <your-login-theme>.xml file in a text editor. 

You can change the font/font-size, etc in here. But make sure you keep a backup copy of the original .xml file - say <your-login-theme>-old.xml - just in case you make a serious error.

HTH
maqi :)

---

### Post by strawberry on 2005-04-01
and what about the size of the letters in the login box? How can we modify it?

---

### Post by vaskark on 2005-04-01
[QUOTE=maqi]Have a look in /usr/share/gdm/themes. Then go into the directory with the same name as your login theme and take a look at the <your-login-theme>.xml file in a text editor. 

You can change the font/font-size, etc in here. But make sure you keep a backup copy of the original .xml file - say <your-login-theme>-old.xml - just in case you make a serious error.

HTH
maqi :)[/QUOTE]
Yeah I tried that, but the changes didn't seem to take. I changed all fonts to "Trebuchet MS 8" but nada.

Yeah, I want them smaller in the login box, too!

---

### Post by vaskark on 2005-04-01
Ok, editing the theme file seems to be working now. I use 1280 resolution, and a font size = 7 is perfect. Now what about the Language, Session, etc. windows? Those fonts are still huge.

---

### Post by Buffalo Soldier on 2005-04-01
[QUOTE=Buffalo Soldier]My problem is the opposite. It's too tiny. Seeing that I only boot once in a while, it's something that I ignore. But would be nice to know how to change the font size though.[/QUOTE]Thanks Maqi,

The fix for my problem is to increase the font size from original of 9 to 14 (Bitsream Vera Sans). My screen resolution is 1600x1200.

[QUOTE=vaskark]Ok, editing the theme file seems to be working now. I use 1280 resolution, and a font size = 7 is perfect. Now what about the Language, Session, etc. windows? Those fonts are still huge.[/QUOTE] Vaskark, I think you have to change font size for all sections. Look under *<!-- language -->* and *<!-- session -->*.

---

### Post by maqi on 2005-04-02
[QUOTE=strawberry]and what about the size of the letters in the login box? How can we modify it?[/QUOTE]

[QUOTE=vaskark]Now what about the Language, Session, etc. windows? Those fonts are still huge.[/QUOTE]

It's a bit like RTFM: Just read the .xml file carefully - you will find which bit you need to edit. Otherwise - google for a tutorial in XML and/or gdm themes.

@Buffalo Soldier: Glad it worked for you  8) 

maqi

---

### Post by nicholaspaul on 2005-05-04
I looked at the human.xml file and all the fonts are 11poin t. On the login screen they are more like 300point. 
ANyone have an idea?

---

### Post by rorzik on 2007-08-26
> **nicholaspaul said:**
> I looked at the human.xml file and all the fonts are 11poin t. On the login screen they are more like 300point. 
ANyone have an idea?

Yeah, I just had to solve a similar problem (which is why I found this thread).  In your xorg.conf (usually /etc/X11/xorg.conf) under the Monitor section you can add a line like:

DisplaySize 339 212

This tells X the size of your display in millimeters, which is then used to calculate the sizes of the fonts that are displayed in gdm.  You can either measure and put the correct value, assuming it has detected it incorrectly, or you can lie to it and give it a different value to scale those font sizes.

---

### Post by Linfreak on 2007-10-01
I m having the same problem too.. (see screenshots) but i think the issue may be related to my nvidia driver.. NVIDIA-Linux-x86-1.0-7185-pkg1.. coz its happening after its installation.. what may be the problem..

this is my xorg.conf...

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
	Load		"bitmap"
	Load		"ddc"
	#	Load	"dri"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-75
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x960"	"1024x768"	"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"enable"
EndSection...

---

### Post by Linfreak on 2007-10-01
info.. I m using Ubuntu Feisty upgraded to Ubuntu Studio.. and that driver worls fine for my Debian and Mandriva...

---

### Post by dmazzone on 2007-11-08
I have the exact same problem, I was able to correct the size of the font in the login prompt through editing the Human.xml. The Options menu displays far too large still (i.e. taking up my entire screen), does anyone have any suggestions on how to display that properly?

---

### Post by dmazzone on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/99145](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/99145) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				And here my friends is the actual fix (at least for me):

"Fonts on High-Res Screens

On high-res screens (e.g. 15" 1680x1050), some users consider the default fonts too be too large. You can fix this by following these steps:

   1. Open System->Preferences->Appearance
   2. Select the "Fonts" tab
   3. Click the "Details" button (lower right)
   4. Adjust the Resolution down to 96dpi
   5. Make sure you have Subpixel (LCD) Smoothing enabled
   6. Save the preferences 

If you also want small fonts on the GDM login window, you can do this:

   1. Open System->Administration->Login Window
   2. Select the 'Security' tab
   3. Click the 'Configure X-Server' button
   4. Append '-dpi 96' (without quotes) to the text in the 'Command' field"

Brought to you thanks to:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61)

---

### Post by Yfrwlf on 2008-06-22
It would indeed be nice to have GDM/KDM do one of the following with all fonts (including the login/password box and user names): sync up a bit somehow with the desktop font sizes; have the font sizes used in any given them be adjustable from the login window manager GUI; or just change the font size to be by default a little bit more proportional (not to big, not to small, depending on detected resolution).  Or any combination of the above.  I vote 2 and 3.

Perhaps after/if integration becomes better between gdm/kdm and the rest of the desktop so that one flows into the other more nicely (fixing other issues as well, like having nice transitions) this issue will be a thing of the past.

---


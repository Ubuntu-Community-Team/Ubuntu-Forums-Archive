---
title: "White Screen of Death--plus other problems"
date: 2007-02-21
forum: Desktop Environments
---

### Post by Idfy on 2007-02-21
I have been at this for a while. And I have searched endlessly for answers. And I think I ran out of solutions.
I am on a fresh install of edgy.
First here is the xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"dbe"
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
	Option  	"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"LM-500"
	Option		"DPMS"
	HorizSync	29-61
	VertRefresh	55-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Monitor		"LM-500"
	DefaultDepth	16
	
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
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

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```
Now first I downloaded 0.1.9999 package and installed it. But that had problems (white-screen). So then I followed this post:
> 

for users running beryl/xgl on ubuntu edgy who are getting the white screen problem and who want to downgrade but have been wrestling with synaptic:

i have also had the white screen problem when installing beryl-0.2.0+svn20070219 from debs. the beryl-xgl --use-copy also worked for me, but as others have noted, it runs slower. i didn't find this performance hit acceptable, so i tried to downgrade as others have done (to 0.1.4). i've been having a tough time synaptic to force install previous versions because of the weird dependency complexities between beryl and emerald that i encountered.

i solved the problem by completely removing the beryl and emerald packages in synaptic, and then i went to the svn repository a la http and downloaded the debs for version 0.1.5 (edgy) manually:

[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/)

in here are all the 0.1.5 debs for beryl and emerald. note these are specific svn revisions, and they work together. there are other (some newer) svn revisions for 0.1.5 (at [http://download.tuxfamily.org/3v1deb...gy/beryl-svn/)](http://download.tuxfamily.org/3v1deb...gy/beryl-svn/)), but i found that you will _probably_ encounter weird python errors specific to beryl-settings.

when installing these debs, you need to do it in a specific order, because of dependencies, and even then, it will give your 'unconfigured' errors. this is ok, you can configure them afterwards. these are the 0.1.5 packaged i installed using dpkg -i

[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu5_i386.deb](http://download.tuxfamily.org/3v1deb...untu5_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...buntu0_all.deb](http://download.tuxfamily.org/3v1deb...buntu0_all.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu1_i386.deb](http://download.tuxfamily.org/3v1deb...untu1_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)
[http://download.tuxfamily.org/3v1deb...untu0_i386.deb](http://download.tuxfamily.org/3v1deb...untu0_i386.deb)

the order you install them with dpkg is important, as there will be configuration errors. i think i installed the libs first, and then the beryl-* packages, then emerald, then beryl. i ran dpkg --configure -a after every config error message. i also ran it after attempting to install all the debs, as well as dpkg -i *.deb (reinstall all the debs) for good measure.

it seems beryl-0.1.5 runs well and without any crazy white screens.

I followed all instructions and had it installed. When I entered 'beryl-manager' into the terminal. Everything goes white. And I have to ctrl-f4 to get out of it. Now when I do a 'beryl --use-copy' it shows the beryl animation and then goes to my highly disfigured gnome desktop. Colors are greenish and its all messed up. Animations work (slowly) and in about 30 secounds it crashed. To give a cross-reference I tried it on my 64-bit ati x300 machine with the same results.

Anyone have any suggestions?

---

### Post by nachotronics on 2007-02-23
Here's a solution I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or just [_**get the entire set at once from rapidshare -> beryl-svn.tar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html")

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Start beryl by running
```
beryl-manager
```

8. Enjoy\\:D/

---


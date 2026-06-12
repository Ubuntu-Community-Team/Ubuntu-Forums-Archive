---
title: "beryl probs"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by gamer91 on 2007-05-04
Im not sure if this is the right place, but here goes:

I have installed beryl and I like it, although how do i get the taskbar back? it seems to have disappeared. also how do I change the theme?

---

### Post by ayoli on 2007-05-04
for the task bar try to launch it:
ALT+F2 (will show the run dialog)
enter:
```
gnome-panel
```
hit enter
to change beryl them or edit beryl pref, use your beryl systray icon (with a right clic) or if you do not have it use the run dialog (ALT+F2) and enter:
```
emerald-theme-manager
``` 
for theme choosing or:
```
beryl-settings
```
for prefs settings

---

### Post by gamer91 on 2007-05-05
> **ayoli said:**
> for the task bar try to launch it:
ALT+F2 (will show the run dialog)
enter:

```
emerald-theme-manager
```for theme choosing 

I have opened this and clicked on the theme I want, but how do i tell it i want to use that one - it doesnt seem to want to do anything apart from highlight it.

---

### Post by ayoli on 2007-05-05
Is beryl running ?
do you have a beryl icon in your systray ? if not, hit ALT+F2 to open run dialog and launch:
```
beryl-manager
```
then right clic on the beryl icon in your systray and check that bery is selected as window manager. Re-open emerald-theme-settings (you can also do that from the right clic menu on the beryl icon in systray) and apply the theme you want.

---

### Post by gamer91 on 2007-05-05
the manager is running and it is in the systray, i just dont know how to actually apply the theme.

---

### Post by bagbiter on 2007-05-08
> **gamer91 said:**
> the manager is running and it is in the systray, i just dont know how to actually apply the theme.

I would like to know this as well.. in the emerald themer, there's a list of themes, but i can only highlight them.. not actually activate them.

---

### Post by LinuxNerd on 2007-05-08
Make sure that Emerald is set as your window decorator. You can check by right-clicking the beryl-manager icon and seeing if Emerald, not Metacity, is selected in the "Select Window Decorator" sub-menu.

---

### Post by jujudellago on 2007-05-09
I got exactly the same problem !

I found a dozen of forums where people ask the same question, then other answer "just refresh the decorator" .. "make sure emerald is the window decorator" .....  (so yes, I did that too)

then people stop posting :(



PS: I have another  problem... all my programs run well.... except the most basic one, the terminal, I can get the "Konsole" working, but no way to change the colors, it's sticked to black on white background (my eyes very much prefer white text on dark background.."

---

### Post by ayoli on 2007-05-09
type this in a terminal and post the output here:
```
ps aux |grep emerald && ps aux |grep beryl
```

---

### Post by misfitpierce on 2007-05-09
Themes are applied by having emerald themer open highlight the theme you want and right click beryl theme with window still open then click reload window-decorator!

---

### Post by bagbiter on 2007-05-09
> **misfitpierce said:**
> Themes are applied by having emerald themer open highlight the theme you want and right click beryl theme with window still open then click reload window-decorator!
tried that and nothing happened

heres the output

```

oystean   7967  2.4  1.1  40280 24368 ?        S    11:42   0:04 emerald-theme-manager
oystean   8015  0.8  0.6  24464 13032 ?        S    11:45   0:00 emerald --replace
oystean   8043  0.0  0.0   1724   564 pts/1    S+   11:45   0:00 grep emerald
oystean   7858  0.3  0.6  50524 14120 ?        Ssl  11:42   0:00 beryl-manager
oystean   7983  1.6  1.3  78832 27168 ?        SL   11:44   0:01 beryl --skip-gl-yield
oystean   8009  6.2  1.4  44644 29912 ?        S    11:45   0:02 python /usr/bin/beryl-settings
oystean   8045  0.0  0.0   1720   560 pts/1    S+   11:45   0:00 grep beryl

```

---

### Post by ayoli on 2007-05-09
stange, it should work.
when i select a theme in emerald-theme-manager, it applies straight away. Some people tell they need to reload window decorator by right cliking on beryl-manager icon in systray and picking "reload window decorator".
you also may want to search in [beryl forums]("http://forum.beryl-project.org/")

---

### Post by jujudellago on 2007-05-09
> **misfitpierce said:**
> Themes are applied by having emerald themer open highlight the theme you want and right click beryl theme with window still open then click reload window-decorator!

I did that exactly but still the same.

> **ayoli said:**
> type this in a terminal and post the output here:
```
ps aux |grep emerald && ps aux |grep beryl
```

ok, here it is:
```

juju@mekhong:~$  ps aux |grep emerald && ps aux |grep beryl
juju      7243  6.0  1.1 100596 24864 ?        S    18:35   0:03 emerald-theme-manager
juju      7307  0.9  0.3  14728  7672 ?        S    18:36   0:00 emerald --replace
juju      7313  0.0  0.0   2900   780 pts/3    R+   18:36   0:00 grep emerald
juju      6444  0.3  0.4  73536  9396 ?        Ssl  18:26   0:01 beryl-manager
juju      7261  2.3  3.9 180668 81476 ?        SL   18:35   0:01 beryl --force-nvidia --skip-gl-yield
juju      7315  0.0  0.0   2900   788 pts/3    S+   18:36   0:00 grep beryl
juju@mekhong:~$ 




```

thank you for your help :KS

---

### Post by ayoli on 2007-05-09
okay, try launch the emerald-theme-manager from command line, just type in a term:
```
emerald-theme-manager
```
then try change theme and see if there any debug outpout in your term, then post it here.
Another thing you can try:
turn off beryl, then save all conf in a tmp folder in a term type in:
```
mkdir ~/beryl-emerald.save && mv ~/.beryl* ~/beryl-emerald.save && mv .emerald* ~/beryl-emerald.save
```
then restart beryl by launching beryl-manager, if then you can change theme, it was a conf file problem.

---

### Post by jujudellago on 2007-05-09
nothing comes out of the shell when I star the emerald manager from the shell, however by starting beryl itself from the shell, I had a whole bunch of

```

beryl: Couldn't bind redirected window 0x2c000fe to texture
beryl: No GLXFBConfig for depth 32

```

some more comes out as I move the windows or turn the cube desktop around.

so I googled a bit around with that error message, and found a few forums with people descibing the same problem.

I found those clues:

- check if the defaul depth n the scrren section of the xorg.conf file must be 24
-> checked, didn work

-add this line in the screen section "Option "DisableGLXRootClipping" "True" 
-> didn't work either

-add this line in the screen section
Option "AddARGBGLXVisuals" "True"

-> nothing changed either.....



in case I messed around too much with the xorg.conf (indeed I made a backup before the previous modifications) here is my xorg.conf file, maybe something obvious in there ?

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"fr"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [GeForce Go 7400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [GeForce Go 7400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Option "DisableGLXRootClipping" "True"
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


PS: now I just noticed my mouse scroll does'nt work anymore in emacs (it was made by a trick in the .emacs file)

PSPS: weird thing also, when I open a shell before starting beryl everything works well, but if I open a new one, I just see an empty white box appear, while those opened before starting beryl 

PSPSPS: how should I restart properly beryl ? when I close the Beryl icon nothing stops, and when I kill the process, I can't switch windows, or change desktops, so I close my session and re-open....

thanks a lot for any suggestions...

---

### Post by z0phi3l on 2007-05-09
When Beryl starts acting up the easiest I've found ( and bookmarked) is to reinstall Beryl and rebooting.


It only happens once or twice a week so it's not that big a deal to me.


*edit* I use this method to install Beryl, it works every time I've needed to reinstall it.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method)

---

### Post by jujudellago on 2007-05-10
YOUPIE !!!

hihi it still didn't work  last night, I just closed the cover of my laptop.... this morning beryl hanged totally, couldn't event hit "CTRL-ALT-F1" to reboot manually, I had to connect remotely with SSH from my desktop computer.

so the laptop restarted, I started Beryl, and .... Magical, everything works just perfectly, no more problems with my white shells, and now when I click on a theme on the emerald manager it just comes up when I clock on the theme in the list, nothing to refresh :)

lalalalaalaaaaaaaaaa  :KS :KS :KS   I'm happy now

thanks everybody, bless you all !

(now I'm wondering how to have the fancy 3-d background behind the cube, but I'll look around the forums to figure it out :) )

---


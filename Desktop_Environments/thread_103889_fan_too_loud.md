---
title: "fan too loud"
date: 2005-12-14
forum: Desktop Environments
---

### Post by masingerz on 2005-12-14
Dear Forum:

I have an Intel D915PGN with a 3.2Ghz, 800 bus, 1 meg L2, 1 Giga Kingston RAM, 3 HDD, and 2 fans, in a Foxconn case (I put PC toghether myself), so the fans were really loud, mainly the processor fan, I noiced that when I flashed the Bios the noise went away, Originally I flashed the Bios to try to fix this spontaneus reboot problem the Pc is having, the problem sorta keeps occuring in both winXP and Ubuntu also. But I'm focusing on the loud fan, when I reboot the system the fan slows down and becomes quiet. Isther a way to approach the loud fan? (and the spontaneus reboot)

regards Masingerz

---

### Post by 23meg on 2005-12-14
What's your processor? Is powernowd running? What running speed does /proc/cpuinfo or the Gnome panel frequency scaling applet show?

---

### Post by MButterman on 2005-12-15
Since this is occuring in XP and Ubuntu, I believe this isn't the O/S you are using.  By the information provided, I assume this is a P4 but I'm not sure if it is a Northwood or Prescott core. Earlier Prescott core P4's ran much hotter and required considerably more power to run them. With the configuration you have described, I would take a close look at the power supply. As more components are added to a system, more power is required to run them.  With the cheaper power supplies, they might claim a certain wattage but as the temperature rises the power supply becomes less efficient. While the specs might say 550 watts, this is based in keeping the power supply very cool (about 70 degrees) but when it reaches a more realistic temp inside a case (about 100 degrees,) the power supply's actual wattage drops far below the printed specs. Also at greater loads it makes it more difficult for the power supply to provide "clean" power to whatever is connected to it.

I assume you are using the stock cooler for this processor and they are inherently loud (especially for the Prescott core processors) I recommend the following:

1. computer components are very power fussy and require a well regulated voltage and as components are added, it also has to provide the same under higher temperatures and larger wattage loads. If you are running a "cheap" power supply with all these components, chances are the power supply isn't doing it's job very well. This is a common cause of system stability problems so consider a high quality replacement. (I recommend and use an Antec Neopower 480)

2. You can replace the stock CPU cooler that runs quieter and does a better job. You can also replaced your case fans with quieter ones. I presently use ones called Stealth, I think the company that makes them is named Vantec. The Neopower 480 is also low noise.

3. If this all doesn't appeal to your budget, you can buy a case with a good power suppy. I avoid plastic cases because of their design and materials used, they tend to retain heat inside the case. I prefer aluminum because it tends to have a "radiator" type affect and the case stays cooler as well as the parts inside.

Hopes this helps and good luck

MButterman

---

### Post by mcduck on 2005-12-15
You could change the CPU's cooler. I'd recommend Zallman's models, they are not too expencive, and certainly not loud. Basicly, the bigger the fan is, the less speed (and noise) it needs to keep things cool.

Other thing that is worth looking at is case cooling. Do you have any case fans? The best way is to have extra fan(s) up on the back of the case to blow heated air out. Fresh air will flow in by itself. 

You could also install lm-sensors so you can check your temperatures, if they are not too high but fans still keep noise you can buy some fan speed controller to slow them down.

---

### Post by moe_syzlak on 2007-11-27
the reason ur fan is too loud is because u have ur xorg.conf misconfigured. change "AIGLX" to "on". The gpu over works, gets hot, and the fan kicks in to stop ur box from melting down. u should hear a difference after like 10mins of changing, and restarting ur xserver.

do ur xorg.conf like mines:


# Xorg configuration created by livna-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "Xinerama" "0"
EndSection

Section	"Module"
#	Load "GLcore"
#	Load	"vbe"
	Load "dbe"
Endsection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "LPL"
	HorizSync    30.0 - 75.0
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce Go 7300"
	Option	    "Accel" "true"
	Option	    "AddARGBGLXVisuals" "True"
	Option	"NoLogo"	"True"
	Option	"DRI"	"true"
	Option	"XAANoOffscreenPixmaps"	"true"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "RenderAccel" "true"
	Option	    "TwinView" "0"
	Option	    "metamodes" "1440x900 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

---

### Post by rfruth on 2007-11-27
IF the CPU is running cool (OCing ?) & fan is a 4 pin let BIOS control fan speed (maybe fan is running faster than need be sometimes)

---


---
title: "Gutsy + ATI X1300, but no Compiz!!"
date: 2008-01-19
forum: Desktop Environments
---

### Post by unshareef on 2008-01-19
Dear Ubuntu Scholars,

I hope you can help. I believe it is an easy problem but I am new.

I have a Dell Inpiron 6400 laptop with Intel Core Duo 1.73GHz, 1GB RAM, and X1300 ATI Graphics card.

I had problems installing the ATI driver but I believe I have succeeded (I presume) now that my resolution is correct and ATI Catalyst Control Centre has appeared.

THE PROBLEM: I can't enable desktop effects in the Appearance window. When I switch it onto medium or full it says "Composite Extension not available".

Here is my compiz file:

> ```
#!/bin/sh
# Compiz Manager wrapper script
# 
# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#
# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages
#
# Much of this code is based on Beryl code, also licensed under the GPL.
# This script will detect what options we need to pass to compiz to get it
# started, and start a default plugin and possibly window decorator.
# 


COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia fglrx intel ati radeon i810"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
#BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
	if [ "x$VERBOSE" = "xyes" ]; then
		printf "$*"
	fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 0;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

# Check for non power of two texture support
check_npot_texture()
{
	verbose "Checking for non power of two support: "
	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for presence of FBConfig
check_fbconfig()
{
	verbose "Checking for FBConfig: "
	if [ "$INDIRECT" = "yes" ]; then
		$GLXINFO -i | grep -q GLX.*fbconfig 
		FB=$?
	else
		$GLXINFO | grep -q GLX.*fbconfig 
		FB=$?
	fi

	if [ $FB = "0" ]; then
		unset FB
		verbose "present. \n"
		return 0;
	else
		unset FB
		verbose "not present. \n"
		return 1;
	fi
}


# Check for TFP
check_tfp()
{
	verbose "Checking for texture_from_pixmap: "
	if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		if [ "$INDIRECT" = "yes" ]; then
			unset LIBGL_ALWAYS_INDIRECT
			INDIRECT="no"
			return 1;
		else
			verbose "Trying again with indirect rendering:\n";
			INDIRECT="yes"
			export LIBGL_ALWAYS_INDIRECT=1
			check_tfp;
			return $?
		fi
	fi
}

# Check wether the composite extension is present
check_composite()
{
	verbose "Checking for Composite extension: "
	if xdpyinfo -queryExtensions | grep -q Composite ; then
		verbose "present. \n";
		return 0;
	else
		verbose "not present. \n";
		return 1;
	fi
}

# Detects if Xgl is running
check_xgl()
{
	verbose "Checking for Xgl: "
	if xvinfo | grep -q Xgl ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		return 1;
	fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
	if [ $MEM -lt $NVIDIA_MEMORY ]; then
		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
		return 1;
	fi
	return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
		return $NVIDIA_INTERNAL_TEST;
	fi
	verbose "Checking for nVidia: "
	if xdpyinfo | grep -q NV-GLX ; then
		verbose "present. \n"
		NVIDIA_INTERNAL_TEST=0
		return 0;
	else
		verbose "not present. \n"
		NVIDIA_INTERNAL_TEST=1
		return 1;
	fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	fi
	verbose "Passed.\n"
	return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
	LOG=$(xset q|grep "Log file"|awk '{print $3}')
	if [ -z "$LOG" ];then
		verbose "AIEEEEH, no Log file found \n"
		verbose "$(xset q) \n"
	return 0
	fi
	for DRV in ${WHITELIST}; do
		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
		then
			return 0
		fi
	done
	verbose "No whitelisted driver found\n"
	return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
	OUTPUT=$(lspci -n)
	for ID in ${BLACKLIST_PCIIDS}; do
		if echo "$OUTPUT" | egrep -q "$ID"; then
			verbose "Blacklisted PCIID '$ID' found \n"
			return 0
		fi
	done
	OUTPUT=$(lspci -vn | grep -i VGA)
	verbose "Detected PCI ID for VGA: $OUTPUT\n"
	return 1
}

build_env()
{
	if check_nvidia; then
		ENV="__GL_YIELD=NOTHING "
	fi
	if [ "$INDIRECT" = "yes" ]; then
		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
	fi
	if check_xgl; then
		if [ -f ${LIBGL_NVIDIA} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
			verbose "Enabling Xgl with nVidia drivers...\n"
		fi
		if [ -f ${LIBGL_FGLRX} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
			verbose "Enabling Xgl with fglrx ATi drivers...\n"
		fi
	fi

	ENV="$ENV FROM_WRAPPER=yes"

	if [ -n "$ENV" ]; then
		export $ENV
	fi
}

build_args()
{
	if [ $INDIRECT = "yes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if check_nvidia; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
	fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
	test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
	abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
	INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
	# if vesa or vga are in use, do not even try glxinfo (LP#119341)
	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
		abort_with_fallback_wm
	fi
	# check if we have the required bits to run compiz and if not, 
	# fallback
	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
		abort_with_fallback_wm
	fi

	if check_nvidia && ! check_nvidia_memory; then
		abort_with_fallback_wm
	fi

	if ! check_fbconfig; then
		abort_with_fallback_wm
	fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

# start the gtk-window-decorator if present
if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
	verbose "Starting emerald\n"
	${COMPIZ_BIN_PATH}emerald --replace &
elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	verbose "Starting gtk-window-decorator\n"
	${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
	verbose "Starting kde-window-decorator\n"
	${COMPIZ_BIN_PATH}kde-window-decorator --replace &
	FALLBACKWM="${KWIN}"
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

```

And here is my Xorg file:

> ```

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

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

#Section "Extensions"
#	Option		"Composite"	"Disable"
#	Option		"Composite"	"0"
#EndSection

```

I very much hope somebody out there can help me. Very much appreciated.

Thanks

---

### Post by Rock42 on 2008-01-19
I also have the same problem, was going 2 start my own thread but now i can piggyback on yours =D

---

### Post by Kaphix on 2008-01-19
I have the same card, this is the only thing that has ever worked for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Method 2 is the only one that worked.

---

### Post by Yellow Pasque on 2008-01-19
unshareef, in your xorg.conf change:
```
#Section "Extensions"
#	Option		"Composite"	"Disable"
#	Option		"Composite"	"0"
#EndSection
```
to
```

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```
Restart and see if you can enable them then. You can also get the advanced compiz settings manager with:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by unshareef on 2008-01-19
> **Temüjin said:**
> unshareef, in your xorg.conf change:
```
#Section "Extensions"
#	Option		"Composite"	"Disable"
#	Option		"Composite"	"0"
#EndSection
```
to
```

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```
Restart and see if you can enable them then. You can also get the advanced compiz settings manager with:
```
sudo apt-get install compizconfig-settings-manager
```
Thanks for the reply Temujin.

I changed it as you instructed but it an error still appears saying "desktop effects could not be enabled". It almost works, in that a waiting sign appears for a few seconds before this error appears.

I already downloaded and installed the advanced settings manager in excitement and anticipation :-)

---

### Post by Yellow Pasque on 2008-01-19
Oh, also turn AIGLX on:
```
Section "ServerFlags"
	Option		"AIGLX"	**"on"**
EndSection
```

---

### Post by unshareef on 2008-01-19
Thanks, did that too now ...

but the error persists!

---

### Post by Yellow Pasque on 2008-01-19
Ok, let's look at your /var/log/Xorg.0.log file. Please post that.

---

### Post by unshareef on 2008-01-19
Sure, here it is:

> ```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux umar-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 19 23:24:26 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "on"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01bd rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01bd rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01bd rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01bd rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01bd rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01bd rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01bd rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7149 card 1028,2003 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,01af rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,01bd rev 00 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,01bd rev 19 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,01bd rev 01 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,01bd rev 0a class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,01bd rev 05 class 08,80,00 hdr 80
(II) PCI: 0b:00:0: chip 8086,4222 card 8086,1021 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 11 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:3), (0,12,13), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfbfffff (0x200000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdf9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc M52 [ATI Mobility Radeon X1300] rev 0, Mem @ 0xc0000000/28, 0xdfdf0000/16, I/O @ 0xee00/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[5] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[6] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[7] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[8] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[12] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[13] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[14] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[15] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[18] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[19] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[20] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[5] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[6] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[7] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[8] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[12] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[13] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[14] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[15] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[18] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[19] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[20] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[9] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[10] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[18] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[24] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[25] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[26] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.44.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.443.1                  
(II) ATI Proprietary Linux Driver Build Date: Dec 19 2007 21:29:14
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x7149) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[9] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[10] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[18] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[24] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[25] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[26] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82094f0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[9] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[10] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[27] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[28] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1300" (Chipset = 0x7149)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2003)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M52P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AUO  Model: 1474  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  CD514
(II) fglrx(0):  0AMWx€Ìø
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0006af741400000000
(II) fglrx(0): 	010f0103802115780aa7e599594f8c27
(II) fglrx(0): 	1d505400000001010101010101010101
(II) fglrx(0): 	010101010101c71b00a0502017301520
(II) fglrx(0): 	44004bcf10000018261700a050201730
(II) fglrx(0): 	152044004bcf10000000000000fe0043
(II) fglrx(0): 	443531340042313534455731000000fe
(II) fglrx(0): 	0030414d5778a4ccf801010a202000fa
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 398/342MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   3. 209/252MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1301 1333 1440  800 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1301 1333 1440  720 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1301 1333 1440  768 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1301 1333 1440  600 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1301 1333 1440  480 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1301 1333 1440  480 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1301 1333 1440  432 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1301 1333 1440  400 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1301 1333 1440  384 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1301 1333 1440  300 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1301 1333 1440  240 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1301 1333 1440  200 804 808 823 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1301 1333 1440  800 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   71.11  1280 1301 1333 1440  720 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1301 1333 1440  768 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1301 1333 1440  600 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1301 1333 1440  480 804 808 823 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1301 1333 1440  480 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   71.11  640 1301 1333 1440  432 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1301 1333 1440  400 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 1301 1333 1440  384 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   71.11  400 1301 1333 1440  300 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   71.11  320 1301 1333 1440  240 804 808 823 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   71.11  320 1301 1333 1440  200 804 808 823 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[7] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[8] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[9] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[10] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[11] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[12] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[13] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[14] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[15] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[30] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[31] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[32] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[33] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x20000
(II) fglrx(0): [drm] mapped SAREA 0x20000 to 0xb7bd8000
(II) fglrx(0): [drm] framebuffer handle = 0x21000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.44.3
(II) fglrx(0):     Date: Dec 19 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00022000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01000400
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3277)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2477
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		19 256x256 slots
		5 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetClientVersion: 0 9
```

Cheers

---

### Post by Yellow Pasque on 2008-01-19
All the extensions are loading properly and your driver installation looks excellent. WHat output do you get when you type in the terminal:
```
compiz
```

---

### Post by unshareef on 2008-01-19
Here's what came up when I typed "compiz" in terminal

> [CODEumar@umar-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7149 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
][/CODE]

---

### Post by unshareef on 2008-01-19
whoops, didnt quite post that properly, here:

> umar@umar-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7149 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found


---

### Post by sloggerkhan on 2008-01-19
My guess is that you need to unblacklist your card from the compiz settings.
PS: I am jealous of your max texture size.
Mine's smaller than the size of 2 monitors, which makes for all kinds of 'either or' problems.

---

### Post by Yellow Pasque on 2008-01-19
In /usr/bin/compipz file:
> COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 
------->
```
COMPIZ_BIN_PATH="**/usr/bin/**" # For window decorators and compiz
PLUGIN_PATH="**/usr/lib/compiz/**"
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="**compiz.real**" # Final name for compiz (compiz.real)
```

Then, type compiz in terminal and check the output.

EDIT: For Intel video, you'll need to scroll down a bit and delete or comment out (put a '#' in front of) these two lines:
> T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)

---

### Post by unshareef on 2008-01-19
My effects have started working!! Many thanks temujin,

Here is the output after typing compiz:

> umar@umar-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7149 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


There seems to be a warning at the end as you can see (8 bit something), is that ok?

---

### Post by Yellow Pasque on 2008-01-19
Congratulations.
> There seems to be a warning at the end as you can see (8 bit something), is that ok?

Yes, it's okay. I found this explanation from an Ubuntu developer.
[http://ubuntuforums.org/showpost.php?p=3805293&postcount=17](http://ubuntuforums.org/showpost.php?p=3805293&postcount=17)

---

### Post by unshareef on 2008-01-19
also, my screensavers are flickering now as opposed to before :-/

but they do have a much smoother framerate :-)

---

### Post by unshareef on 2008-01-19
whenever I goto choose a screensaver,  the preview of the screensaver starts flickering. If I then click full screen preview, or if I drag and move about the window a bit, all the windows on the screen become garbled and messed up. I then have to press CTRL ALT Backspace to use ubuntu. Could the code require tweaking? Perhaps we took some unnecessary steps earlier on...

---

### Post by Yellow Pasque on 2008-01-19
We didn't take any unnecessary steps as Compiz definitely needs AIGLX and the Composite extensions. I've been searching for info on flickering and it appears some people are having the same problem, but I have not seen a solution yet :\

I will keep looking..

---

### Post by unshareef on 2008-01-19
> **Temüjin said:**
> We didn't take any unnecessary steps as Compiz definitely needs AIGLX and the Composite extensions. I've been searching for info on flickering and it appears some people are having the same problem, but I have not seen a solution yet :\

I will keep looking..

Sure thing. Thanks a bunch anyway, and I'll give you a break for now.

If you do find a solution be sure to post the link to it here, thanks. Good night.

---

### Post by terminal on 2008-01-27
Thats the problem with ati drivers right now . I have hd2600 card and it flickers with every driver while watching movies . In fullscreen mode it doesnt flickers . you can change ur media player (vlc ) to use Xvideo as output module then it should work fine but cpu usage will be bit higher .

---

### Post by LonelyTraveler on 2008-01-27
Hey Unshareef,

Still having problems activating visual effects?

```
umar@umar-laptop:~$ compiz
Checking for Xgl: not present.
```

If so, that is your problem. Well... It was mine. Install xserver-xgl and reboot. Then try activating.

---

### Post by billmik on 2008-01-27
Hi
I have a ati x1300 and after installing the ati restricted driver i had the same problem and error with visual effects. The way i got it to work is: Clicked on system, admin, synaptic package manager then did a search for xserver-xgl. When it found it i checked it for install. when its done, reboot then Visual effectrs will work. at least it did for me:)

---


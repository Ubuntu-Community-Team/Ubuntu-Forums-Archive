---
title: "compiz=no windows borders"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by museworry on 2008-04-10
Hi. I've meet the problem with compiz running and showing no borders. I've tried to google on it, but did not find any suitable solution. So, I have ati X1400 with latest ati driver, installed by ENVY

compiz --replace did not run for me:

```
alex ~ $  compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
present.
Checking for non power of two support: Segmentation fault (core dumped)
present.
Checking for Composite extension: present.
Segmentation fault (core dumped)
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
```

so I am using this:
compiz.real --replace

after runing compiz, if i try to restore windows border by metacity --replace  -- it stops compiz,  
kde-window-decorator --replace do not give any effect

and also alt+mouse do not drag windows

here is my Xorg.conf:

```
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"
        Fontpath        "/usr/share/fonts/truetype/ttf"
EndSection

Section "Module"
        Load            "freetype"
        Load            "dbe"
        #       Load  "type1"
        Load            "bitmap"
        Load            "drm"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "record"
        Load            "glx"
        ##
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,ru"
        Option          "XkbVariant"    ",winkeys"
        Option          "XkbOptions"    "grp:ctrl_shift_toggle,grp_led:scroll"

EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection
```

this is my compiz (I've made some changes to original)

```

alex ~ $  cat /usr/bin/compiz
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
WHITELIST="nvidia intel ati radeon i810"

# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
BLACKLIST_PCIIDS="$T"
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

---

### Post by Saint Angeles on 2008-04-10
don't know if this will help, but take a look at my xorg.conf.

i have an x1550.

---

### Post by tamoneya on 2008-04-10
there is currently an ongoing post on this topic.  You will get the best support if you just join this thread.

[http://ubuntuforums.org/showthread.php?t=750390&highlight=borders](http://ubuntuforums.org/showthread.php?t=750390&highlight=borders)

---

### Post by museworry on 2008-04-10
some extra


```
alex ~ $  glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

---

### Post by falkTX on 2008-04-10
I had the same problem when I was using Gutsy with the NVIDIA drivers.
I noticed that NVIDIA reported 32bit desktop when was using 16bit.
So I always changed 2 lines in /etc/X11/xorg.conf from 16bit to 24bit. It ALWAYS WORKED.

Now with Hardy, I don't need to do it anymore, it fixes the problem alone.

I hope it was helpful

---

### Post by museworry on 2008-04-10
Thanks, but I already do have 24 bits in my xorg.conf

---

### Post by museworry on 2008-04-10
> **tamoneya said:**
> there is currently an ongoing post on this topic.  You will get the best support if you just join this thread.

[http://ubuntuforums.org/showthread.php?t=750390&highlight=borders](http://ubuntuforums.org/showthread.php?t=750390&highlight=borders)

This person seems to have some problem with latest driver, but I have a bit different problem. I've managed to run compiz, but than I screw it up somehow during changing settings, and now I am not able to run it. Even with reinstalling compiz and deleting .config/compiz

And also I wondering, why all run compiz via compiz --replace, wich is not working for (goes to infinit loop), thouth the compiz.real --replace work.

---

### Post by museworry on 2008-04-11
NVM, I've manage to fix it.

---

### Post by markcgriffiths on 2008-04-11
What did you do?  I have a similar problem.

---

### Post by museworry on 2008-04-11
I've used this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

in extra compiz script wants some from the file
```
/etc/xdg/compiz/compiz-manager.ubuntu
```
(recheck it in your  /usr/bin/compiz)
and in my system this file had a different name (smth. like /etc/xdg/compiz/compiz-manager.ubuntu.new-pkg_bla_bla) so I just rename it  and now
compiz --replace work for me (though compiz.real --replace does not)

---


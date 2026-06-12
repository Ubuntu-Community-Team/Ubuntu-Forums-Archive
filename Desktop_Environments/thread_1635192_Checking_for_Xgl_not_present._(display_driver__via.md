---
title: "Checking for Xgl: not present. (display driver : via chrom )"
date: 2010-12-01
forum: Desktop Environments
---

### Post by hamza0081 on 2010-12-01
hi evry one iam new user for lunix os , and i  tired to get work compiz , in terminal whene i type : compiz 
i get the folowing errors :

compiz
 ```

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin
kwin(12206) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1.
kwin(12206) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_ozone.so"  for  "kwin3_ozone"

```and lspci i get this 
```

lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:08.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


```for this command   lshw -C display i get this 
```

root@bt:~# lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: CN896/VN896/P4M900 [Chrome 9 HC]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2
root@bt:~#   

```and this is my compiz file 
```


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

if [ -x $METACITY ]; then
    FALLBACKWM="${METACITY}"
elif [ -x $KWIN ]; then
    FALLBACKWM="${KWIN}"
else
    FALLBACKWM=true
fi
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"
#WHITELIST="Inc. CN896/VN896/P4M900"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562" # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS="core"
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Default X.org log if xset q doesn't reveal it
XORG_DEFAULT_LOG="/var/log/Xorg.0.log"

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
    
    if [ "x$CM_DRY" = "xyes" ]; then
        verbose "Dry run failed: Problems detected with 3D support.'n"
        exit 1;
    fi

    verbose "aborting and using fallback: $FALLBACKWM \n"

    if [ -x $FALLBACKWM ]; then
        exec $FALLBACKWM $FALLBACKWM_OPTIONS
    else
        printf "no $FALLBACKWM found, exiting\n"
        exit 1
    fi
}

# Check if we run with the Software Rasterizer, this happens e.g.
# when a second screen session is opened via f-u-a on intel
check_software_rasterizer()
{
    verbose "Checking for Software Rasterizer: "
    if glxinfo 2> /dev/null | egrep -q '^OpenGL renderer string: Software Rasterizer' ; then
        verbose "present. \n";
        return 0;
    else
        verbose "Not present. \n"
        return 1;
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
    if [ ! -x "$NVIDIA_SETTINGS" ]; then
    return 0
    fi

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
    if [ "$LOG" = "" ]; then
        verbose "xset q doesn't reveal the location of the log file. Using fallback $XORG_DEFAULT_LOG \n"
        LOG=$XORG_DEFAULT_LOG;
    fi
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
    if [ "x$INDIRECT" = "xyes" ]; then
        COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
    fi
    if check_nvidia; then
        if [ "x$INDIRECT" != "xyes" ]; then
            COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
        fi
    fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
    test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
    OLD_IFS=$IFS
    IFS=:
    for CONFIG_DIR in $XDG_CONFIG_DIRS
    do
        test -f $CONFIG_DIR/compiz/compiz-manager && . $CONFIG_DIR/compiz/compiz-manager
    done
    IFS=$OLD_IFS
    unset OLD_IFS
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

    # check if we run with software rasterizer and if so, bail out
    if check_software_rasterizer; then
        verbose "Software rasterizer detected, aborting"
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

if [ "x$CM_DRY" = "xyes" ]; then
    verbose "Dry run finished: everything should work with regards to Compiz and 3D.\n"
    exit 0;
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS


```
Please help me :-(

---

### Post by oneillam on 2011-02-24
Maybe you're having issues with Linux because you either suck at English or you just can't type...

"hi evry one iam new user for lunix os , and i tired to get work compiz , in terminal whene i type..."

---


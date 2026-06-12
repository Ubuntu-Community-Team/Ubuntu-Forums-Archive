---
title: "/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by polppol on 2007-10-23
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing

helpp i can't use desktop effect T-T

Ubuntu 7.10
ATi mobi x1700

polppol@polppol-nbl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6747 (8.40.4)


polppol@polppol-nbl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6747 (8.40.4)

I already install xserver-xgl

---

### Post by michael37 on 2007-10-23
> **polppol said:**
> /usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing

helpp i can't use desktop effect T-T

Ubuntu 7.10
ATi mobi x1700

polppol@polppol-nbl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6747 (8.40.4)


polppol@polppol-nbl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6747 (8.40.4)

I already install xserver-xgl

1. run command fglrinfo -display :1
2. please follow howto in this [thread=569654]ATI-specific thread[/thread]

---

### Post by polppol on 2007-10-23
thx I got it

---

### Post by family on 2008-01-12
At one point, I had compiz fusion running perfectly and it was fast. After a clean Gutsy install, NOTHING works. I tried reconfigureing X and whatnot but still no luck.
I didnt have to do anything special to get it to work last time...
I installed xserver-xgl, but my computer had a movement:action ratio of 10:1, ie it was in uberlaggg mode. Help?
```

q@Q-Desktop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```
```

q@Q-Desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by family on 2008-01-12
I fixed it. I had to do some heavy editing of the /usr/bin/compiz script though.
Essentially, I pointed compiz.real to load my i810 driver instead of guessing one. This meant to change the driver filepath string, and also to change the load string to remove un-needed extensions to the filepath.
DO NOT REPLACE YOUR COMPIZ WRAPPER WITH THIS UNLESS YOU HAVE A i810 ON A SAMSUNG SYNCMASTER 914, ON A P4 OR BETTER COMPUTER. Just saying.
```

#!/bin/sh
# Compiz Manager wrapper script
COMPIZ_BIN_PATH="/usr/local/bin/"
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz"
# For detecting what driver is in use, the + is for one or more /'s
#XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/i810_drv.so"
FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"
# Driver whitelist
WHITELIST="intel i810 vga vesa"
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
# Use emerald by default if it exist plz change back to yes
USE_EMERALD="yes"
# No indirect by default, plz change back to no
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
		if egrep -q "Loading ${XORG_DRIVER_PATH}" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}" $LOG; 
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

### Post by family on 2008-01-12
Compiz is running as fast as metacity again, and so is emerald (with gtk-window decorator :)). All without xserver-xgl.
I would adwise to i810 ppl out there to 
```

sudo apt-get install i810switch && i810switch lcd on

```
ONLY IF YOU HAVE AN LCD SCREEN. (btw those are the ones that are flat and thin, ie not the bulky monitors from the 90's.)

---


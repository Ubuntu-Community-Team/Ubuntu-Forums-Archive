---
title: "Quake2 install, from the beginning?"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by 4linux on 2005-10-19
OK, I've got breezy all set up and everything is working good.  

Now I would like to play Quake2.  I have a retail Quake2 cd for windows. (plus all the expansion CDs).  I need instructions....keeping in mind I am still sort of a noob at Linux, (but learning fast).  With your help, I'll soon be fragging Strogg :twisted: 

-Pat

---

### Post by hammett111 on 2005-10-21
Before I tell you are you running 64-bit or 32-bit?

---

### Post by arcanistherogue on 2005-10-22
What I suggest:

1. Install on windows. (everything, including expansions)
2. Get Quake II installer from [http://liflg.org](http://liflg.org)
3. Install demo of Quake II.
4. Mount your windows drive and copy the Quake II files into the /usr/local/games/quake2 folder, replacing all the paks and whatnot. 

Thats what I did and it works fine.  You can also delete all the .exe files and whatnot.  What I love about the Quake II  linux installer is that it has the OpenGL .dll file, not even the Quake 4 Bonus DVD version of Quake II had that :D

---

### Post by 4linux on 2005-10-22
OK, thanks to you both.  I got Quake2 installed by following: [http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html](http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html)

It works fine except for one thing.  When I run Quake2 from outside of X, i have no mouse.  It says mouse not found.  Here is what my libvga.config looks like.  Help!  I really don't know what to do to get the mouse working.  I have tried just about everything I can think of to set or change it that file, but still no mouse.  I must be missing something.  ```
# Configuration file for svgalib. Default location is /etc/vga.
# Other config file locations:	~/.svgalibrc
# 				where SVGALIB_CONFIG_FILE points
# Lines starting with '#' are ignored.

# If you have two vga cards with the same pci vendor id, svgalib will try
# to use the first one, even if the second one is active. In that case,
# use PCIStart to force starting the search for a vga card only at a
# specific bus and device numbers. For example, an AGP card is usually on
# bus 1, while pci is on bus 0, so to use the AGP card, uncomment:

# PCIStart 1 0

# Have a deep look at README.config to see what can do here (especially
# for mach32).

# Mouse type:

# mouse Microsoft	# Microsoft
# mouse MouseSystems	# Mouse Systems
# mouse MMSeries	# Logitech MM Series
# mouse Logitech	# Logitech protocol (old, newer mice use Microsoft protocol)
# mouse Busmouse	# Bus mouse
# mouse PS2		# PS/2 mouse
# mouse MouseMan	# Logitech MouseMan
# mouse Spaceball	# Spacetec Spaceball
# mouse IntelliMouse	# Microsoft IntelliMouse or Logitech MouseMan+ on serial port
# mouse IMPS2		# Microsoft IntelliMouse or Logitech MouseMan+ on PS/2 port
# mouse pnp		# plug'n'pray
# mouse WacomGraphire   # Wacom Graphire tablet/mouse
# mouse DRMOUSE4DS	# Digital Research double-wheeled mouse
# mouse none		# None
mouse PS2 

# (DEBIAN NOTE: the mouse used to default to microsoft, but this was changed
#  to fix bug #13458. If your mouse used to work fine, you can simply change
#  it back to read "microsoft" again. If you are careful to change *only that
#  one word*, and not to add or remove extra whitespace, the package
#  installation will continue to update this file without requiring user
#  intervention because of a modified config file.
#  This applies to all mouse types, not just microsoft.)

# Mouse/keyboard customisation by 101 (Attila Lendvai). If you have any good
# ideas you can reach me at 101@kempelen.inf.bme.hu

# mouse_accel_type	normal	# No acceleration while delta is less then
				# threshold but delta is multiplied by
				# mouse_accel_mult if more. Originally done by
				# Mike Chapman mike@paranoia.com

mouse_accel_type	power	# The acceleration factor is a power function
				# of delta until it reaches m_accel_mult. It
				# starts from the coordinate 
				# [1, 1 + m_accel_offset] and goes to
				# [m_accel_thresh, m_accel_mult]. If delta
				# is bigger then m_accel_thresh it is a plain
				# constant (m_accel_mult). It is the f(delta)
				# function with which the delta itself will be
				# multiplied. m_accel_offset is 1 by default,
				# so for delta = 1 the accelerated delta will
				# remain 1 (You don't lose resolution). The
				# starting point of the f(delta) function
				# might be moved along the Y axis up/down with
				# m_accel_offset thus defining the initial
				# minimum acceleration (for delta = 1).
				# Basically it's like the normal mode but the
				# acceleration factor grows as you move your
				# mouse faster and faster, not just turns in
				# and out. Threshold is the point from where
				# the f(delta) function gets linear.
				# This is the one I use for *uaking... =)

# mouse_accel_type	off	# No comment...


mouse_accel_mult	60	# This is the number with which delta will
				# be multiplied. Basically it's the number
				# that defines how big the acceleration will
				# be

mouse_accel_thresh	4	# This is the threshold. See description by
				# power

mouse_accel_power	0.8	# This is the second parameter of the power
				# function used in power mode. Used only by
				# the power mode

mouse_accel_offset	30	# This is the offset of the starting point
				# on the Y axis. With this you can define the
				# number that will multiply delta = 1 so it's
				# the initial acceleration.

# mouse_accel_maxdelta	600	# This is an upper limit for delta after
				# the acceleration was applied

# mouse_maxdelta	30	# This is an upper limit for the delta
				# before the acceleration. With this one you
				# can limit the biggest valid delta that
				# comes from the mouse.

# mouse_force			# Force parameters even if they seem strange
				# By default svgalib prints an error if any
				# of the numbers are somhow out of the
				# reasonable limit, (Like a negative mult :)
				# and uses the default that's in vgamouse.h

# Usually /dev/mouse will be a link to the mouse device.
# However, esp. with the Spacetec Spaceball you may
# want to specify a different device for svgalib to use

# mdev /dev/ttyS0 # mouse is at /dev/ttyS0

# Some multiprotocol mice will need one of the following:

# setRTS   # set the RTS wire.
# clearRTS # clear the RTS wire.
# leaveRTS # leave the RTS wire alone (default) (Wire is usually set)
# setDTR   # set the DTR wire.
# clearDTR # clear the DTR wire.
# leaveDTR # leave the DTR wire alone (default) (Wire is usually set)

# On mice such as the Microsoft IntelliMouse and Logitech MouseMan+, turning
# the wheel rotates the mouse around the X axis. mouse_wheel_steps controls
# how many steps make up a full 360-degree turn and thus how much rotation
# occurs with each step. The default is 18 steps (20 degrees per step), the
# real-world value for the IntelliMouse. Adjust it to match your mouse or to
# suit your preferences; a negative number reverses the direction and zero
# disables rotation.

# mouse_wheel_steps 18		# For MS IntelliMouse (default)
# mouse_wheel_steps 24		# For Logitech FirstMouse+
# mouse_wheel_steps -18		# Reverses direction
# mouse_wheel_steps 0		# Disables rotation

# mouse_fake_kbd_event sends a fake keyboard event to the program when the
# wheel on a Microsoft IntelliMouse, Logitech MouseMan+, or similar wheel
# mouse is turned. This can be useful for programs that do not recognize the
# Z axis, but only works with some programs that use raw keyboard.
# The format is:
#
#   mouse_fake_kbd_event upscancode downscancode
#
# The up and down scancodes are the scancodes of the keys to simulate when
# the wheel is turned up and down, respectively.
#
# Scancodes can be specified numerically or symbolically; the symbolic names
# are determined by the keymap (see below), if no keymap is loaded the default
# is the standard US QWERTY keyboard with the following names available:
# letters (a-z), numbers (zero-nine), function keys (F1-F12), the keypad
# numbers (KP_0-KP_9) and other keys (KP_Multiply, KP_Subtract, KP_Add,
# KP_Period, KP_Enter, and KP_Divide), and the following - minus, equal,
# Delete, Tab, bracketleft, bracketright, Return, Control, semicolon,
# apostrophe, grave, Shift, backslash, comma, period, slash, Shift, Alt, space,
# Caps_Lock, Num_Lock, Scroll_Lock, Last_Console, less, Control_backslash,
# AltGr, Break, Find, Up, Prior, Left, Right, Select, Down, Next, Insert,
# and Remove.
#
# Note that this option has no effect unless the IntelliMouse or IMPS2 mouse
# type is used (see above). Also note that the simulated keypresses are
# instantaneous, so they cannot be used for functions that require a key to
# be held down for a certain length of time.

#  This example simulates a press of the left bracket ([) when the wheel is
#  turned up and a press of the right bracket (]) when the wheel is turned
#  down (good for selecting items in Quake II):
# mouse_fake_kbd_event bracketleft bracketright

# Keyboard config:

# kbd_keymap allows you to use an alternate keyboard layout with programs that
# use raw keyboard support by translating scancodes from the desired layout to
# their equivalents in the layout expected by the program. This option has no
# affect on programs that do not use raw keyboard.
#
# Keymap files to convert between any two arbitrary keyboard layouts can be
# generated with the svgakeymap utility, but there are limitations to the
# translations that can be performed. Read the file README.keymap in the
# svgalib documentation directory for more in-depth information.
#
# You must specify the full path to the keymap file; it is recommended that
# keymaps be kept in the same directory as libvga.config, normally /etc/vga.
# The keymap specified in the configuration file can be overriden by setting
# the environment variable SVGALIB_KEYMAP to point to another keymap file;
# this can be useful for setting keymaps on a per-program basis.
#
#  This example will use the provided US-Dvorak to US-QWERTY map to allow a
#  Dvorak keyboard layout to be used with a program that expects a standard US
#  QWERTY keyboard, for instance Quake:
# kbd_keymap /etc/vga/dvorak-us.keymap

# There is a potential security risk in allowing users to remap keyboard
# scancodes at will; with this option enabled only keymap files owned by
# root can be used. Normally you should leave this on, but if you have a
# single-user box or you really trust your users you may find it convenient
# to run without it and allow users to load arbitrary keymaps.

kbd_only_root_keymaps

# kbd_fake_mouse_event, as it says, sends a fake mouse event to the program.
# The format is: kbd_fake_mouse_event scancode [flag(s)] command [argument]
#   Scancode is a raw scancode or a descriptive name, the same as with fake
#   keyboard events (see above). If you use keymap conversion, specify
#   scancodes for the keyboard layout the program will receive.
#   Flags:   down   - trigger event when the key is pressed (default)
#	     up     - the opposite
#	     both   - trigger in both case, if pressed/released
#	     repeat - repeat events if the key is kept pressed (off by default)
#   commands: delta[xyz]  - send a fake delta event as if you have moved your
#	 		    mouse. If the parameter is 'off' / 'on' it will turn
#			    off/on the respective mouse axis (requires a
#			    parameter, of course)
#	      button[123] - send a fake event that the mouse button is pressed
#			    or released that's given by the parameter.
# 			    ('pressed' or 'released')
# Here are some examples:

#  This is one I use in *uake: it turns around, looks down a bit and when the
#  key is released it does the opposite, so it gets back to the starting state.
#  With this one and the help of a rocket you can fly though the whole map :)
#  (Scancode 28 is enter)
# kbd_fake_mouse_event 28 both deltax 8182 down deltay -1500 up deltay 1500

#  This one will switch off the y axis of the mouse while the key (right ctrl)
#  is kept pressed.
# kbd_fake_mouse_event 97 down deltay off  up deltay on

#  This one is the same as if you were pressing the left mouse button. (But
#  if you move your mouse then the button state will reset even if you keep
#  right ctrl down...)
# kbd_fake_mouse_event 97 down button1 pressed up button1 released

# Monitor type:

# Only one range can be specified for the moment.  Format:
# HorizSync min_kHz max_kHz
# VertRefresh min_Hz max_Hz

# Typical Horizontal sync ranges
# (Consult your monitor manual for Vertical sync ranges)
#
# 31.5 - 31.5 kHz (Standard VGA monitor, 640x480 @ 60 Hz)
# 31.5 - 35.1 kHz (Old SVGA monitor, 800x600 @ 56 Hz)
# 31.5 - 35.5 kHz (Low-end SVGA, 8514, 1024x768 @ 43 Hz interlaced)
# 31.5 - 37.9 kHz (SVGA monitor, 800x600 @ 60 Hz, 640x480 @ 72 Hz)
# 31.5 - 48.3 kHz (SVGA non-interlaced, 800x600 @ 72 Hz, 1024x768 @ 60 Hz)
# 31.5 - 56.0 kHz (high frequency, 1024x768 @ 70 Hz)
# 31.5 - ???? kHz (1024x768 @ 72 Hz)
# 31.5 - 64.3 kHz (1280x1024 @ 60 Hz)

HorizSync 31.5 35.5
VertRefresh 50 90

# If you have a NeoMagic card on a Toshiba Libretto 100, 110 use that instead

# HorizSync 31.5 70
# VertRefresh 50 100
# Modeline "800x480"   50  800  856  976 1024   480  483  490  504 +hsync +vsync
# newmode  800 480 256       800 1
# newmode  800 480 32768    1600 2
# newmode  800 480 65536    1600 2
# newmode  800 480 16777216 2400 3

# Monitor timings
#
# These are prefered over the default timings (if monitor and chipset
# can handle them). Not all drivers use them at the moment, and Mach32
# has its own syntax (see below).
# The format is identical to the one used by XFree86, but the label
# following the modeline keyword is ignored by svgalib.
#
# Here some examples:

# modeline "640x480@100"  43  640  664  780  848   480  483  490  504
# modeline "800x600@73"   50  800  856  976 1024   600  637  643  666
# modeline "1024x768@75"  85 1024 1048 1376 1400   768  771  780  806

# It seems there is a need for a 512x384 mode, this timing was donated
# by Simon Hosie <gumboot@clear.net.nz>: (it is 39kHz horz by 79Hz vert)

# Modeline "512x384@79"     25.175 512  522  598  646   384  428  436  494

# Here's a 400x300 Modeline (created by svidtune). Note that for
# doublescan modes, the Vertical values are half the real one (so XFree86
# modelines can be used). 

# Modeline "400x300@72" 25.000 400 440 504 520 300 319 322 333 doublescan

# Here is a mode for a ZX Spectrum emulator:
# Modeline "256x192@73" 12.588 256 269 312 360 192 208 212 240 doublescan
# newmode 256 192 256 256 1

# the width must be divisible by 8. Some cards require even divisiblity by
# 16, so that's preferable, since there are no standard modes where the
# width is not divisible by 16.

# The following modes are defined in svgalib, but have no timings in
# timing.c, so you'll have to add a modeline in order to use them:
# 1280x720, 1360x768, 1800x1012, 1920x1080, 1920x1440, 2048x1152
# and 2048x1536   

# Mach32 timings:

# e.g. Setup a 320x200 mode for the mach32:

#define 320x200x32K 320x200x64K 320x200x16M 320x200x16M32
#                     16 320 392 464 552 200 245 265 310

# These are REQUIRED for above mode, please edit to suit your monitor.
# (No, I won't pay for a new one)
# HorizSync 29 65
# VertRefresh 42 93.5

# Chipset type:
#
# Use one of the following force chipset type.
# Autodetects if no chipset is specified.
#
# If you have a PCI or AGP card, don't use chipset type forcing.
# If the card is not autodetected, its a bug, and it will probably
# not work even with forcing. Try running vgatest (with no chipset 
# line), and send to me (matan@svgalib.org) the output, a copy of
# /proc/pci (or lspci -n -vv) and whatever info you have on the card. 
#
# If a chipset driver gives trouble, try forcing VGA.

# chipset VGA		# Standard VGA
# chipset EGA		# EGA
# chipset ET3000	# Tseng ET3000
# chipset ET4000	# Tseng ET4000
# chipset Cirrus	# Cirrus Logic GD542x
# chipset TVGA		# Trident TVGA8900/9000
# chipset Oak		# Oak Technologies 037/067/077
# chipset S3		# S3 chipsets
# chipset GVGA6400	# Genoa 6400
# chipset ARK		# ARK Logic
# chipset ATI		# old ATI VGA
# chipset Mach32	# ATI Mach32
# chipset ALI		# ALI2301
# chipset Mach64	# ATI Mach64 - deprecated
# chipset ET6000        # Tseng ET6000
# chipset APM	 	# Alliance Technology AT 24/25/3D
# chipset NV3		# nVidia Riva 128 / TNT / GeForce
# chipset VESA          # nicely behaved Vesa Bioses
# chipset MX		# MX86251 (some Voodoo Rush boards)
# chipset PARADISE 	# WD90C31
# chipset RAGE		# RagePro (and might work with some older mach64)
# chipset BANSHEE	# Banshee/V3.
# chipset SIS		# SiS 5597/6326/620/530 cards / integrated vga.
# chipset I740		# Intel i740 based cards.
# chipset NEOMAGIC
# chipset LAGUNA	# Cirrus Logic Laguna series (546X)
# chipset FBDEV		# Use kernel fbdev, instead of direct hardware.
# chipset G400		# Matrox Mystique/G100/G200/G400/G450
# chipset R128		# Ati Rage128
# chipset SAVAGE	# S3 chipsets Savage
# chipset C&T		# Chips and Technologies
chipset R128

# EGA Color/mono mode:
# Required if chipset is EGA.
#
# Use one of the following digits to force color/mono:

# monotext  # Card is in monochrome emulation mode
# colortext # Card is in color emulation mode
colortext

# RAMDAC support:
# Some chipsets (e.g. S3 and ARK) allows specifying a RAMDAC type.
# If your RAMDAC is not autodetected, you can try specifying it.
# Do NOT specify a RAMDAC if you card uses the S3 Trio chipset
# (the RAMDAC is built in).

# Ramdac Sierra32K
# Ramdac SC15025
# Ramdac SDAC         # S3 SDAC
# Ramdac GenDAC       # S3 GenDAC
# Ramdac ATT20C490    # AT&T 20C490, 491, 492 (and compatibles)
# Ramdac ATT20C498    # AT&T 20C498
# Ramdac IBMRGB52x    # IBM RGB524, 526, 528 (and compatibles)

# Dotclocks:
# Some chipsets needs a list of dot clocks for optimum operation.  Some
# includes or supports a programmable clock chip.  You'll need to specify
# them here.

# Fixed clocks example:
# (The following is just an example, get the values for your card from
#  you XF86Config)

# Clocks 25.175 28.3 40 70 50 75 36 44.9 0 118 77 31.5 110 65 72 93.5

# Programmable clockchip example:

# Clockchip ICD2061A  # The only one supported right now



# Here are miscellaneous options to help with specific problems.

# VesaText	      # Helps the VESA driver with text mode restoration
		      # problems.

# VesaSave 14	      # changing value might help text mode restoring
		      # problems with VESA driver. Legal values: 0-15

# NoVCControl	      # Disables svgalib's finding a new VC if run
		      # from X. Good fo using dumpreg under X, but
		      # probably bad for standard usage.


# RageDoubleClock     # If your card is based on ATI's rage card, and
		      # the pixel clock is double what it should be 
		      # (main symptom is some modes are out of sync),
		      # try enabling this. If it helps, please report to
		      # me (matan@svgalib.org) 

# NeoMagicLibretto100
		      # Enable if you have a NeoMagic card on a Toshiba
		      # Libretto 100, 110, etc


```


BTW, I am running breezy on a 600mhz celeron, w/ ati rage 128 32 mg vid card.

This is my "learning 'bout Linux box"...and getting Quake2 to run is just one more thing to learn. :) 


-Pat

---

### Post by 4linux on 2005-10-25
Bump.... 

Anybody?

-Pat

---

### Post by mike998 on 2005-10-25
Okay - the loki installer works, but I don't have any sound.
The console shows the following error :
```
SDL: Audio timeout - buggy audio driver? (disabled)
audio: Bad file descriptor

```

Does anyone have any ideas?

---

### Post by TuxicGuy on 2005-10-25
I have the same question - i installed the quake2 and quake2-data files from synaptic, but i have no idea how to get the game data files ( I have the quake2 CDROM). The description for quake2-data tells me that i will be 'asked' where to install from - either CD or the internet - I assumed that there would be some script which would do the relevant steps, but i can't seem to find anything. Could someone please guide me as to the correct steps?

---

### Post by benplaut on 2005-10-25
[QUOTE=mike998]Okay - the loki installer works, but I don't have any sound.
The console shows the following error :
```
SDL: Audio timeout - buggy audio driver? (disabled)
audio: Bad file descriptor

```

Does anyone have any ideas?[/QUOTE]

yeah... same here, but it isn't hard to fix:

gksudo gedit

and put this in a blank file:

SDL_DSP_NOSELECT='1'; export SDL_DSP_NOSELECT; quake2

...save it as whatever you want in /usr/bin, "chmod +x" it to make it executable, then type whatever you named it in a terminal :) 

if it complains that it can't find an audio device, go to System>Prefences>Sound and uncheck the first box (but recheck it when you're done playing!)

<<edit>>

for the loki installer (i use it too), replace the "quake2" with "sh /location/to/quake2.sh", that file should be wherever you installed to. by the dafault location, it would be "sh ~/quake2/quake2.sh"

---

### Post by TuxicGuy on 2005-10-26
I answered my own question :) - sudo dpkg-reconfigure quake2-data will install the data from CD - however, now that it's running - Sound is really Choppy - can someone tell me how to fix this?  - setting snddriver to anything other than   oss (inside config.cfg) causes segmentation fault when starting.

Another question : - to run quake2, i need to get to terminal and type "quake2" - i would like to create a menu entry that does this. I can create the entry under Applications -> Games -> quake 2 , but i don't know what command to assign to the entry. Could some one enlighten me as to this?

Thanks

---

### Post by dmn_clown on 2005-10-26
[QUOTE=TuxicGuy]Another question : - to run quake2, i need to get to terminal and type "quake2" - i would like to create a menu entry that does this. I can create the entry under Applications -> Games -> quake 2 , but i don't know what command to assign to the entry. Could some one enlighten me as to this?

Thanks[/QUOTE]

There are several ways of doing this, the simplest being just adding the entry /usr/games//quake2 to your menu.

Another way is to write a short script using your favorite text editor, something along the lines of:  
```
#!/bin/sh
quake2 +set vid_ref glx
exit
```

save that script in a place where you won't delete it with a name like q2.sh, make it executable with ```
chmod +x /PATH/TO/q2.sh
``` then add the script to the menu in the above manner.

The "script menu entry" comes in handy when starting games in wine, cedega, or in a chroot environment, it is generally a waste of effort for a native game.

---

### Post by GIBson3 on 2005-10-27
[QUOTE=TuxicGuy]Another question : - to run quake2, i need to get to terminal and type "quake2" - i would like to create a menu entry that does this. I can create the entry under Applications -> Games -> quake 2 , but i don't know what command to assign to the entry. Could some one enlighten me as to this?[/QUOTE]


heh you could also do this the "lazy way"  ;)

[applications]->[system tools]->[applications menu editor]

open the [games] section and make a new enitity and use the command "/path/to/quake2"  or just "quake2" will work if it's in a directory in your PATH ;)

---

### Post by TuxicGuy on 2005-10-28
Another question -  would like to play quake2 full screen - without the title bar or the gnome taskbar at the bottom - is this possible? - i also get a query when i run quake2 telling me about the security implications of running q2 on a network -- i have to type 'y' to continue each and every time i load the game - is there a way to switch this off?
Thanks in advance

---

### Post by kverde on 2005-11-22
I too would like to know -- how to get quake and DOOM for that matter to play in full screen?  

[QUOTE=TuxicGuy]Another question -  would like to play quake2 full screen - without the title bar or the gnome taskbar at the bottom - is this possible? - i also get a query when i run quake2 telling me about the security implications of running q2 on a network -- i have to type 'y' to continue each and every time i load the game - is there a way to switch this off?
Thanks in advance[/QUOTE]

---

### Post by Matt Houston on 2005-12-04
Aaaaaaaah, that was it, I can't believe I didn't try the other install friles. That felt so good when I typed in doom3 in the terminal and it started up. Thanks.

---

### Post by brad84 on 2005-12-05
*MY FIRST POST!!!!!*
Personally, I would just use Jake2. Its a Java version of the Quake 2 engine and it takes about 2 minutes to install on any Java capable OS.

[http://www.bytonic.de/html/jake2.html](http://www.bytonic.de/html/jake2.html)

ENJOY!

---

### Post by mr_niceguy on 2005-12-09
[QUOTE=brad84]I would just use Jake2.

[http://www.bytonic.de/html/jake2.html](http://www.bytonic.de/html/jake2.html)[/QUOTE]

I can second that. It even accepted my favourite Homer Simpson model.

---

### Post by EvilBill on 2005-12-09
[QUOTE=TuxicGuy]I answered my own question :) -**_ sudo dpkg-reconfigure quake2-data_** will install the data from CD - however, now that it's running - Sound is really Choppy - can someone tell me how to fix this?  - setting snddriver to anything other than   oss (inside config.cfg) causes segmentation fault when starting.

Another question : - to run quake2, i need to get to terminal and type "quake2" - i would like to create a menu entry that does this. I can create the entry under Applications -> Games -> quake 2 , but i don't know what command to assign to the entry. Could some one enlighten me as to this?

Thanks[/QUOTE]

I ran that command, & it brought up a screen like the one when I installed Java 1.4 It took me to id Software for a 45min. d/l then after it was done I ran...

quake2

.....in the terminal & it gave me some song & dance about not having a joystick. ????

I installed those 2 quake things from SPM and they are installed somewhere, I cannot find them for nothing.

Does anyone know what I did wrong or whatever? I tried installing wine from that other site with the terminal command leading to a different source. it would not work either, it got to the site o.k. but that was it?

And I tried that Java Quake also, no luck there either, it would let me d/l it for abourt 5 minutes then it stopped & said it would not work. I am batting 1000 on this...........[frown].........

---

### Post by EvilBill on 2005-12-09
I got the latest version of wine installed & configured. Plus I still have those 2 quake 2 thingies installed somewhere...........;) :( ...I may be headed in the right dirrection....??

:???: :)

---

### Post by joelito on 2005-12-11
Sorry but

The thing is that the quake2 command (installed from synaptic) includes a warning message that runs from the console what I did was creating the menu entry(kde) pointing to '/usr/lib/games/quake2/quake2.real' as for the sound, what I did was setting up artsdsp to use alsa and then, the command i use is 
```

artsdsp /usr/lib/games/quake2/quake2.real

```

---

### Post by ishkabob on 2005-12-11
For those of you who are having trouble with the mouse in Quake 2 under the GLX OpenGL driver, open up your console in Quake 2 and type "set _windowed_mouse 1".  If that doesn't work try "set _windowed_mouse 0".  You can make that permanent by adding that as a line to your baseq2/config.cfg file.

On another note, if anyone has gotten the GLX OpenGL driver to work in fullscreen, unwindowed mode, let me know.  It is much more convenient as it interfaces with the window manager better than SDL.  Also, some of my textures look a little weird, but I'm not sure if that is just because I haven't played in awhile.  Perhaps someone has some tweaking advice on that.

---

### Post by Liam on 2005-12-13
Cribbed this from [Ubunu-ES]("http://www.ubuntu-es.org/node/8036"), for those of you who were having problems with the sound driver, like me:

quake2 +set snddriver ao +set snddevice oss

That's with softsdl for video.

---

### Post by cydermaster on 2006-03-31
Thanks for the tip, Liam - got me fragging in style (ie. *with* sound)!

:D

---

### Post by sorceror on 2006-09-26
I wanted full screen Quake 2, and I hadn't found this thread yet, so I compiled my own. You can get the source here:

[http://www.icculus.org/quake2/files/quake2-r0.16.1.tar.gz](http://www.icculus.org/quake2/files/quake2-r0.16.1.tar.gz)

Now, to compile, you'll need to install a bunch of packages. I needed at least:

build-essential
libsdl1.2-dev
libxxf86dga-dev
libxxf86vm-dev

 Then, extract the source (tar xzvf quake2-r0.16.1.tar.gz), go into the top directory (with the file "Makefile" in it), and run:

 make

 This will first build a 'debug' and then a 'release' version. You'll find the release version in the "releasei386" directory. It includes a bunch of executables, namely:

quake2          - game executable
sdlquake2       - SDL game executable
gamei386.so     - the main core of the game
ref_glx.so      - OpenGL renderer
ref_sdlgl.so    - SDL OpenGL renderer
ref_softx.so    - Software (ugly :-> ) renderer
ref_softsdl.so  - SDL software renderer

Copy these to the quake2 directory; basically the directory that has "baseq2" in it. (Note: not *in* the baseq2 directory, just *above* it.)

This gave me good sound, full-screen goodness, etc. Perhaps I might have time to package this up at some point, but that will probably take a geologic era or two.

---

### Post by xfile087 on 2007-03-03
Brilliant, I did that and now I have sound - even if it does crackle.

---

### Post by Phenax on 2007-03-03
> **xfile087 said:**
> Brilliant, I did that and now I have sound - even if it does crackle.

Run sdlquake2 instead of quake2, Icculus' without SDL is pretty cruddy in my experience. 

Also, if you want to compile Icculus' Quake 2 on x86_64 you'll need to add this patch in, because mremap on x86_64 won't work without it.
```

diff -r -u quake2-r0.16.1.orig/src/linux/q_shlinux.c quake2-r0.16.1/src/linux/q_shlinux.c
--- quake2-r0.16.1.orig/src/linux/q_shlinux.c	2002-02-09 23:09:23.000000000 +0100
+++ quake2-r0.16.1/src/linux/q_shlinux.c	2006-12-14 20:07:11.000000000 +0100
@@ -17,6 +17,7 @@
 Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
 
 */
+#define _GNU_SOURCE
 #include <sys/types.h>
 #include <sys/stat.h>
 #include <errno.h>

```

---


---
title: "XKB Extension not present"
date: 2006-12-27
forum: Desktop Environments
---

### Post by Theimon on 2006-12-27
I installed Beryl from the repo's on my Dapper desktop which went fine. But when I rebooted, I noticed some keyboard shortcuts weren't working anymore and keys didn't get any acceleration.
I've tried the solution on the bottom of this page: [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#.22I_have_no_keyboards_listed_in_gnome-keyboard-preferences.3F.22](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#.22I_have_no_keyboards_listed_in_gnome-keyboard-preferences.3F.22)
but that didn't help at all.
When I entered setxkbmap in a terminal I got the error "XKB extension not present on :0.0
".
My xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
```
And when I "locate" for xkb:
```

/var/lib/dpkg/info/libxkbfile1.list
/var/lib/dpkg/info/libxkbfile1.md5sums
/var/lib/dpkg/info/libxkbfile1.shlibs
/var/lib/dpkg/info/xkbutils.list
/var/lib/dpkg/info/xkbutils.md5sums
/var/lib/xkb
/etc/X11/xkb
/etc/X11/xkb/compat
/etc/X11/xkb/compat/README
/etc/X11/xkb/compat/accessx
/etc/X11/xkb/compat/basic
/etc/X11/xkb/compat/complete
/etc/X11/xkb/compat/default
/etc/X11/xkb/compat/iso9995
/etc/X11/xkb/compat/japan
/etc/X11/xkb/compat/keypad
/etc/X11/xkb/compat/ledcaps
/etc/X11/xkb/compat/lednum
/etc/X11/xkb/compat/ledscroll
/etc/X11/xkb/compat/level5
/etc/X11/xkb/compat/misc
/etc/X11/xkb/compat/mousekeys
/etc/X11/xkb/compat/norepeat
/etc/X11/xkb/compat/pc
/etc/X11/xkb/compat/pc98
/etc/X11/xkb/compat/xfree86
/etc/X11/xkb/compat/xtest
/etc/X11/xkb/compiled
/etc/X11/xkb/geometry
/etc/X11/xkb/geometry/digital_vndr
/etc/X11/xkb/geometry/digital_vndr/lk
/etc/X11/xkb/geometry/digital_vndr/pc
/etc/X11/xkb/geometry/digital_vndr/unix
/etc/X11/xkb/geometry/ibm_vndr
/etc/X11/xkb/geometry/ibm_vndr/thinkpad
/etc/X11/xkb/geometry/sgi_vndr
/etc/X11/xkb/geometry/sgi_vndr/O2
/etc/X11/xkb/geometry/sgi_vndr/indigo
/etc/X11/xkb/geometry/sgi_vndr/indy
/etc/X11/xkb/geometry/README
/etc/X11/xkb/geometry/amiga
/etc/X11/xkb/geometry/ataritt
/etc/X11/xkb/geometry/chicony
/etc/X11/xkb/geometry/dell
/etc/X11/xkb/geometry/everex
/etc/X11/xkb/geometry/fujitsu
/etc/X11/xkb/geometry/hp
/etc/X11/xkb/geometry/keytronic
/etc/X11/xkb/geometry/kinesis
/etc/X11/xkb/geometry/macintosh
/etc/X11/xkb/geometry/microsoft
/etc/X11/xkb/geometry/nec
/etc/X11/xkb/geometry/northgate
/etc/X11/xkb/geometry/pc
/etc/X11/xkb/geometry/sony
/etc/X11/xkb/geometry/sun
/etc/X11/xkb/geometry/winbook
/etc/X11/xkb/keycodes
/etc/X11/xkb/keycodes/digital_vndr
/etc/X11/xkb/keycodes/digital_vndr/lk
/etc/X11/xkb/keycodes/digital_vndr/pc
/etc/X11/xkb/keycodes/sgi_vndr
/etc/X11/xkb/keycodes/sgi_vndr/indigo
/etc/X11/xkb/keycodes/sgi_vndr/indy
/etc/X11/xkb/keycodes/sgi_vndr/iris
/etc/X11/xkb/keycodes/README
/etc/X11/xkb/keycodes/aliases
/etc/X11/xkb/keycodes/amiga
/etc/X11/xkb/keycodes/ataritt
/etc/X11/xkb/keycodes/evdev
/etc/X11/xkb/keycodes/fujitsu
/etc/X11/xkb/keycodes/hp
/etc/X11/xkb/keycodes/ibm
/etc/X11/xkb/keycodes/macintosh
/etc/X11/xkb/keycodes/powerpcps2
/etc/X11/xkb/keycodes/sony
/etc/X11/xkb/keycodes/sun
/etc/X11/xkb/keycodes/xfree86
/etc/X11/xkb/keycodes/xfree98
/etc/X11/xkb/keymap
/etc/X11/xkb/keymap/digital_vndr
/etc/X11/xkb/keymap/digital_vndr/us
/etc/X11/xkb/keymap/sgi_vndr
/etc/X11/xkb/keymap/sgi_vndr/be
/etc/X11/xkb/keymap/sgi_vndr/bg
/etc/X11/xkb/keymap/sgi_vndr/ca
/etc/X11/xkb/keymap/sgi_vndr/ch
/etc/X11/xkb/keymap/sgi_vndr/cz
/etc/X11/xkb/keymap/sgi_vndr/de
/etc/X11/xkb/keymap/sgi_vndr/dk
/etc/X11/xkb/keymap/sgi_vndr/dvorak
/etc/X11/xkb/keymap/sgi_vndr/es
/etc/X11/xkb/keymap/sgi_vndr/fi
/etc/X11/xkb/keymap/sgi_vndr/fr
/etc/X11/xkb/keymap/sgi_vndr/gb
/etc/X11/xkb/keymap/sgi_vndr/hu
/etc/X11/xkb/keymap/sgi_vndr/it
/etc/X11/xkb/keymap/sgi_vndr/jp
/etc/X11/xkb/keymap/sgi_vndr/no
/etc/X11/xkb/keymap/sgi_vndr/pl
/etc/X11/xkb/keymap/sgi_vndr/pt
/etc/X11/xkb/keymap/sgi_vndr/ru
/etc/X11/xkb/keymap/sgi_vndr/se
/etc/X11/xkb/keymap/sgi_vndr/sk
/etc/X11/xkb/keymap/sgi_vndr/th
/etc/X11/xkb/keymap/sgi_vndr/us
/etc/X11/xkb/keymap/sun_vndr
/etc/X11/xkb/keymap/sun_vndr/all
/etc/X11/xkb/keymap/sun_vndr/de
/etc/X11/xkb/keymap/sun_vndr/es
/etc/X11/xkb/keymap/sun_vndr/fi
/etc/X11/xkb/keymap/sun_vndr/fr
/etc/X11/xkb/keymap/sun_vndr/no
/etc/X11/xkb/keymap/sun_vndr/pl
/etc/X11/xkb/keymap/sun_vndr/ru
/etc/X11/xkb/keymap/sun_vndr/se
/etc/X11/xkb/keymap/sun_vndr/uk
/etc/X11/xkb/keymap/sun_vndr/us
/etc/X11/xkb/keymap/README
/etc/X11/xkb/keymap/amiga
/etc/X11/xkb/keymap/ataritt
/etc/X11/xkb/keymap/macintosh
/etc/X11/xkb/keymap/sony
/etc/X11/xkb/keymap/xfree86
/etc/X11/xkb/keymap/xfree98
/etc/X11/xkb/rules
/etc/X11/xkb/rules/README
/etc/X11/xkb/rules/base
/etc/X11/xkb/rules/base.lst
/etc/X11/xkb/rules/base.xml
/etc/X11/xkb/rules/sgi
/etc/X11/xkb/rules/sun
/etc/X11/xkb/rules/xfree86
/etc/X11/xkb/rules/xfree86.lst
/etc/X11/xkb/rules/xfree86.xml
/etc/X11/xkb/rules/xfree98
/etc/X11/xkb/rules/xkb.dtd
/etc/X11/xkb/rules/xorg
/etc/X11/xkb/rules/xorg.lst
/etc/X11/xkb/rules/xorg.xml
/etc/X11/xkb/semantics
/etc/X11/xkb/semantics/basic
/etc/X11/xkb/semantics/complete
/etc/X11/xkb/semantics/default
/etc/X11/xkb/semantics/xtest
/etc/X11/xkb/symbols
/etc/X11/xkb/symbols/digital_vndr
/etc/X11/xkb/symbols/digital_vndr/lk
/etc/X11/xkb/symbols/digital_vndr/pc
/etc/X11/xkb/symbols/digital_vndr/us
/etc/X11/xkb/symbols/digital_vndr/vt
/etc/X11/xkb/symbols/fujitsu_vndr
/etc/X11/xkb/symbols/fujitsu_vndr/jp
/etc/X11/xkb/symbols/fujitsu_vndr/us
/etc/X11/xkb/symbols/hp_vndr
/etc/X11/xkb/symbols/hp_vndr/us
/etc/X11/xkb/symbols/macintosh_vndr
/etc/X11/xkb/symbols/macintosh_vndr/apple
/etc/X11/xkb/symbols/macintosh_vndr/ch
/etc/X11/xkb/symbols/macintosh_vndr/de
/etc/X11/xkb/symbols/macintosh_vndr/dk
/etc/X11/xkb/symbols/macintosh_vndr/es
/etc/X11/xkb/symbols/macintosh_vndr/fi
/etc/X11/xkb/symbols/macintosh_vndr/fr
/etc/X11/xkb/symbols/macintosh_vndr/gb
/etc/X11/xkb/symbols/macintosh_vndr/is
/etc/X11/xkb/symbols/macintosh_vndr/it
/etc/X11/xkb/symbols/macintosh_vndr/nl
/etc/X11/xkb/symbols/macintosh_vndr/no
/etc/X11/xkb/symbols/macintosh_vndr/pt
/etc/X11/xkb/symbols/macintosh_vndr/se
/etc/X11/xkb/symbols/macintosh_vndr/us
/etc/X11/xkb/symbols/nec_vndr
/etc/X11/xkb/symbols/nec_vndr/jp
/etc/X11/xkb/symbols/sgi_vndr
/etc/X11/xkb/symbols/sgi_vndr/jp
/etc/X11/xkb/symbols/sony_vndr
/etc/X11/xkb/symbols/sony_vndr/us
/etc/X11/xkb/symbols/sun_vndr
/etc/X11/xkb/symbols/sun_vndr/cs
/etc/X11/xkb/symbols/sun_vndr/cz
/etc/X11/xkb/symbols/sun_vndr/de
/etc/X11/xkb/symbols/sun_vndr/dk
/etc/X11/xkb/symbols/sun_vndr/es
/etc/X11/xkb/symbols/sun_vndr/fi
/etc/X11/xkb/symbols/sun_vndr/fr
/etc/X11/xkb/symbols/sun_vndr/gb
/etc/X11/xkb/symbols/sun_vndr/gr
/etc/X11/xkb/symbols/sun_vndr/hu
/etc/X11/xkb/symbols/sun_vndr/it
/etc/X11/xkb/symbols/sun_vndr/jp
/etc/X11/xkb/symbols/sun_vndr/ko
/etc/X11/xkb/symbols/sun_vndr/lt
/etc/X11/xkb/symbols/sun_vndr/lv
/etc/X11/xkb/symbols/sun_vndr/nl
/etc/X11/xkb/symbols/sun_vndr/no
/etc/X11/xkb/symbols/sun_vndr/pl
/etc/X11/xkb/symbols/sun_vndr/pt
/etc/X11/xkb/symbols/sun_vndr/ru
/etc/X11/xkb/symbols/sun_vndr/se
/etc/X11/xkb/symbols/sun_vndr/solaris
/etc/X11/xkb/symbols/sun_vndr/sw
/etc/X11/xkb/symbols/sun_vndr/tr
/etc/X11/xkb/symbols/sun_vndr/tuv
/etc/X11/xkb/symbols/sun_vndr/tw
/etc/X11/xkb/symbols/sun_vndr/us
/etc/X11/xkb/symbols/sun_vndr/usb
/etc/X11/xkb/symbols/xfree68_vndr
/etc/X11/xkb/symbols/xfree68_vndr/amiga
/etc/X11/xkb/symbols/xfree68_vndr/ataritt
/etc/X11/xkb/symbols/ad
/etc/X11/xkb/symbols/af
/etc/X11/xkb/symbols/al
/etc/X11/xkb/symbols/altwin
/etc/X11/xkb/symbols/am
/etc/X11/xkb/symbols/ara
/etc/X11/xkb/symbols/az
/etc/X11/xkb/symbols/ba
/etc/X11/xkb/symbols/bd
/etc/X11/xkb/symbols/be
/etc/X11/xkb/symbols/bg
/etc/X11/xkb/symbols/br
/etc/X11/xkb/symbols/bt
/etc/X11/xkb/symbols/by
/etc/X11/xkb/symbols/ca
/etc/X11/xkb/symbols/capslock
/etc/X11/xkb/symbols/ch
/etc/X11/xkb/symbols/compose
/etc/X11/xkb/symbols/cs
/etc/X11/xkb/symbols/ctrl
/etc/X11/xkb/symbols/cz
/etc/X11/xkb/symbols/de
/etc/X11/xkb/symbols/dk
/etc/X11/xkb/symbols/ee
/etc/X11/xkb/symbols/epo
/etc/X11/xkb/symbols/es
/etc/X11/xkb/symbols/eurosign
/etc/X11/xkb/symbols/fi
/etc/X11/xkb/symbols/fo
/etc/X11/xkb/symbols/fr
/etc/X11/xkb/symbols/gb
/etc/X11/xkb/symbols/ge
/etc/X11/xkb/symbols/gh
/etc/X11/xkb/symbols/gr
/etc/X11/xkb/symbols/group
/etc/X11/xkb/symbols/hr
/etc/X11/xkb/symbols/hu
/etc/X11/xkb/symbols/ie
/etc/X11/xkb/symbols/il
/etc/X11/xkb/symbols/in
/etc/X11/xkb/symbols/inet
/etc/X11/xkb/symbols/ir
/etc/X11/xkb/symbols/is
/etc/X11/xkb/symbols/it
/etc/X11/xkb/symbols/jp
/etc/X11/xkb/symbols/keypad
/etc/X11/xkb/symbols/kg
/etc/X11/xkb/symbols/kh
/etc/X11/xkb/symbols/kr
/etc/X11/xkb/symbols/kz
/etc/X11/xkb/symbols/la
/etc/X11/xkb/symbols/latam
/etc/X11/xkb/symbols/latin
/etc/X11/xkb/symbols/level3
/etc/X11/xkb/symbols/level5
/etc/X11/xkb/symbols/lk
/etc/X11/xkb/symbols/lt
/etc/X11/xkb/symbols/lv
/etc/X11/xkb/symbols/mao
/etc/X11/xkb/symbols/mk
/etc/X11/xkb/symbols/mm
/etc/X11/xkb/symbols/mn
/etc/X11/xkb/symbols/mt
/etc/X11/xkb/symbols/mv
/etc/X11/xkb/symbols/nl
/etc/X11/xkb/symbols/no
/etc/X11/xkb/symbols/pc
/etc/X11/xkb/symbols/pk
/etc/X11/xkb/symbols/pl
/etc/X11/xkb/symbols/pt
/etc/X11/xkb/symbols/ro
/etc/X11/xkb/symbols/ru
/etc/X11/xkb/symbols/se
/etc/X11/xkb/symbols/si
/etc/X11/xkb/symbols/sk
/etc/X11/xkb/symbols/srvr_ctrl
/etc/X11/xkb/symbols/sy
/etc/X11/xkb/symbols/th
/etc/X11/xkb/symbols/tj
/etc/X11/xkb/symbols/tr
/etc/X11/xkb/symbols/ua
/etc/X11/xkb/symbols/us
/etc/X11/xkb/symbols/uz
/etc/X11/xkb/symbols/vn
/etc/X11/xkb/symbols/za
/etc/X11/xkb/types
/etc/X11/xkb/types/README
/etc/X11/xkb/types/basic
/etc/X11/xkb/types/cancel
/etc/X11/xkb/types/caps
/etc/X11/xkb/types/complete
/etc/X11/xkb/types/default
/etc/X11/xkb/types/extra
/etc/X11/xkb/types/iso9995
/etc/X11/xkb/types/level5
/etc/X11/xkb/types/mousekeys
/etc/X11/xkb/types/numpad
/etc/X11/xkb/types/pc
/etc/X11/xkb/compat.dir
/etc/X11/xkb/geometry.dir
/etc/X11/xkb/keycodes.dir
/etc/X11/xkb/keymap.dir
/etc/X11/xkb/semantics.dir
/etc/X11/xkb/symbols.dir
/etc/X11/xkb/types.dir
/etc/X11/xkb/xkbcomp
/usr/X11R6/lib/X11/xkb
/usr/bin/setxkbmap
/usr/bin/xkbbell
/usr/bin/xkbcomp
/usr/bin/xkbevd
/usr/bin/xkbprint
/usr/bin/xkbvleds
/usr/bin/xkbwatch
/usr/lib/X11/xkb
/usr/lib/python2.4/site-packages/LanguageSelector/xkb.py
/usr/lib/python2.4/site-packages/LanguageSelector/xkb.pyc
/usr/lib/python2.4/site-packages/LanguageSelector/xkb.pyo
/usr/lib/libxkbfile.so.1
/usr/lib/libxkbfile.so.1.0.0
/usr/share/doc/libxkbfile1
/usr/share/doc/libxkbfile1/changelog.Debian.gz
/usr/share/doc/libxkbfile1/copyright
/usr/share/doc/xkbutils
/usr/share/doc/xkbutils/changelog.Debian.gz
/usr/share/doc/xkbutils/copyright
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas
/usr/share/icons/Tangerine/16x16/devices/kxkb.png
/usr/share/icons/Tangerine/22x22/devices/kxkb.png
/usr/share/icons/Tangerine/24x24/devices/kxkb.png
/usr/share/icons/Tangerine/scalable/devices/kxkb.svg
/usr/share/icons/Tango/16x16/devices/kxkb.png
/usr/share/icons/Tango/22x22/devices/kxkb.png
/usr/share/icons/Tango/24x24/devices/kxkb.png
/usr/share/icons/Tango/scalable/devices/kxkb.svg
/usr/share/locale-langpack/en_AU/LC_MESSAGES/xfce4-xkb-plugin.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/xfce4-xkb-plugin.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/kxkb.mo
/usr/share/man/man1/setxkbmap.1x.gz
/usr/share/man/man1/xkbcomp.1x.gz
/usr/share/man/man1/xkbevd.1x.gz
/usr/share/man/man1/xkbprint.1x.gz
/usr/share/vim/vim70/syntax/xkb.vim

```

Any suggestions. I've searched everything but I'm unable to find any solution :|

---

### Post by Theimon on 2006-12-28
Oh and maybe usefull as well.....after the first reboot it gave me a warning dialog where I could choose between usgin the Gnome settings or the X settings. I'm not able to reproduce the error dialog.

---

### Post by Theimon on 2006-12-28
I somehow managed to reproduce the Information dialog. I'm using Gnome settings now, so keyspeed and delay is fixed.

One little thing do: In the Keyboard Shortcuts I always had <Alt>+F3 to run a terminal. But no matter what key combination I try, none will open up a terminal.

Any suggestions on how to get that fixed?

---


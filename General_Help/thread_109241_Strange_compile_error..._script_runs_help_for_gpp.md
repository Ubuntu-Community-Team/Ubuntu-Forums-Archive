---
title: "Strange compile error... script runs help for gpp?"
date: 2005-12-28
forum: General Help
---

### Post by quincunx on 2005-12-28
I'm attempting to compile Mesa to make use of my 3D card.  Last night I thought I finally had it all figured out, but after running "./configure" and "make linux-glide" for Mesa 3.5 I eventually got the following output

```
gcc -shared  accum.lo api_arrayelt.lo api_loopback.lo api_noop.lo api_validate.lo attrib.lo blend.lo buffers.lo clip.lo colortab.lo config.lo context.lo convolve.lo debug.lo depth.lo dispatch.lo dlist.lo drawpix.lo enable.lo enums.lo eval.lo extensions.lo feedback.lo fog.lo get.lo glapi.lo glthread.lo hash.lo highpc.lo hint.lo histogram.lo image.lo imports.lo light.lo lines.lo lowpc.lo matrix.lo mem.lo mmath.lo pixel.lo points.lo polygon.lo rastpos.lo state.lo stencil.lo texformat.lo teximage.lo texobj.lo texstate.lo texstore.lo texutil.lo varray.lo vtxfmt.lo -Wl,--whole-archive math/.libs/libMesaMath.al swrast/.libs/libMesaSwrast.al swrast_setup/.libs/libMesaSwrast_setup.al tnl/.libs/libMesaTnl.al array_cache/.libs/libMesaAC.al X86/.libs/libMesaX86.al FX/.libs/libMesaFX.al FX/X86/.libs/libMesaFX_X86.a -Wl,--no-whole-archive  -Wl,--rpath -Wl,/home/me/Mesa-3.5/src/OSmesa/.libs -Wl,--rpath -Wl,/usr/local/lib  math/.libs/libMesaMath.al swrast/.libs/libMesaSwrast.al swrast_setup/.libs/libMesaSwrast_setup.al tnl/.libs/libMesaTnl.al array_cache/.libs/libMesaAC.al X86/.libs/libMesaX86.al FX/.libs/libMesaFX.al -lglide2x FX/X86/.libs/libMesaFX_X86.a OSmesa/.libs/libMesaOS.so -lpthread           -Wl,-soname -Wl,libGL.so.1 -o .libs/libGL.so.1.2.350
(cd .libs && rm -f libGL.so.1 && ln -s libGL.so.1.2.350 libGL.so.1)
(cd .libs && rm -f libGL.so && ln -s libGL.so.1.2.350 libGL.so)
creating libGL.la
(cd .libs && rm -f libGL.la && ln -s ../libGL.la libGL.la)
make[3]: Leaving directory `/home/me/Mesa-3.5/src'
make[2]: Leaving directory `/home/me/Mesa-3.5/src'
Making all in si-glu
make[2]: Entering directory `/home/me/Mesa-3.5/si-glu'
Making all in include
make[3]: Entering directory `/home/me/Mesa-3.5/si-glu/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/me/Mesa-3.5/si-glu/include'
Making all in libnurbs
make[3]: Entering directory `/home/me/Mesa-3.5/si-glu/libnurbs'
Making all in interface
make[4]: Entering directory `/home/me/Mesa-3.5/si-glu/libnurbs/interface'
/bin/sh ../../../libtool --mode=compile gpp -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../include -I../../../include -I../internals -I../nurbtess  -I./src/X86  -DLIBRARYBUILD -c bezierEval.cc
gpp -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../include -I../../../include -I../internals -I../nurbtess -I./src/X86 -DLIBRARYBUILD -Wp,-MD,.deps/bezierEval.pp -c bezierEval.cc  -fPIC -DPIC -o bezierEval.o
Usage : gpp [-{o|O} outfile] [-I/include/path] [-Dname=val ...] [-z] [-x] [-m]
            [-n] [-C | -T | -H | -X | -P | -U ... [-M ...]] [+c<n> str1 str2]
            [+s<n> str1 str2 c] [long options] [infile]

      default:    #define x y           macro(arg,...)
 -C : maximum cpp compatibility (includes -n, +c, +s, ...)
 -T : TeX-like    \define{x}{y}         \macro{arg}{...}
 -H : HTML-like   <#define x|y>         <#macro arg|...>
 -X : XHTML-like  <#define x|y/>        <#macro arg|.../>
 -P : prolog compatible cpp-like mode
 -U : user-defined syntax (specified in 9 following args; see manual)
 -M : user-defined syntax for meta-macros (specified in 7 following args)

 -o : output to outfile
 -O : output to outfile and stdout
 -z : line terminator is CR-LF (MS-DOS style)
 -x : enable #exec built-in macro
 -m : enable automatic mode switching upon including .h/.c files
 -n : send LF characters serving as macro terminators to output
 +c : use next 2 args as comment start and comment end sequences
 +s : use next 3 args as string start, end and quote character

 Long options:
 --include file : process file before infile
 --nostdinc : don't search standard directories for files to include
 --nocurinc : don't search the current directory for files to include
 --curdirinclast : search the current directory last
 --warninglevel n : set warning level
 --includemarker formatstring : keep track of #include directives in output

 --version : display version information and exit
 -h, --help : display this message and exit

make[4]: *** [bezierEval.lo] Error 1
make[4]: Leaving directory `/home/me/Mesa-3.5/si-glu/libnurbs/interface'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/me/Mesa-3.5/si-glu/libnurbs'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/me/Mesa-3.5/si-glu'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/Mesa-3.5'
make: *** [all-recursive-am] Error 2
```

It's difficult for me to tell what the line is doing that caused the help to display, am I missing something that I need to get via Synaptic?  Is the code for making this program just messed up?  Is it time for me to give up and install XP?  Help!

---

### Post by shin on 2005-12-28
For sure it is not the reason to go back to xp.
Yet error is erm.. interesting. It doesn't look like some packets missing, there is a problem with this gpp thing syntax
"-I. -I." this parameter is strange to me. Looks like some include dirs were not parsed correctly.

Check readme or something - maybe there are some parameters of ./configure that you omitted?
Oh and check if there were any kind of errors during ./configure.

---

### Post by quincunx on 2005-12-29
[QUOTE=shin]For sure it is not the reason to go back to xp.
Yet error is erm.. interesting. It doesn't look like some packets missing, there is a problem with this gpp thing syntax
"-I. -I." this parameter is strange to me. Looks like some include dirs were not parsed correctly.

Check readme or something - maybe there are some parameters of ./configure that you omitted?
Oh and check if there were any kind of errors during ./configure.[/QUOTE]

I looked through the readme's again, and read a few that I didn't think applied (and they didn't).  I did add some parameters to the ./configure command, but I was mostly ensuring default values.  The configure ran fine again, but after typing "make' I got the same error as above.

The only suspicion I have is that the Glide files that are supposed to be in /usr/local/glide were ones that I copied to that location.  Synaptic put them in /usr/lib/glide so I just made a new directory structure identical to the one in /usr/lib and copied the files.  Are there references to the locations of those files somewhere in my system that need to be changed?  Or is it just important that the files are in the expected directory?

Thanks again!

Quincunx

---

### Post by shin on 2005-12-29
They have to be in expected directory. Yet you can always create a symlink for them in whatever directory you want. E.g. if you want some file to exist in /usr/local/glide and /usr/lib you can just go to /usr/local/glide and there
sudo ln -s /usr/lib/some_file

you can do the same with directories. It's a better kind of shortcuts in windows. 

Sorry if I just explained something you already know. ;)

Anyway, this doesn't seem to be a problem now. I just checked mesa webpage - why are you using such an old Mesa? Latest stable is 6.4.1 (instructions [http://www.mesa3d.org/install.html)](http://www.mesa3d.org/install.html)), but the one with ubuntu should do the thing. Make sure you got libgl1-mesa and libgl1-mesa-dri installed.

Set your device in xorg.conf to some driver of your card (if you haven't done this already). Make sure that there is a Load "dri" line (in modules section), and that you got somewhere in xorg.conf:

Section "DRI"
    Mode       0660
EndSection

Restart X. If still
glxinfo | grep direct
shows direct rendering: off - get some dri drivers for your card from dri.sf.net

---

### Post by quincunx on 2005-12-29
[QUOTE=shin]<snip>...
Anyway, this doesn't seem to be a problem now. I just checked mesa webpage - why are you using such an old Mesa? Latest stable is 6.4.1 (instructions [http://www.mesa3d.org/install.html)](http://www.mesa3d.org/install.html)), but the one with ubuntu should do the thing. Make sure you got libgl1-mesa and libgl1-mesa-dri installed.

Set your device in xorg.conf to some driver of your card (if you haven't done this already). Make sure that there is a Load "dri" line (in modules section), and that you got somewhere in xorg.conf:

Section "DRI"
    Mode       0660
EndSection

Restart X. If still
glxinfo | grep direct
shows direct rendering: off - get some dri drivers for your card from dri.sf.net[/QUOTE]

I'm using an older version of Mesa for a couple of reasons.  First, the webpages I was reading (most written in 1998 and 1999) referred to using Mesa 3.x.  Second, the current version of Mesa only mentions supporting Voodoo3 and nothing earlier.

My xorg.conf has everything you mentioned except I have:

```
Section "DRI"
    Mode       0666
EndSection
```

Should I just change the "6" to a "0", save the file and ctrl-alt-backspace?

I just looked at dri.sf.net's troubleshooting section.  The first thing it says to check for is "dmesg | grep drm" and mine returns nothing.  I passed the following tests on the page though.  It says to compile agpgart into the kernel or load it as a module.  I couldn't find anything relative in Synaptic searching for "agpgart" or "agp".  However, the Voodoo2 card was made prior to AGP anyway.

---

### Post by shin on 2005-12-29
I did some google thing. As far as I know - agpgart is not needed for Voodoo2 so it wont show up in lsmod.

For Voodoo2 you should use "glide" driver in device section of xorg.conf
Check /var/log/Xorg.0.log and dmesg if there are any errors according to it or does it successfuly load.

If still no joy in troy - download glide source and according to [http://www.mesa3d.org/README.3DFX](http://www.mesa3d.org/README.3DFX) you should be able to compile newer mesa with glide support (which is disabled by default) when running before compilation:

./configure --with-glide=Dir_to_your_glide_libs

---

### Post by quincunx on 2005-12-29
[QUOTE=shin]I did some google thing. As far as I know - agpgart is not needed for Voodoo2 so it wont show up in lsmod.

For Voodoo2 you should use "glide" driver in device section of xorg.conf
Check /var/log/Xorg.0.log and dmesg if there are any errors according to it or does it successfuly load.

If still no joy in troy - download glide source and according to [http://www.mesa3d.org/README.3DFX](http://www.mesa3d.org/README.3DFX) you should be able to compile newer mesa with glide support (which is disabled by default) when running before compilation:

./configure --with-glide=Dir_to_your_glide_libs[/QUOTE]

I'm still not sure if I can edit the xorg.conf; seems like I remember special instruction for making changes to it.  Or is it just a file?  Here's what mine looks like:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"ViewSonic"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"ViewSonic"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

As you can see the "Device" section is i810.  Can I just edit this using "sudo gedit"?  Would I still need to change the "Mode 0666" to "Mode 0660"?

I checked out my Xorg.0.log and found this!

...
```

II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 24
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
```
...

I know the 3Dfx card has to be in 16bpp, aparently, so does the i810.  Does this look like where things are going wrong?

I ran dmesg, but couldn't make sense of it.  I could tell that there were no errors though.  I did "man dmesg" to see if anything would make more sense, but the man page made less sense than the dmesg output, hahaha

Thanks so much for your help!  It feels like I/we are making progress :)  Even though I still don't understand everything you're having me check, I don't feel near as "lost" as I did a few days ago ;)

---

### Post by shin on 2006-01-01
Hi again. Now in 2006 ;)

xorg.conf is a normal file. You can just edit it. To try new configuration (after editing) restart your X.org by pressing ctrl+alt+backspace. If there are errors - they will show up in X.org.0.log.

I dunno about xorg.conf with Voodoo but before experimenting with Driver in it try just changing:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Monitor         "ViewSonic"
        DefaultDepth    24

```

To 

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Monitor         "ViewSonic"
        DefaultDepth    16

```

This way your Xorg should use 16bpp, thus maybe dri will start.

---


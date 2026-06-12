---
title: "qvwm x windows manager not show icons in Ubuntu 8.04.4"
date: 2010-06-02
forum: Desktop Environments
---

### Post by wachin on 2010-06-02
Hello, help me please. I have Ubuntu 8.04.4 installed on a Pentium III 750 Mhz, 470 MB RAM, I have tried several x window managers: fvwm, fvwm-crystal, icewm, windows maker, lxde, and jwm, and three others believe, but the faster than all is "qvwm" is very very fast (with gkrellm I see the results. The programs Firefox, OpenOffice, charge with agility) but qvwm do not show any icons on the panel, no one, is pure single text, also the whole desktop is pure text, and the menu, no icon appears in any application. And I worry that they took him out of the repositories of ubuntu in the version 9.10 and 10.04 qvwm is died (tried your search in: "qvwm site:packages.ubuntu.com"). 
I installed from the repositories debs in Ubuntu 8.04.4.

For the moment I found a solution I have installed fspanel that if displays icons (not fbpanel but not working here), and placed the qvwm panel on the left (not down) and with autohide, to reveal fspanel bottom, but yet is not the same.
 If you put in google "qvwm" appears beautiful images.

see this:

[http://www.csg.is.titech.ac.jp/~kourai/qvwm/gallery-en.html](http://www.csg.is.titech.ac.jp/~kourai/qvwm/gallery-en.html)

[http://www.csg.is.titech.ac.jp/~kourai/qvwm/screenshots/taskbar_s.gif](http://www.csg.is.titech.ac.jp/~kourai/qvwm/screenshots/taskbar_s.gif)

[http://www.csg.is.titech.ac.jp/~kourai/qvwm/screenshots/screen2.jpg](http://www.csg.is.titech.ac.jp/~kourai/qvwm/screenshots/screen2.jpg)

I have no wallpaper, no icons, do not know how to put it. But I tried the following.

When installing qvwm done that:

Copy, paste and rename the file:

/Etc/X11/qvwm/system.qvwmrc

to:

HOME/ .qvwmrc

But nothing, no icon appears.

Then in that file I changed some things, this is the original:

uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

[Variables]
LocaleName		= ""		; locale name used in this file
ImagePath		= "/usr/share/qvwm/images"
SoundPath		= "/usr/share/qvwm/sounds"
RestartOnFailure	= True		; restart on seg fault/bus error
UseDebugger		= False
HourGlassTime		= 1000
ImageAnimation		= True

bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb


And I changed the direction of the images to see if it displays icons:


uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

[Variables]
LocaleName		= "WACHOFORCE"		; locale name used in this file
ImagePath		= "/usr/share/pixmaps/"  
SoundPath		= "/usr/share/qvwm/sounds"
RestartOnFailure	= True		; restart on seg fault/bus error
UseDebugger		= False
HourGlassTime		= 1000
ImageAnimation		= True

nnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn

But nothing at all, does not display icons.

and more, just below in the same file look this:

ttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttt

[StartMenu]
include		/etc/X11/qvwm/menu.hook
"\&Setting"	"debian-swirl-32x32.xpm"

uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

The file "debian-swirl-32x32.xpm" default is not installed in the directory: "/usr/share/qvwm/images". But there is installed: "debian-swirl-16x16.xpm."

Finally, if you still looking in "/usr/share/qvwm/images" you will find several pictures of icons xpm, but are not shown in the panel qvwm.


I also looked at the debian page, there is to download some icons (xpm files are):

[http://patch-tracker.debian.org/package/qvwm/1:1.1.12-4](http://patch-tracker.debian.org/package/qvwm/1:1.1.12-4)

I have searched icons in the "File System" with "Gnome-search-tool" and are not installed in me Ubuntu 8.04.4. I downloaded and copied two of these files in:

[http://patch-tracker.debian.org/patch/misc/dl/qvwm/1:1.1.12-4/icons/calculator-32x32.xpm](http://patch-tracker.debian.org/patch/misc/dl/qvwm/1:1.1.12-4/icons/calculator-32x32.xpm)
[http://patch-tracker.debian.org/patch/misc/dl/qvwm/1:1.1.12-4/icons/debian-swirl-32x32.xpm](http://patch-tracker.debian.org/patch/misc/dl/qvwm/1:1.1.12-4/icons/debian-swirl-32x32.xpm)

/usr/share/qvwm/images/
/usr/share/pixmaps/

but anything not shown icons in qvwm.





Also I search all dependences of wvwm in:

[http://packages.debian.org/etch/qvwm](http://packages.debian.org/etch/qvwm)

seeing in the synaptic (ubuntu is debian like), a Found "libungif4g" is not installed, but I installed it, and nothing.





I also started looking in the file:

/Etc/X11/qvwm/menu.hook


There is the menu generated automation. And there is this:

lllllllllllllllllllllllllllllllllllllllllllllllll

"Editores"   ""
+
  "Gedit"  "/usr/share/pixmaps/gedit-icon.xpm" "/usr/bin/gedit"
  "LeafPad"  "/usr/share/pixmaps/leafpad.xpm" "/usr/bin/leafpad"
  "Nano"  "/usr/share/nano/nano-menu.xpm" "x-terminal-emulator  -T \"Nano\" -e sh -c \"/bin/nano\""
  "Xedit"  "" "xedit"
  "Xfw File Writer"  "/usr/share/pixmaps/xfw.xpm" "/usr/bin/xfilewriter"

iiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii

I notice that:

/Usr/share/pixmaps/

xpm there are many files, so they should appear in qvwm, nothing. incredible, what will?

Finally, I looked at:

[http://manpages.ubuntu.com/manpages/hardy/man1/qvwm.1x.html](http://manpages.ubuntu.com/manpages/hardy/man1/qvwm.1x.html)

interesting, look this: 


nnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn

NAME PATH
       You Can Use ~ for your home directory, ~ user's home directory for user,
       Following environment variables and to $.

            ex) include $ HOME / .qvwmrc.local
                IconPath = ~ / lib / qvwm / pixmaps

SUPPORTED IMAGE FORMATS
       Supports qvwm xpm format (extension. Xpm). If you use Imlib Also qvwm
       Imlib That Supports formats supports. Also, qvwm Supports animation
       qvwm for files (extension. ani). Because the animation files Contain
       Some images as it is, is an animation file if qvwm Supported Supports
       all formats of the images in the file.

uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

I add this IconPath to the file: ".qvwmrc"


[Variables]
LocaleName = "WACHOFORCE" Used in this locale file name
ImagePath = "/ usr / share / pixmaps /"
IconPath = "/ usr / share / pixmaps /"
SoundPath = "/ usr / share / qvwm / sounds"
RestartOnFailure = True; restart on seg fault / bus error
UseDebugger = False
HourGlassTime = 1000
ImageAnimation = True


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
but nothing. help me please, not to do.

Thanks for reading this, for all yours. God bless.

Att:

Washington Indacochea Delgado

---


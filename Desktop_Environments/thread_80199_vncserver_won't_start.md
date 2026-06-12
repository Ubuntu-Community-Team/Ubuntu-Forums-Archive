---
title: "vncserver won't start"
date: 2005-10-21
forum: Desktop Environments
---

### Post by Footer on 2005-10-21
I've spent almost the entire day trying to get vncserver running on my Ubuntu system with no luck.  The log file in the /home/user/.vnc directory is as follows:
[INDENT]
Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc


Fri Oct 21 15:34:56 2005
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from
 list!

Fatal server error:
could not open default font 'fixed'
xrdb: Connection refused
xrdb: Can't open display 'kubuntu:1'
xsetroot:  unable to open display 'kubuntu:1'
xterm Xt error: Can't open display: kubuntu:1
xsetroot:  unable to open display 'kubuntu:1'
xset:  unable to open display "kubuntu:1"
[/INDENT]
Does anyone know what all this means?  I've googled "could not open default font 'fixed'" as I suspect that's the main problem and tried some things I've found but nothing has worked so far.  I'm really stuck.  Has anyone gotten vncserver to work on Ubuntu?  If so, I'd be curious to know how.  I'd use a different remote solution but I'm trying to get to Ubuntu from a Windoze machine and vnc is one of the only games in town that works (sometimes anyway!).  I've successfully gotten vncserver to work on SuSE, Fedora and KnoppMyth.

Thanks in advance!

---

### Post by markpalinux on 2005-10-21
I just installed 5.10 tonight, I had gotten the same error, here is what I had done:


When I tried to launch tightvncserver I had gotten errors like yours,
in addition my errors included:

Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring


I edited the /etc/vnc.conf and added the following to the bottom of the file:
       $fontPath .= "/usr/share/X11/fonts/misc/,";
       $fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
       $fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
       $fontPath .= "/usr/share/X11/fonts/Type1/,";
       $fontPath .= "/usr/share/X11/fonts/Speedo/,";
       $fontPath .= "/usr/share/X11/fonts/75dpi/,";
       $fontPath .= "/usr/share/X11/fonts/100dpi/,";
       $fontPath .= "/usr/share/X11/fonts/freefont/,";
       $fontPath .= "/usr/share/X11/fonts/sharefont/";


hope this works for you.

---

### Post by Footer on 2005-10-22
[QUOTE=markpalinux]I just installed 5.10 tonight, I had gotten the same error, here is what I had done:


When I tried to launch tightvncserver I had gotten errors like yours,
in addition my errors included:

Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring


I edited the /etc/vnc.conf and added the following to the bottom of the file:
       $fontPath .= "/usr/share/X11/fonts/misc/,";
       $fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
       $fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
       $fontPath .= "/usr/share/X11/fonts/Type1/,";
       $fontPath .= "/usr/share/X11/fonts/Speedo/,";
       $fontPath .= "/usr/share/X11/fonts/75dpi/,";
       $fontPath .= "/usr/share/X11/fonts/100dpi/,";
       $fontPath .= "/usr/share/X11/fonts/freefont/,";
       $fontPath .= "/usr/share/X11/fonts/sharefont/";


hope this works for you.[/QUOTE]


VERY COOL!!!  I added those lines to my /etc/vnc.conf and VIOLA! it worked!!!  Thanks much!!!

Just one more problem though, I get the gray weave desktop.  Normally, I use  an xstartup file in ~/.vnc like this:
[INDENT]
~/.vnc$ more xstartup
#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
/usr/bin/startkde &
[/INDENT]
but that doesn't seem to be getting accessed.  Any further ideas???  Much further than I got yesterday though.  MANY THANKS!

:)

---

### Post by markpalinux on 2005-10-23
I added "gnome-session" as the last line of my xstartup file and got gnome started, a bit strage through it stops with the startup box at window manager. The full desktop is usable.

here is my xstartup
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
gnome-session &

---

### Post by seanmc42 on 2006-03-23
I have the same problem - but this technique didn't work for me.
One thing I noticed is that I don't have all those fonts
directories - I ONLY have the misc, 75dpi, 100dpi, and encoded directories...
I looked at xfonts-base in synaptic, but that doesn't seem to contain the missing directories. I have no idea where to get them.
I'm assuming the basic problem here is that the 'fixed' font is missing...

---

### Post by gnychis on 2007-12-15
solution for me, add this to vnc.conf:
$fontPath .= "/usr/share/fonts/X11/misc/,";

---


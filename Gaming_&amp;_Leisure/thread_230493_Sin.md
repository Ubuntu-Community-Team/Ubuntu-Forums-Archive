---
title: "Sin"
date: 2006-08-06
forum: Gaming &amp; Leisure
---

### Post by straxus on 2006-08-06
Last year I managed to get Sin running in Debian with the instructions found [here]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games").  I've been trying to get it to run in Dapper.  I've tried the ATI and FGLRX drivers with the same results.  This is what I get:


straxus@minerva:/opt/Sin$ LD_PRELOAD=/usr/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3 /opt/Sin/sin.exe
Added packfile ./base/pak0.sin (9421 files)
Added packfile ./base/pak1.sin (289 files)
Added packfile ./base/pak2.sin (2978 files)
Added packfile ./base/pak3.sin (172 files)
execing default.cfg
couldn't exec /home/straxus/.hyperion/Sin/players/blade/config.cfg
cddir is write protected.
NET Initialized
Console initialized.
------- Loading ./ref_soft.so -------
setting mode 3: 640 480 FS
Shutting down SW imp
Using DGA DirectMouse
1976k surface cache
ref_soft version: SOFT 0.01
------------------------------------

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
CD Audio Initialized
Mouse support enabled
execing autoexec.cfg
------- Server Initialization -------
-------------------------------------
====== Sin Initialized ======

loopback: client_connect
Shutting down SW imp
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x2a00001
  Serial number of failed request:  139
  Current serial number in output stream:  144

---

### Post by straxus on 2006-08-06
I managed to get Sin to load by changing 'set vid_fullscreen' in default.cfg from 1 to 0, and running in window mode.  Running in fullscreen would be nice, but it's not a showstopper for me.

Oddly, the audio for the game comes from my onboard device rather than my SBLive! card.  I would prefer it to use the SBLive! like everything else, but this is again, not a showstopper.

However, while the game works fine in software mode, it pukes when I enable OpenGL.  This really has to change before I can play.  I have the FGLRX driver loaded and working.  fglrxinfo returns:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18)


Here is the exit error when I enable OpenGL:
------- Loading ./ref_gl.so -------
ref_gl version: GL 0.01
Couldn't load OpenGL library: libGL.so
ref_gl::R_Init() - could not load "opengl32"
Segmentation fault


Let me know if you have any advice for any of the above problems. :)

---

### Post by straxus on 2006-08-06
Okay.  I'm answering alot of my own questions here.  Hopefully someone else who needs these answers will find this one day.  I now have Sin running in a window with OpenGL working.  I'd still like fullscreen, and for the sound to come from my other device if anyone can help with that.

If anyone else needs to know how I got to this point, here's everything I did.

Run setup.sh from the Sin install CD with sudo.
For install path, I went with /opt/Sin
For binary directory, I chose /usr/local/bin
Check all the install options.
Download the 'loki_compat_libs' archive from: [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)
Extract these files.  I put them in /usr/lib/Loki_Compat

cd /usr/lib
sudo ln -s libSDL-1.2.so.0 libSDL-1.1.so.0
sudo ln -s libGL.so.1.2 libGL.so
sudo gedit /opt/Sin/base/default.cfg
(Find 'set vid_fullscreen' and change the 1 to a 0 - save and exit)

After all of this has been done, you can run Sin by opening the terminal and entering these commands:
cd /opt/Sin
LD_PRELOAD=/usr/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3 /opt/Sin/sin.exe

---

### Post by cchester on 2008-07-08
Hey I am trying to install Sin in Ubuntu 8.04 32bit and I get the following error:

setup.sh: 9: function: not found
x86

when i run sh setup.sh

What does this mean and how do I fix it.

Thanks for any help.

---


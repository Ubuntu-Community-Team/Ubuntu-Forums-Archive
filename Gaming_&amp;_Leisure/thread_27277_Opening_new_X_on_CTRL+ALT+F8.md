---
title: "Opening new X on CTRL+ALT+F8"
date: 2005-04-15
forum: Gaming &amp; Leisure
---

### Post by gnutux on 2005-04-15
Hey all,

 I just wanted to know how I can give access to normal users to open a new X window so I can play AASF on one window and keep KDE on another.

This is the error I get when I try xinit /usr/local/games/armyops/armyops -- :1
> 
X: user not authorized to run the X server, aborting.
xinit:  Server error.


Please help and reply!

gnutux

---

### Post by AndersAA on 2005-04-15
```

if ! xauth list | grep ':1' >/dev/null; then
    LINE=`xauth list | grep -o 'MIT-MAGIC-COOKIE.*' | head -n 1 | xargs echo add :1`
    LINE2=`xauth list | grep -o 'MIT-MAGIC-COOKIE.*' | head -n 1 | xargs echo add :2`
  xauth << EOF
${LINE}
${LINE2}
exit
EOF

```


I have this in a bash script (along with some other stuff)
put that in a file and write sh <filename> and it'll work

---

### Post by gnutux on 2005-04-15
After I paste that script and saved it, my kdesu command went missing! AHHH!

Please help!

gnutux

---

### Post by AndersAA on 2005-04-16
that script does absolutly nothing with kdesu..

---

### Post by Seth on 2005-05-01
[QUOTE=AndersAA]```

if ! xauth list | grep ':1' >/dev/null; then
    LINE=`xauth list | grep -o 'MIT-MAGIC-COOKIE.*' | head -n 1 | xargs echo add :1`
    LINE2=`xauth list | grep -o 'MIT-MAGIC-COOKIE.*' | head -n 1 | xargs echo add :2`
  xauth << EOF
${LINE}
${LINE2}
exit
EOF

```


I have this in a bash script (along with some other stuff)
put that in a file and write sh <filename> and it'll work[/QUOTE]
 Got past that, now I get: ```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux eos 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:27:02 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun May  1 01:59:00 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(EE) fglrx(0): No valid mode found for CRTC2 clone
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) fglrx(0): Failed to initialize UMM driver.
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

waiting for X server to shut down

```

I assume I need to set up another Screen in xorg.conf? How?

---

### Post by dafrabbit on 2005-05-02
[QUOTE=Seth]Got past that, now I get: ```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux eos 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:27:02 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun May  1 01:59:00 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(EE) fglrx(0): No valid mode found for CRTC2 clone
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) fglrx(0): Failed to initialize UMM driver.
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

waiting for X server to shut down

```

I assume I need to set up another Screen in xorg.conf? How?[/QUOTE]
 Hrmm....just fyi, if all you would like is to have two concurrent X sessions, you can simply use the command:

gdmflexiserver

Then switch between the two by ctrl-alt-f#. I have not tried this while running 3d games on one or both sessions however....

---

### Post by Seth on 2005-05-02
That would be great, except I use kdm :P

---

### Post by Seth on 2005-05-05
As a note, I'd really like this because X.org can't do RANDR and 3D simultaneously. This would allow me to run America's Army on a second screen at a lower resolution and still fill the whole screen.

---


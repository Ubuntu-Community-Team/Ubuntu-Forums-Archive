---
title: "GUI Problems..."
date: 2008-08-21
forum: Desktop Environments
---

### Post by Indigo6 on 2008-08-21
Hardware: Compaq HP nc6000 laptop

Hi, here's my problem.  I started with Kubuntu 8.04, upgraded to KDE 4.1 and loved it.  Then, I installed Gnome.  I also have KDE 3.5.9 -- At some point, I think after an update to the kernel, or some other, or maybe right after a Nessus scan... the computer locked up and I turned it off without shutting down properly (in KDE 4.1).  I'd done this before without a problem, but this time KDE4 wouldn't load again.  I have no problems loading Gnome or the older KDE.

I've been working on this for more than a week, and I've learned a lot, but I've tried everything I can think of... I am relatively new to linux, but not afraid of the command line.  I have moved ~/.kde4 out of the way, tried using GDM vs. KDM -- oh, and BTW, KDM-KDE4 crashes and drops me to a text login -- I've removed and reinstalled everything related to KDE4.  And still, it doesn't work.

The error log (when using KDM-KDE4) says 'received an unknown command -2 from greeter'

When trying to load KDE4 from KDM, the error that comes up is 'Call to lnusertemp failed (temporary directory full?)  Check your installation'

Also, /usr/lib/kde4/etc/kde4/kdm/kdmrc doesn't seem to exist, though I don't see how this could be causing the problem.

I have tried emptying /tmp, thinking maybe it was just a problem with KDM-KDE4, even tried re-creating my user account -- I've read through everything I could find on the web and I'm beginning to think it's a display problem.  There's one strange thing which points me to this:  When trying to load KDE4, when the screen changes (or refreshes), I can actually see the black shiny icon screen loading somehow 'beneath' the ugly bright blue kdm screen where the error comes up.

Could I be having this problem because it's trying to open a display that's already open?  And why wouldn't the other GUIs have this problem?  (I even tried Xfce but didn't like it... maybe I do have too many desktop interfaces, but next I'm thinking Enlightenment.)  I really like KDE 4.1 and had it completely configured.  There are a number of other problems I have yet to work out, but first things first.  Any ideas?  I'm in over my head on this and any help would be really appreciated.

---

### Post by Indigo6 on 2008-09-01
Ok, so KDE 4.1 still isn't working... and this has become such a long project.  I haven't received any replies, but I have made progress.

Since I posted, I have installed Enlightenment (which works beautifully) and removed everything related to KDE3 and KDE4.  I used 'apt-get remove --purge', even, and kde4*, etc... then, I installed a fresh kubuntu-kde4-desktop -- same problem, kdm-kde4 crashes and kde4 (I suspect) probably still won't load even from gdm.

So here's the progress:  I've narrowed down the problem, though I'm still in over my head with no idea how to fix this porblem.  The following few lines from the log files are what I've found.

Kernel log --
Sep  1 15:05:32 Laptop kernel: [  157.183453] mtrr: no MTRR for 98000000,2000000 found

Syslog --
Sep  1 15:05:32 Laptop kdm: :0[5580]: Received unknown or unexpected command -2 from greeter
Sep  1 15:05:32 Laptop kdm: :0[5580]: Abnormal termination of greeter for display :0, code 127, signal 0

So, this does seem to be a display problem... but not necessarily related to X11.  I don't really understand what MTRR is, or how to fix it, but from what I've read in other posts I suspect it's a problem related to this laptop's video driver.

Is there a different driver I can use?  Or maybe an argument I can add to grub?  How might I disable MTRR, and is that a good idea?  Again, any help would be greatly appreciated.  Gnome and Enlightenment work just fine, but I liked KDE 4.1 much better.

---

### Post by Indigo6 on 2008-09-04
Ok, I still can't get kdm-kde4 or KDE 4.1 to run -- and I haven't a clue what to do next.  The last batch of updates didn't help, still crashes.  I've been looking through my log files and, while I honestly don't want to reply to my own post (without a solution), I thought I'd list the most interesting things I found.  Although, I'm not sure how much of this is related to the reason why KDE won't work.  I really don't want to re-install from scratch.  Please, anyone, even if you can't give me a solution, can you point me in the right direction?  I still think this is a video problem, but I'm pretty new at this (and learning a lot)... Help???



debug

Boot video device is 0000:01:00.0


kdm.log

/usr/lib/kde4/lib/kde4/libexec/kdm_greet: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv


syslog

Sep  4 10:31:08 Laptop kdm: :0[5869]: Received unknown or unexpected command -2 from greeter
Sep  4 10:31:08 Laptop kdm: :0[5869]: Abnormal termination of greeter for display :0, code 127, signal 0


kern.log

Sep  4 10:31:13 Laptop kernel: [  139.848648] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep  4 10:31:13 Laptop kernel: [  139.848907] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Sep  4 10:31:13 Laptop kernel: [  139.849103] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Sep  4 10:31:14 Laptop kernel: [  141.141502] [drm] Setting GART location based on new memory map
Sep  4 10:31:14 Laptop kernel: [  141.141515] [drm] Loading R300 Microcode
Sep  4 10:31:14 Laptop kernel: [  141.141571] [drm] writeback test succeeded in 2 usecs
Sep  4 10:31:09 Laptop kernel: [  146.178197] mtrr: no MTRR for 98000000,2000000 found


Xorg.0.log

(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9bff9800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0

...

(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x9bff9800 is: 0x9bff9800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xb07fb000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9bff9800 0x9bff9800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xb07fb000

...

(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

---

### Post by Indigo6 on 2008-09-04
...I forgot to mention one thing.  I have only one monitor (I'm on a laptop), but for some reason there are two AGP V2 devices.  Also, I think I'm using the flgrx ATI driver, with frame buffering.  Everything but KDE works.  For anyone who goves this some thought, thank you in advance.

---

### Post by Indigo6 on 2008-09-07
I finally found a solution, thought I'd post it for anyone who comes across this thread.  It turns out that there's a conflict with the qt4 libraries that come with the Nessus Client.

See these links for specifics:
[http://kubuntuforums.net/forums/index.php?topic=3090266.0](http://kubuntuforums.net/forums/index.php?topic=3090266.0)
[http://article.gmane.org/gmane.linux.redhat.fedora.general/299265](http://article.gmane.org/gmane.linux.redhat.fedora.general/299265)

One can either uninstall Nessus, or comment out the line in /etc/ld.so.conf then points to the directory /opt/nessus/lib/ -- I don't know if I can just remove the Qt files, leaving the Nessus libraries, or if Nessus will even run without them... but I hardly use the program, so I'm just removing it and KDE 4.1 is back... finally.

---


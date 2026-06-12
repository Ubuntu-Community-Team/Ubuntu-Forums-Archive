---
title: "No GDM launch at boot &amp; No Sound"
date: 2009-03-26
forum: General Help
---

### Post by mithbuntu on 2009-03-26
**[COLOR="Red"]SOLVED BOTH![/COLOR]**  Fixed 2. by running through the sound troubleshooting thread for the 4th time.  Fourth time's a charm, eh?  In the end, the fix was that I was finally able to retrieve the missing modules that were erroring out previously.

1. Solved below.

2. I have no sound. I've tried several steps to get my sound back, but none have worked.  Have removed many packages, and I am currently at a bare bones state.  

System>Admin>Sound>>
Attempting [test] button gives error:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: could not get/set setting from/on resource

```

Following sound troubleshooting guide, but here were the results:
```

drew@mithbuntu:~/Desktop/make$ aplay -l
aplay: device_list:215: no soundcards found...

drew@mithbuntu:~/Desktop/make$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko

drew@mithbuntu:~/Desktop/make$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-11-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-11-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

****
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
 Subsystem: nVidia Corporation Device c55e
 Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
 Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel modules: snd-hda-intel

```



---SOLVED PORTION (ignore)---
X. Booting into ubuntu places me at the terminal login.  I must type startx at the terminal to load ubuntu. 

If I:
sudo startx >> No user configuration. Logged in as root instead of user.
startx      >> Extensive problems abound.  Linked to ubuntu not running most commands with root access. Synaptic et al "Failed to run ... as root".  

Looks like it is trying to load xorg.conf.failsafe instead of my real config ??
```

(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(EE) No devices detected.
```

Configure X Server (Login Admin Pane) >> ```
 /usr/X11R6/bin/X -br -audit 0 
```

**[COLOR="Red"]SOLVED![/COLOR]**
Need solution to: Restore GDM to typical post-boot autoload condition.

]I fixed my GDM problem by changing the default startup X type from "Xgl" to "Standard", but I have a new peculiarity with firefox since the fix.

1.All navigation buttons, bookmarks, and browsing history are GONE. Also, when I switch tabs, the url doesn't change. Reinstalling firefox didn't seem to work.  Screenshot attached:

[IMG]http://triton.imageshack.us/Himg237/scaled.php?server=237&filename=firefoxissues.png&xsize=640&ysize=480[/IMG]

**[COLOR="Red"]SOLVED![/COLOR]** 
To fix this problem:
```

sudo rm -rf ~/.mozilla/firefox

```

---

### Post by mithbuntu on 2009-03-26
Bump.  Just need help with sound issues now.

---


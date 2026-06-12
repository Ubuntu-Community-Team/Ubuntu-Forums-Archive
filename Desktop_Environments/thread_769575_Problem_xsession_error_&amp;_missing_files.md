---
title: "Problem xsession error &amp; missing files"
date: 2008-04-26
forum: Desktop Environments
---

### Post by evilc on 2008-04-26
I have finally installed 8.04 after 3 installations (glitches/no video etc), everything ran perfect via live-cd. Now I have I think almost everything running (how I like it), but I noticed 2 problems/queries.

1/ Installed glipper from Synaptic, unable to find it anywhere, should be in usr/bin? Synaptic thinks it's installed.

2/ The dreaded xsession-error has shown up again, this is what it say's after startup and of course nautilus open.

```
 /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/clive:/tmp/.ICE-unix/5382
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Initializing nautilus-share extension
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
seahorse nautilus module initialized
11

** (nautilus:5469): WARNING **: Unable to add monitor: Not supported
I/O warning : failed to load external entity "/home/clive/.compiz/session/default0"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing. 
```Any suggestions appreciated.

---

### Post by evilc on 2008-04-27
bump

No suggestions?

---

### Post by mali2297 on 2008-04-27
You can see the file list for the package glipper here:
[http://packages.ubuntu.com/hardy/i386/glipper/filelist](http://packages.ubuntu.com/hardy/i386/glipper/filelist)

There is a file /usr/lib/glipper/glipper, might it be what you're looking for?

---

### Post by evilc on 2008-04-27
> **mali2297 said:**
> You can see the file list for the package glipper here:
[http://packages.ubuntu.com/hardy/i386/glipper/filelist](http://packages.ubuntu.com/hardy/i386/glipper/filelist)

There is a file /usr/lib/glipper/glipper, might it be what you're looking for?

That's the one thanks, used to be in user/bin. The other strange thing was when I searched for it nothing was found, not to worry only the error message to clear up now.:)

Thanks,

---


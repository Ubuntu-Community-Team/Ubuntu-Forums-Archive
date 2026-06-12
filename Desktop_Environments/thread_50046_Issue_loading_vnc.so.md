---
title: "Issue loading vnc.so"
date: 2005-07-18
forum: Desktop Environments
---

### Post by vipergts450 on 2005-07-18
Hello all,

I would like to first say that I've been lurking on these forums for a long time and wish to say that the community here is very friendly and most helpful. You're all great! :)

Now, unfortunately I've been having a lot of issues trying to get the vnc.so module provided by the vnc4server package to load in xorg. I am running Hoary on a Pentium III 1GHz box with 512MB RAM and an nVidia GeForce2 GTS 64MB video card.

I have added the appropriate like to my xorg.conf, of course, but whenever X loads, the logfile shows the following:
```

(II) LoadModule: "vnc"
(WW) Warning, couldn't open module vnc
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (module does not exist, 0)

```

I then tried to change the Load line to something more direct, i.e.
```

Load "/usr/X11R6/lib/modules/extensions/vnc.so"

```

This did indeed force X to see the module, but a new error sprung up:
```

(II) LoadModule: "/usr/X11R6/lib/modules/extensions/vnc.so" (vnc.so)
(WW) LoadModule: given non-canonical module name "/usr/X11R6/lib/modules/extensi
ons/vnc.so"
(II) Loading /usr/X11R6/lib/modules/extensions/vnc.so
(EE) LoadModule: Module /usr/X11R6/lib/modules/extensions/vnc.so does not have a
 vnc.soModuleData data object.
(II) UnloadModule: "vnc.so"
(II) Unloading /usr/X11R6/lib/modules/extensions/vnc.so
(EE) Failed to load module "/usr/X11R6/lib/modules/extensions/vnc.so" (invalid m
odule, 0)

```

I'm pretty much out of ideas on how to proceed from this point. I've tried alternatives to get DISPLAY :0 connected via VNC:
[list=1]
[*]vino - works, but only if a user is logged into the system already, which is not what I want
[*]x11vnc - This package looked promising, but I found it to be very unstable. Specifically, I'd VNC to my Hoary box and I'd be presented with the GDM screen, as I want. As soon as I hit ENTER after entering the password, x11vnc would crash.
[*]x0rbserver - Ugh. Slow and doesn't load at GDM start
[/list]

I have a Fedora Core 3 box which runs Xorg and vnc.so with no issues, allowing me direct access to the desktop when I need it. I really wish to do the same with Ubuntu, as I've found it to be a great distro thusfar. I installed it to teach a younger child to use a computer and I want to have vnc.so working so that I can administer it remotely (I know SSH is an option, and that's how I do 95% of my administration, but sometimes I just need that :0 desktop).

Sorry for the long winded first post and I hope you'll invite me into your wonderful community.

Many thanks in advance,
Mike

---

### Post by vipergts450 on 2005-07-19
Anyone? I've really been struggling with this.

---

### Post by vace117 on 2005-11-12
[QUOTE=vipergts450]Anyone? I've really been struggling with this.[/QUOTE]

If you rename vnc.so to libvnc.so, the module will be loaded properly.

---

### Post by legume on 2006-01-28
[QUOTE=vace117]If you rename vnc.so to libvnc.so, the module will be loaded properly.[/QUOTE]

Thank you! I had exactly the same problem, and this fixed it (though actually I made a symbolic link libvnc.so->vnc.so, in the hope that any future upgrades to vnc.so would work).

Laz

---

### Post by manuelrrojas on 2008-03-11
maybe do you want install X11vnc there are 2 options :P

x11vnc                          - VNC server which uses your current X11 ses
x2vnc                           - A dual-screen hack - link an MS-Windows an


i found more information abooyt x11vnc at this how to

[http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions#Method_2:__X_Server_.28system-started.29_method](http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions#Method_2:__X_Server_.28system-started.29_method)

---


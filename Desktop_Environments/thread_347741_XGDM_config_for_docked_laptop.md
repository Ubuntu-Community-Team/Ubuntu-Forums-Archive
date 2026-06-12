---
title: "X/GDM config for docked laptop"
date: 2007-01-27
forum: Desktop Environments
---

### Post by mfremont on 2007-01-27
I'm trying to get my lap.top running 6.10 to work with the external display I have attached to my docking station. When docked, I want output only on the external display. When undocked, I want output on the built in display.

The catch is that the external display is SGI 1600SW driven by a Number 9 Revolution IV installed in the dock. So the system has two sets of Device, Monitor, Screen, and ServerLayout sections in /etc/X11/xorg.conf, only one of which should be active.

I've left the Ubuntu-generated "Default Layout" unmodified and added a second custom server layout, "DockLayout". With this layout Ubuntu is able to successfully start X and runs GDM on the dock's SGI display, But when I boot undocked it still tries to start the i128 X server even though the Number 9 hardware isn't present. The result is that I'm greeted with an ugly screen notifying me that X failed to start.

The X server binary has a command line option to specify which ScreenLayout to use, but I don't see a way to specify this in the GDM startup scripts. If such an option existed I could attempt to detect the bridge hardware for the dock and pass the correct layout as a startup option for X/GDM.

Is the correct thing to start a second server using my DockLayout in the /etc/gdm/gdm-conf.custom file, knowing that only one of the two servers will actually start up successfully?

Or is there another, better way?

Thanks in advance for your help.

---

### Post by mfremont on 2007-02-10
After posting the question, it occuurred to me that a simple solution is to create a wrapper script for starting the X server from gdm.conf-custom. The wrapper scans the PCI bus to determine if the Number 9 card that drives my SGI 1600SW is present, and, if so, starts the X server with the layout I created in /etc/X11/xorg.conf that uses this hardware. Otherwise, the X server is started with the default layout, which uses the laptop's built in hardware.

To get this to work, I first created a custom wrapper script: /etc/gdm/gdm-startx:

```
#!/bin/sh

# site local script to start X for GDM

# scan PCI bus to determine if Number 9 Rev IV is attached
dockhardware=`X -scanpci 2>&1 | grep "Number 9 Computer Company Revolution 4"`
if [ ${#dockhardware} != 0 ]; then
        # it is. use layout for SGI 1600SW
        layout="-layout SgiLayout"
fi

# run the server with the layout and the args we were passed
exec X $layout $*
```

Next, I modified the "[server-Standard]" section of /etc/gdm/gdm.conf-custom to call my wrapper script:

```
[server-Standard]
name=Standard server
command=/etc/gdm/gdm-startx -br -audit 0 
flexible=true

```

The trick in writing the wrapper is determining the correct string to look for in the output of the [FONT="Courier New"]X -scanpci[/FONT] command. If X is already running and you try to run this command, it balks because it detects the X server's lock file:

```
mrf@mrf$ sudo X -scanpci

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again
```.

For the purposes of capturing the output, I removed the lock file and re-ran [FONT="Courier New"]X -scanpci[/FONT] so that I could copy/paste the identification string into my wrapper script.

This is working well for me, and allows me to use the bigger display when docked and the builtin display when standalone without any hiccups.

---


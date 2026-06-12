---
title: "had ubuntu and installed kubuntu-desktop.... and they became one?!?!"
date: 2009-03-01
forum: General Help
---

### Post by bluemarble on 2009-03-01
hello, after a year or so of playing around with ubuntu I still have not leant much. I have installed ubuntu 8.10 on my new asus n10 and decided to try out the Kubuntu-desktop which work out well. I prefer ubuntu-desktop...

I then tried to install UNR on the ubuntu installation.... things didn't work out very well

Now I have a blank ubuntu-desktop with no panels or menus and Kubuntu-desktop has all its menus plus all the ubuntu panels and menus (see screen-shot attached), kubuntu even has UNR.

I tried reinstalling gnome-panels, ubuntu-desktop, kubuntu-desktop etc but nothing has working.

In the Grub menu when try and boot recovery mode I get a error 32 message, what ever then means.

when I tried using the desktop-switcher i got the following in terminal...

I am two days away from complete system reinstall... hopefully some brilliant mind in the wonderful land of ubuntu and save me!

bluemarble@flyingbee:~$ desktop-switcher
In classic mode: false
bluemarble@flyingbee:~$ desktop-switcher
In classic mode: false
** (desktop-switcher:6758): DEBUG: Enabling classic mode
** (desktop-switcher:6758): DEBUG: Suppressing Launcher autostart
** (desktop-switcher:6758): DEBUG: Unable to suppress launcher autostart: Error opening file '/home/bluemarble/.config/autostart/netbook-launcher.desktop': File exists
** (desktop-switcher:6758): DEBUG: Killing the launcher
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6762): WARNING **: Failed to send buffer

** (nautilus:6762): WARNING **: Failed to send buffer
** (desktop-switcher:6758): DEBUG: Restoring panel settings

** (nautilus:6762): WARNING **: Unable to add monitor: Not supported

** (nautilus:6762): WARNING **: Unable to add monitor: Not supported
** (desktop-switcher:6758): DEBUG: 
Restored panel configuration from: /home/bluemarble/.config/desktop-switcher/classic-panel-config.xml

gnome-panel: no process killed

** (desktop-switcher:6758): WARNING **: Failed to send buffer
bluemarble@flyingbee:~$ Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Disabling the GTK-Qt Theme Engine for "gnome-panel" 
Unable to open desktop file XP%2520desktop-1.desktop for panel launcher

(gksu:6828): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

---


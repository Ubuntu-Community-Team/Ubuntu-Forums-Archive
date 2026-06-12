---
title: "Gnome Shell Graphic Problems"
date: 2011-10-24
forum: Desktop Environments
---

### Post by Diemex on 2011-10-24
Ubuntu Oneiric Oncelot 64 bit
Ati radeon 4890 - fglrx proprietary driver
[IMG]http://i1232.photobucket.com/albums/ff375/D1emex/Screenshotat2011-10-24145012.png[/IMG]


I gave Unity a try for about a week and decided that it is just too buggy and doesnt't do what I want it too (menus integrated into the statusbar, windows are sometimes stuck and soforth...).

I like the idea of Unity, but it seems not finished yet. Now I want to give Gnome-Shell a try. 


I went ahead and just simply installed gnome-shell, this is the result.

The main shell window looks fine but the everything in the statusbar is just messed up.


Well after trying out some stuff, removing fglrx and installing radeon-driver I seem to break more and more stuff.

For example the Catalyst Settings Manager doesn't save the settings anymore and always reverts back.[IMG]http://s1232.photobucket.com/albums/ff375/D1emex/?action=view&current=Screenshotat2011-10-24145012.png[/IMG][IMG]http://s1232.photobucket.com/albums/ff375/D1emex/?action=view&current=Screenshotat2011-10-24145012.png[/IMG]

---

### Post by bcarlowise on 2011-10-24
Follow the instructions here to completely uninstall the fglrx driver and reinstall the radeon driver. It worked for me flawlessly:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Diemex on 2011-10-24
Thanks!
Gnome Shell is working now.
But I have a problem with the Radeon Driver. 

The fps in minecraft is VERY poor. I get about 8-12 fps while i get at least 40 fps with fglrx.

Has someone got an idea how to fix this?

Could I change the driver that is used when I open minecraft or can i maybe create a menuentry in the loginscreen that will use fglrx and gnome 2 instead so I can still play minecraft?

---


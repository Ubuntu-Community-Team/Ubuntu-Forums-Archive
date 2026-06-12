---
title: "Configuring lirc to control system sound"
date: 2009-02-01
forum: General Help
---

### Post by aliam13_2 on 2009-02-01
Hi.

I am running Ubuntu 8.10. Before I started messing around my remote control on my TV card had limited functionality. I could change volume - which would change the gnome default mixer and thus display the nice compiz sound level information. 

I however needed my remote to have more functionality, for example with MythTV. I now have working, my remote control. I have installed and setup lirc properly. When i run "irw" and presses buttons on my remote control, i see the various events that are sent. I have partly configured my .lircrc file to control MythTV and rhythm box. However I have a single annoying issue. I can not control sound volume in a good way. Firstly I don't seem to be able to get the volume control in MythTV to use my pulse audio master channel - If I could do this then that may be enough to make me happy, altough rhythmbox would also need to do the same and I think rythumbox will only control its own sound, not the system sound.

The way I thought I would solve this is to use irexec to have a kind of master volume (no other apps using lirc would respond to volume events of the remote). Then irexec would control the gnome volume - just like my remote did in the first place, where I would see the compiz display with the current sound level. I found scripts in /etc/acpi to "simulate" pressing the vol+/- buttons on my keyboard, but you need to be root for these scripts to work. I do not fancy running irexec as root.

Does anyone know how to:
a) Get execir (or something else, maybe gnome or compiz) to control volume via gonme - so that i get the compiz display. I this this is my prefered setting.

or 

b) get at least MythTV to use my pulseaudio master channel as the sound 

Thanks
Liam

---

### Post by aliam13_2 on 2009-02-01
I am now convinced that mapping various remote control keys to the multimedia keys on my keyboard is the correct thing to do. The volume keys will work better in this way and possible keys such as Play, Stop, Pause etc as most applications work with my keyboard's multimedia keys anyway.

---


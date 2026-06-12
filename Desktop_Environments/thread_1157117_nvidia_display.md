---
title: "nvidia display"
date: 2009-05-12
forum: Desktop Environments
---

### Post by santaris on 2009-05-12
Hello.Yesterday i installed ubuntu 9.04.I was enthousiased because i saw something good at first sight.But i have a problem with the display.I have installed the nvidia drivers the latest using hardware drivers and when i try to change my display using Preferences->Display it shows me that:"t appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"And when i answer yes it directs me to nvidia X Server Settings.I change my display.But i have 2 problems.First the display is on 1024x768@60 and the screen shakes(i don't know if this is the right term).And second when i reboot my PC all the changes are lost.And i have to do it again.Any idea?

---

### Post by nacho32 on 2009-05-12
to get rid of shakes or called flicker change the mhz to higher like 70 or up. Make sure you hit apply at the bottom, this should save  your settings.

---

### Post by Neil_LT on 2009-05-12
The flicker rate is usually fairly easy to resolve, as stated the higher the flicker rate the less you notice it.

I have had a similar issue to you, and that is the the Nvidia control panel is not saving my settings.

I'm sure that this is something to do with file permissions, but I have to many other things to try and work out, mainly how to get my dual screening working properly.. but thats another post

The way I get round the saving issue is I run sudo nvidia-settings from a command prompt.

I know thats not the proper way of doing it, and I'm sure as many of you are reading this your screeming "NOOOO you shouldn't do it" and I'm sure your right, but it works for me.

Hope this helps someone

---

### Post by santaris on 2009-05-13
I do hit the apply and i do run sudo nvidia-settings to change my resolution and save it into my xorg.conf.But when i restart my PC the display is always on 800x600

---

### Post by Manigoldo on 2009-05-13
I have had a similiar problem myself. I don't have problems with my resolutions but I can't seem to set my dual screen settings as I need to enable my secondary screen every boot. It says my config has been saved and I have used the methods supplied but still... not a major problem for me but it would be nice to sort it out

---


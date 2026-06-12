---
title: "Can't apply theme with Emerald or gdmsetup"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by superlolman on 2007-03-30
I have recently installed unbuntu edgy eft 6.10 and downloaded the latest updates. All I have installed so far are the drivers for my ATI card (pain in the ***), Beryl and xgl.

This is all working great and looks amazing and runs smooth and fast unlike vista did :mad: 

When I attempt to apply a theme nothing happens, although when I go to log out on the login screen the theme has applied. But it won't apply to the desktop.

Any one have an idea why, I have googled but can't find anything that has fixed it.

Thanks.

---

### Post by mcduck on 2007-03-31
That's a common problem when using Ati & XGL. To solve add 'gnome-settings-daemon' to your startup programs in System/Preferences/Session.

To change Emerald themes you need to select the theme you want and then restart Emerald (you can do that with the Beryl icon in your Notification Area)

---

### Post by superlolman on 2007-03-31
Thanks for help mate, I have tryed that and still can't get anything to apply apart from the System>Preferances>Theme 

Added to startup, but hasn't made a differance. I tryed reapplying another theme but it only changes on the login screen not my desktop?

Any more ideas guys?, I think I have the drivers running correctly, them seem to be working good and I have Beryl set up all nicely, the only thing annoying me is I can't have another theme applyed :( 

limey@fuckwiggle:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6400 (8.35.5)

Don't know if anything else would be usful, but thankyou for help duck. :)

---

### Post by mcduck on 2007-04-04
What theme are you trying to install? Login screen themes and desktop themes are two different things.

Use GTK2-themes for your applications, and Metacity themes for window borders. Icons are, well, icons, and GDM themes are for login screen.

---

### Post by petey220 on 2008-04-01
Help! i've been using Emerald theme manager for a few days now and have installed a few nice themes, but i now want to use just the normal human theme which came with ubuntu preinstalled, but whenever i click the human theme it doesnt do anything??!!! any help???



oh it changes everthing just not the the border??

---

### Post by armory555 on 2008-04-01
look at my post(one up form urs)mabye it will help cuz i think i did sumthing with emerald themes

---


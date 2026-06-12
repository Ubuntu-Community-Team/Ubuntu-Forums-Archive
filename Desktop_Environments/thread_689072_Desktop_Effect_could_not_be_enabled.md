---
title: "Desktop Effect could not be enabled"
date: 2008-02-06
forum: Desktop Environments
---

### Post by anonymousT on 2008-02-06
Hi, I'm trying to enable desktop effects.
 I went to [COLOR="blue"]menu->system->prefs->appearance->visual effects[/COLOR] which by default is set to [COLOR="Blue"]no effect[/COLOR], when I try to set it to any of the other options it says [COLOR="Blue"]desktop effects could not be enabled[/COLOR]
Then I went to [COLOR="Blue"]system->prefs->advanced desktop effect settings[/COLOR]
(after i installed [COLOR="Blue"]compizconfig-settings-manager[/COLOR]),  poked around, but none of them seemed to work
my graphics card is ati radeon x1400 and i just upgraded my system from 7.04

any help is much appreciated

---

### Post by irrdev on 2008-02-06
I have had the same problem on my office computer. I have a decent NVIDIA Graphics card with 128mb of memory and a 1.66GHZ i386 processor. For me, the problem seems to be my limited RAM of only 256mb. I plan to increase my RAM to 1GB, and I hope that this might do the trick. GNOME is truly ugly without any desktop effects in place. ;)

---

### Post by MasterJS on 2008-02-06
Now for both ATI and Nvidia, you need to install the restricted drivers (which if you haven't, you install them through the restricted drivers manager: SYSTEM > ADMINISTRATION > RESTRICTED DRIVERS MANAGER)
Now, one more thing for ATI, you need to install XGL. There are tutorials around google so poke around. I had to do it for Feisty Fawn, which has its own process, while in Gutsy its a lot easier as all you need to do is install it from the repositories and thats it.

---

### Post by mtbsoft on 2008-02-08
> **anonymousT said:**
> Hi, I'm trying to enable desktop effects.
 I went to [COLOR="blue"]menu->system->prefs->appearance->visual effects[/COLOR] which by default is set to [COLOR="Blue"]no effect[/COLOR], when I try to set it to any of the other options it says [COLOR="Blue"]desktop effects could not be enabled[/COLOR]
Then I went to [COLOR="Blue"]system->prefs->advanced desktop effect settings[/COLOR]
(after i installed [COLOR="Blue"]compizconfig-settings-manager[/COLOR]),  poked around, but none of them seemed to work
my graphics card is ati radeon x1400 and i just upgraded my system from 7.04

any help is much appreciated
I had exactly the same problems and found it because I upgraded from 7.04 rather than doing a fresh install of 7.10.  I followed every install guide for the ATI drivers that I could find and none worked - I have the x1400 in my laptop too.

Be warned though that even a clean install isn't without problems, you'll have to use the alternative CD and do the textual install then install the drivers afterward to get the graphics going.

---


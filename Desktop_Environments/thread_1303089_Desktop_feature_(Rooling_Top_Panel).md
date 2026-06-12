---
title: "Desktop feature? (Rooling Top Panel)"
date: 2009-10-27
forum: Desktop Environments
---

### Post by toolmanpaul on 2009-10-27
i tried SAM live cd the other day...i really like way applications scroll around a center wheel on the desktop.!. Anyone know how i can do that with my xubuntu? Thanks

[SIZE=4]**[undecim]("http://ubuntuforums.org/member.php?u=623644")**[/SIZE] wrote
That's would be Compiz's "Ring Switcher"

To do that, you need to be running compiz (desktop effects)

If compiz is working on your system, make sure you have the settings manager installed by typing the following into a terminal: 	Code:
 	sudo aptitude  isntall compizconfig-settings-manager 
Then, press ALT+F2 and type "ccsm" to open the compiz settings manager.

Disable the "Shift Switcher" and enabled the "Ring Switcher"

Optionally, click the Ring Switcher Icon to configure the Ring Switcher's behavior to your liking.

[COLOR=SeaGreen]**I don't seem to have a shift switcher or a ring switcher! I looked in every box that i could think might have it.. Any more help out there??**[/COLOR]

---

### Post by lidex on 2009-10-27
Look for compiz related packages in your package manager. Here is a screenie of my installed packages.You could be missing some plugins.
:( Note: You will not need all these packages as some refer to emerald and cairo-dock; just ignore those.

---

### Post by toolmanpaul on 2009-10-28
> **lidex said:**
> Look for compiz related packages in your package manager. Here is a screenie of my installed packages.You could be missing some plugins.
:( Note: You will not need all these packages as some refer to emerald and cairo-dock; just ignore those.
[COLOR=Blue]
i used the add remove in applications .. when i try the apt-get command i get an error message when i type ./configure .. so what do i do to correct this?? .. [/COLOR]

---


---
title: "Unable to install my nVidia accelerated graphics driver (version 177) [Recomended]"
date: 2009-04-23
forum: General Help
---

### Post by Chrono Reaper on 2009-04-23
whenever I click on the nVidia graphics driver in Kubuntu 8.10 and click activate, the loading window will only appear for a second and then it will disappear. There is no Spinning arrow symbol that appears over the circle telling me it installed and needs restarting. What would be the problem?

EDIt: 

here are my specs...

DELL XPS M1730
Intel Dual Core Pro Processor
4GB of RAM 
nVidia 8700 GT SLI with Agiea PhysX

---

### Post by HankB on 2009-04-23
I don't know.

It sounds like the program is exiting abnormally. You may find clues by:

- checking logs in /var/log.

- check the output of 'dmesg.'

- find the name of the program  that installs the drivers by checking the properties on the menu item (System -> Preferences -> Main Menu -> <find the entry and check properties>) Looks like /usr/bin/jockey-gtk. You can run that from a terminal window with 'sudo /usr/bin/jockey-gtk' and you might see some error messages.

HTH,
hank

---


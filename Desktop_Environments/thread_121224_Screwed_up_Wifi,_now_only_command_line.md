---
title: "Screwed up Wifi, now only command line?"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Pojodojo on 2006-01-24
I recently used one of the how tos on here to configure my broadcom wireless card. I got it all working correctly, at least i thought, but it would never use the wireless, so i set it to be the default device for my Networking. Before i restarted, i had 4 green bars on my panel for the strenght, but it didnt seem to be able to actually use it. Then i restarted, and when it booted, it would get to the Detecting Network or whatever in the Ubuntu startup, and it woudl all of a sudden revery to the non GUI(pretty) checklist, with all teh ok/fail things, and it didnt give me a fail on the network, but it gave me a fail on sync the time with...

it then goes the the bash login screen, which i can log on and all, but when i type sudo startx,  i get a bunch of errors and it says its already running. 
Any ideas what i would have done that woudl screw it up like that? and no jokes about "just use the command line" please

---

### Post by sanitario on 2006-01-24
You can try to see if X is running on virtual terminal 7 (which is default), by pressing:

ALT + F7

You can also try to restart X by running: 
sudo invoke-rc.d gdm restart

---

### Post by kryrinn on 2008-04-05
I can confirm the same bug (in Hardy), using the howto here:

[http://ubuntuforums.org/showthread.php?t=738216&highlight=hardy+heron+broadcom+4318]("http://ubuntuforums.org/showthread.php?t=738216&highlight=hardy+heron+broadcom+4318")

Only difference is I couldn't get wifi to even recognize before I restarted, and got a root command line.

---


---
title: "Network Manager loads but isn't on Panel"
date: 2006-01-17
forum: General Help
---

### Post by karate_y2k on 2006-01-17
I recently installed ubuntu and it's great!  I had network manager in the top panel working fine (aka visible).  Now, whenever I boot, it loads (I get prompted to answer my key-chain password) and I log-on to the network, but it is no longer visible in the panel.   Under System--> Preferences-->Sessions-->Startup Programs, I have nm-applet listed.  What do I need to do to get my applet back in the panel?  Thanks.

---

### Post by lamego on 2006-01-17
Right click over the panel -> Add to Panel -> look for the network monitor applet

---

### Post by karate_y2k on 2006-01-17
I tried to add it to the panel as you suggested, however, it is not an option.  I verified it was installed, and tried uninstalling/reinstalling just to make sure.  It still isn't present.  Any other suggestions?

---

### Post by Michael Steinberg on 2006-01-17
Perhaps the notification area got removed from the panel. Nm-applet only lives in the notification area. You might be able to add a new one with the add-to-panel dialog and hope that nm-applet will take up residence there again when you relaunch Gnome.

---

### Post by dcstar on 2006-01-17
[QUOTE=karate_y2k]I tried to add it to the panel as you suggested, however, it is not an option.  I verified it was installed, and tried uninstalling/reinstalling just to make sure.  It still isn't present.  Any other suggestions?[/QUOTE]
Change your desktop theme back to one of the basic Ubuntu ones, and see if it suddenly appears on your panel.

---

### Post by karate_y2k on 2006-01-17
Thanks for all the help, it seems the notification area disappeared.  Now I have another problem.  When I insert my wireless card, it works fine and connects to my network.  Within 10 seconds, Network Manager takes over and effectively shuts the card down.  Network manager can't see any networks, but System-->Administration-->Networking-->Configure can.  Any suggestions?

---

### Post by danish_demon on 2006-05-21
alright everybody, i am having the same problem, but the mentioned fixes aren't working.  my notification area is working (i started gaim and that icon shows up immediately) and nm-applet is running in the background.  i tried changing themes to a default ubuntu one, but still nothing in the notification area.  i had this working a while ago, but got frustrated at it since it always initially tried to connect using my disabled wired ethernet card, and would occasionally cause my system to freeze.  any other ideas?

thanks.

---


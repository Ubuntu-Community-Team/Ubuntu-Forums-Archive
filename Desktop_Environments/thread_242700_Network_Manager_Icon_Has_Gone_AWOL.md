---
title: "Network Manager Icon Has Gone AWOL"
date: 2006-08-24
forum: Desktop Environments
---

### Post by bmor4590 on 2006-08-24
Hey
I accidentally deleted the network manager icon (with the 4 little bars) from my notification area on the top panel. I cant figure out how to get him back,  or control my wireless network in his absence. Ive tried
  - Stopping and restarting nm-applet
  - Reinstalling Network Manager
  - right clicking on the panel/add to panel etc.. but that only allows me to   make an icon to launch nm-applet, i need the icon that allows me to select wireless networks and such.

Any ideas?

---

### Post by bmor4590 on 2006-08-24
Hey again thanks for the huge influx of replies but i managed to work it out, thought i better post just incase another noob stumbles into the same trap. If your nm-applet is missing from the notification area and
   1. You have it installed correctly
   2. It is running but you cannot access it
   3. You have the notification area on a panel
   4. It is not a theme issue

Then check System/Preferences/Sessions startup programs and check that nm-applet is present, NOT nm-applet--sm-disable.

I know its pretty obvious but it kept me guessing for the best part of my day off. Dammit

---

### Post by Fitzcarraldo on 2006-10-17
> **bmor4590 said:**
> Hey again thanks for the huge influx of replies but i managed to work it out, thought i better post just incase another noob stumbles into the same trap. If your nm-applet is missing from the notification area and
   1. You have it installed correctly
   2. It is running but you cannot access it
   3. You have the notification area on a panel
   4. It is not a theme issue

Then check System/Preferences/Sessions startup programs and check that nm-applet is present, NOT nm-applet--sm-disable.

I know its pretty obvious but it kept me guessing for the best part of my day off. Dammit

The Network Manager icon disappeared from my Panel too - I somehow managed to delete it when trying to move things around on the Panel.

Even with "nm-applet --sm-disable" left as it is in System -> Preferences -> Sessions -> Startup Programs, Network Manager seems to be working. In my case I just needed to right-click on the Panel, select 'Add to Panel', and then select 'Notification Area' (it's in the Utilities section in the 'Add to Panel' window). Voilà - the Network Manager icon reappeared on the Panel.

---

### Post by Joh_ on 2006-10-17
Right click the panel > choose "Add to panel..." > pick the network manager under "System & Hardware" > Add > right click the network manager that popus up in the panel > choose "Properties". Under "Connection", set "Name" to the name of your device (eg. in my case it's wlan0). If it isn't listed (mine wasn't), just type it in.

Note that some translations might be incorrect as I'm not using the english version of ubuntu.

**Edit:** Missed the part where you said it was already resolved. :p

---

### Post by thekip on 2007-02-22
you should try installing
network-manager-gnome

that is the tray utility I had the same problem ;)

---

### Post by bakermiller on 2007-05-12
> **Fitzcarraldo said:**
> The Network Manager icon disappeared from my Panel too - I somehow managed to delete it when trying to move things around on the Panel.

Even with "nm-applet --sm-disable" left as it is in System -> Preferences -> Sessions -> Startup Programs, Network Manager seems to be working. In my case I just needed to right-click on the Panel, select 'Add to Panel', and then select 'Notification Area' (it's in the Utilities section in the 'Add to Panel' window). Voilà - the Network Manager icon reappeared on the Panel.

thanks i was freaked out because i could not get network manager applet in the panel back for the last  three hours.

why call it "notification area!??".

thanks

---


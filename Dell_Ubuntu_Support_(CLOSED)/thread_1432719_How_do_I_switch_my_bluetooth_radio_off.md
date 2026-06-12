---
title: "How do I switch my bluetooth radio off?"
date: 2010-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tuesdaytaurus on 2010-03-18
I have a Dell Inspirion 6400 with a built in Blue-tooth radio. Under Ubuntu 9.10 (gnome) and earlier I was able to easily switch off the BT radio, but since I recently converted to KDE I am unable to do so. The only reason I want to do this is to conserve what little battery life the laptop has left, when not plugged in to mains.

Any help will be appreciated.

---

### Post by gradinaruvasile on 2010-03-18
Use rfkill. Its console-based command, but can be made into a menu item. I use it on Dell D630 and works wonderfully. I made a toggler switch too for it. I have it on my panel, clicking on it toggles on/off the bluetooth device. I even made it to use notifications, but that is gnome-specific.
Other than that i use blueman manager - it is way better than the default system.

The script:
```
#!/bin/bash

RFBT_SOFT_STATUS=`rfkill list | sed -n 5p`
RFBT_HARD_STATUS=`rfkill list | sed -n 6p`

#if [[ $RFBT_HARD_STATUS =~ "Hard blocked: yes" ]] ;
#  then
#    echo "Killswitch is on"
#    notify-send "Killswitch is on, disable it if you want to use wireless..."
#    exit
#  else 

   if [[ $RFBT_SOFT_STATUS =~ "Soft blocked: yes" ]] ;
     then
	echo "Bluetooth is soft blocked, enabling..."
	rfkill unblock bluetooth
	notify-send "Bluetooth enabled"
     else
	echo "Bluetooth is unblocked, disabling..."			
	rfkill block bluetooth
	notify-send "Bluetooth disabled"
     exit
   fi
fi

```

---

### Post by tuesdaytaurus on 2010-03-18
Thanks gradinaruvasile. The script works like a charm. I'll also give blueman a try. Now I only have to  figure out how to create a nice little launcher for that script in KDE.:D

---

### Post by gradinaruvasile on 2010-03-18
I dont know my way around KDE, but here is how mine works under Gnome:
I created a menu entry - the command line for the menu launcher on my computer:

```
gksudo bash /home/laca/bin/rfkill-bt-toggler
```

replace gksudo with its kde graphical sudo counterpart, the script name and path with the correct ones on your system. The "bash" is a must, otherwise the script wont execute with root rights.

As for icon, just look around for icons, surely you will find a bluetooth somewhere.

Also, you might try uncommenting in the script that part that deals with the hard switch - i commented it out because on my laptop sometimes the bluetooth is reported hard locked and soft unblocked, but in fact it was active with the 2.6.32 kernel - the soft lock is reported ok at all times, the script works perfectly without it this feature. Its essentially a reminder if the hard killswitch (a phisical sliding switch that kills all radio) is activated.

---

### Post by tuesdaytaurus on 2010-03-19
> replace gksudo with its kde graphical sudo counterpart, the script name and path with the correct ones on your system. The "bash" is a must, otherwise the script wont execute with root rights.
According to the only documentation I could find, the replacement command should be *kdesudo*. To create a new Launcher, simply right-click on the Application Launcher widget and select the *Menu Editor* option. It is pretty intuitive from there. It even has a nice Icon picker that shows all the icons of the installed apps and tools.
When running the script through the new launcher, I still get requested to enter the sudo password. But if I remove the *kdesudo* command altogether it works just fine without requesting a password.

---


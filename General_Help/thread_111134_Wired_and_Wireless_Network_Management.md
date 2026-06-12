---
title: "Wired and Wireless Network Management"
date: 2006-01-01
forum: General Help
---

### Post by jrattner on 2006-01-01
In my opinion Network Manager (package: network-manager) is the most effiecent network tool I have seen.  Does anyone know of any other tools that function similar to network manager and may be more effective?  Or any other good wired/wireless network tools?

---

### Post by Fr33d0m on 2006-01-25
[QUOTE=jrattner]In my opinion Network Manager (package: network-manager) is the most effiecent network tool I have seen.  Does anyone know of any other tools that function similar to network manager and may be more effective?  Or any other good wired/wireless network tools?[/QUOTE]

So far I've tried wifi-radar, gtkwifi and network-manager.   None of them work for very long and none of them provide full functionality.

Only wifi-radar seemed to allow me to configure which channel the connection should use.  Only gtkwifi allowed me to setup preferred networks and provided a usefull display of the connection status.  In network-manager's defense, some folks seem to be able to right-click on the somewhat useless panel icon to get more functionality so I am not able to say much other than its only useful function seemed to be the disconnect button.  Of course since I saw no connect button, that usefulness is really not.

Still at the moment I'd have to agree with you.  It is likely that NM is the better of these and the one most worthy of our adulation.

---

### Post by Fr33d0m on 2006-01-25
[QUOTE=Fr33d0m]So far I've tried wifi-radar, gtkwifi and network-manager.   None of them work for very long and none of them provide full functionality.

Only wifi-radar seemed to allow me to configure which channel the connection should use.  Only gtkwifi allowed me to setup preferred networks and provided a usefull display of the connection status.  In network-manager's defense, some folks seem to be able to right-click on the somewhat useless panel icon to get more functionality so I am not able to say much other than its only useful function seemed to be the disconnect button.  Of course since I saw no connect button, that usefulness is really not.

Still at the moment I'd have to agree with you.  It is likely that NM is the better of these and the one most worthy of our adulation.[/QUOTE]

I reinstalled it and found no right-click functionality. Perhaps it is a version issue.

---

### Post by stardotstar on 2006-01-25
I have broken my wired and wireless lan interface configurations several times meddling with NM (esp the next unstable version) and ultimately had to go to a clean install (very frustrating) but I have found NM to be the most reliable - it switches between my work wired and wireless and home wireless effortlessly though it does seem to be very picky about WEP keys - my wireless at work works flawlessly (with a D-Link) and Hex Key transaction but the one at home (an old Net_Geat WGR614) drops on and off a lot if I have any WEP at all - still playing with the combinations...  It seems that other processes are interfearing with the key exchange and I can't work out where NM stores its configuration data for its networks.

There must be a way with NM to fine tune the settings for each network in the way that WiFi Radar lets you do in a config file like /etc/network/interfaces...

I really like NM but still don't know enough about wifi to fine tune for reliable performance (or it could be my w-router it is picky even under windows).

Will

---


---
title: "View Wireless Networks Icon has Disappeared"
date: 2011-01-28
forum: Desktop Environments
---

### Post by ebodnaruk on 2011-01-28
Hi, I just upgraded to Ubuntu 10.04 LTS from 9.10 and the icon that lets me view and choose wireless networks to connect to has mysteriously disappeared.  

I did the whole "Add to Panel" thing and added the "Network Connections" icon to my task bar, but for all the searching through that and other things like System -> Preferences -> Startup Applications, I just can't find a solution!  

The Network Preferences still has the list of all the wireless networks I have connected to in the past.  It still connects to my home network automatically (although I did have to delete another neighboring network from the Network Preferences list so it only has one auto connection to connect to).  So where in the world did my icon go?  It was so great.  Left click to see all local wireless networks and to connect.  Right click to turn off networking or wireless.  

I looked around everywhere and couldn't find a problem like this in the forums.

Thanks for your help!

---

### Post by conradin on 2011-01-28
Ive had this.. I reinstalled / restarted gnome panel I would get the network manager back. But thats prolly not the best option, also, I havent seen that  since lucid was in Alpha. 
The software source is:
[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)
 you could try to re-install from the package manager.

---

### Post by mscir on 2011-04-05
This worked for me:

[http://www.tech-recipes.com/rx/2716/ubuntu_restore_wireless_bluetooth_battery_icon_back_top_panel/](http://www.tech-recipes.com/rx/2716/ubuntu_restore_wireless_bluetooth_battery_icon_back_top_panel/)

Ubuntu – Restore wireless / bluetooth / battery icon back to Top Panel

....Just readd the Notification Area back under Utilities in the Add to Panel menu...

[LIST=1]
[*]Right-Click on the Top Panel area or whichever Panel you want to add the icons too and choose Add to Panel

[*]Scroll down to the Utilities area and either Drag the Notification Area item to the Panel or click on it and click the +Add butto
[/LIST]n.

---


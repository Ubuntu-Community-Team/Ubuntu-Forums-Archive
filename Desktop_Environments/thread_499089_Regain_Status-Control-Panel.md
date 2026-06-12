---
title: "Regain Status-Control-Panel"
date: 2007-07-12
forum: Desktop Environments
---

### Post by muh2k4 on 2007-07-12
Hey there.

Iam quite new to Ubuntu, use it with the GNome-Environment.

I just made a misclicked and removed a statusbar from the top panel and i dont how to bring that back.
It contained information about the laptop battery, had a signal strength indicator as well as a list of running apps ... quite comparable to the systray of windows.

When i click on add_to_panel i receive a list, but non of these matches the panel i just kicked!

Does anybody have a suggestion on how to recreate that panel?

Thanksin advance =/

EDIT: It was also the place where i did my wlan-configuration when i entered new networks etc ... so the need for me as novice user for that panel is quite an urge!

---

### Post by mcduck on 2007-07-12
Right-click on the top panel, select 'Add to Panel', then find the Notification Area-applet and drag&drop it into your panel.

You can move it around by draging with middle mouse button. If it doesn't move past some panel applets, right-click those applets and make sure 'Lock to Panel' is not enabled.

---

### Post by muh2k4 on 2007-07-12
THanks ... that brought back the panel i described. Unfortenately it does not contain the indicator for signalstrength. Therefore i do not have direct access to the network-configuration-tool i was used to have.

To give a better description: When i right-clicked it i was able to en/disable wlan/lan and to connect to wlannetworks/create own networks. Regaining that icon as well and i will never click anything again here =)

EDIT: It was not the Network Monitor ... that ones has a different signaling method and does not give access to the desired wlan-config =/

I found an image on the web showing that indicator (top right)
[http://www.aseville.com/members/attachments/upload/2006/12/30/373.png](http://www.aseville.com/members/attachments/upload/2006/12/30/373.png) ... maybe this helps =)

---

### Post by mcduck on 2007-07-12
> **muh2k4 said:**
> THanks ... that brought back the panel i described. Unfortenately it does not contain the indicator for signalstrength. Therefore i do not have direct access to the network-configuration-tool i was used to have.

To give a better description: When i right-clicked it i was able to en/disable wlan/lan and to connect to wlannetworks/create own networks. Regaining that icon as well and i will never click anything again here =)

EDIT: It was not the Network Monitor ... that ones has a different signaling method and does not give access to the desired wlan-config =/

I found an image on the web showing that indicator (top right)
[http://www.aseville.com/members/attachments/upload/2006/12/30/373.png](http://www.aseville.com/members/attachments/upload/2006/12/30/373.png) ... maybe this helps =)

You probably need to log out and back again, (or even restart the machine) before the Network Manager appears in Notification Area again.

---

### Post by muh2k4 on 2007-07-12
Thank you.

Yes a reboot solved it. =D

---

### Post by Flashgordon20 on 2007-07-12
Pardon me for asking, but what applet is that in the gnome panel that shows the signal strength? The only one available for me to add is " Network Monitor" which is not the same one I saw in your picture. I am pretty new to the gnome environment also. Thanks

---

### Post by mcduck on 2007-07-15
> **Flashgordon20 said:**
> Pardon me for asking, but what applet is that in the gnome panel that shows the signal strength? The only one available for me to add is " Network Monitor" which is not the same one I saw in your picture. I am pretty new to the gnome environment also. Thanks

It's not any applet, it's Network Manager (that has it's icon inside Notification Area applet when running). Network Manager is installed by default in 7.04, but in older Ubuntu versions you need to install it yourself.

---


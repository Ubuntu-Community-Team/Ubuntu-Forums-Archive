---
title: "Wireless Network Monitor"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Branta on 2006-08-22
Ubuntu 6.06 LTS

I had two icons at the right end of the taskbar for a single wireless connection.  I right clicked and deleted the 1 I didn't want and both disappeared.  One icon was 2 monitors, one in front of the other and the other was a vertical bar graph indicating signal strength (preferred).

**How do I get the vertical graph icon restored** to the right side of the task bar?

I installed it yesterday so what was installed **_was the default monitor_**.

I don't know the default wireless utility I am/was using.  The wireless network still works fine.

--- Bob ---

---

### Post by vanchaser on 2007-08-23
Right Click on an empty space on the Panel. Select ADD NEW ITEM from the menu.

From there add the utility you had to monitor your signal strength. Most likely it was simply called NETWORK MONITOR.

To configure it, Right click on the new utility. Select PROPERTIES. From there only have to add in the device you need to monitor. Most likely its WLAN0.

Not sure what device it is called. Open a terminal window and type IWCONFIG. You should see your wireless card and what device name that linux thinks it is. Use THIS name in the configuration.

---

### Post by beetlejelly on 2007-11-14
I deleted mine as well. The "network monitor" icon available in "add to panel" is different than the wireless networking status icon that allows you to see and select wireless networks. Have you figure out how to get it back? :confused:

---

### Post by destructaball on 2008-01-13
First problem solved, the network monitor isnt an applet, to get it back, right click the task bar and go to add to panel and add a notification area to the screen, this is the area that pidgin messanger and other such takbar things live (sorry for my lack of description) and then resart your computer Ctrl+Alt+Backspace and the wireless monitor will be back

---

### Post by psychicdragon on 2008-01-13
> **destructaball said:**
> First problem solved, the network monitor isnt an applet, to get it back, right click the task bar and go to add to panel and add a notification area to the screen, this is the area that pidgin messanger and other such takbar things live (sorry for my lack of description) and then resart your computer Ctrl+Alt+Backspace and the wireless monitor will be back
Restarting your computer for this is complete overkill. The only time you should ever have to reboot is if you installed a new kernel. You can just press Alt + F2 to open the run dialog and enter 'nm-applet' to start the Gnome NetworkManager icon.

---


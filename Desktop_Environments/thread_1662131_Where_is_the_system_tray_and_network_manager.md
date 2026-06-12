---
title: "Where is the system tray and network manager?"
date: 2011-01-07
forum: Desktop Environments
---

### Post by tipp98 on 2011-01-07
I just installed xubuntu-10.10-i386 over pxe but there is no nm-applet. First, I thought is was because there were no drivers and thus it never showed itself. Then I found that the Atheros AR5001X+ and Realtek RTL-8139 both have open drivers and that it seems I have no system tray. I have sound, battery, and notification area icons but these look to be separate from the system tray. If I run nm-applet from the cli, it says it's already running. What package is the system tray part of in xfce or what is it called. If I try to add an applet I do not see it and if I type sys, or tray in the search bar it does not show.

---

### Post by Brandon Williams on 2011-01-08
If you right-click on the panel and select "Add New Items ...", is "Notification Area" one of the options? That is the system tray. Add this item to the panel and you should see the icons for any apps running that are displaying to the system tray. This panel plugin is part of the xfce4-panel package, so if the panel is installed, then so is this plugin, and the panel is a required part of the xubuntu-desktop meta-package.

---

### Post by tipp98 on 2011-01-09
So, I do have the notification area, it is just not showing me the nm-applet. A fresh batch of search criteria brought up new results. I tried the suggestions @ [http://ubuntuforums.org/showthread.php?t=1176238]("http://ubuntuforums.org/showthread.php?t=1176238") to no avail. However, editing the file .config/xfce4/panel/systray* and changing nm-applet and the power applet to true, which I found means hiding, reveals the unhide arrow. Right clicking on that brought up a duologue where I could fix the mistake I just made.

Now, the info @ [http://ubuntuforums.org/showthread.php?t=1469625]("http://ubuntuforums.org/showthread.php?t=1469625") fixed the issue. Second page in was this.

> sudo edit /etc/NetworkManager/nm-system-settings.conf change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......

This was an ugly situation for a fresh install and really kills the out of box experience. I hope that this was caused by my install over pxe and not the default settings off the disk.

---

### Post by Dazed_75 on 2011-08-28
This does appear to be caused by the PXE boot although I have not determined whether the PXE server configuration (there a TON of variations) is responsible.

In addition, Ubuntu changed the name of the configuration file in 11.04.  It is now /etc/NetworkManager/NetworkManager.conf and nm-system-settings appears to be no longer in use so no killall is needed, just the reboot.

---


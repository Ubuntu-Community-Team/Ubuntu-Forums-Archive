---
title: "Wireless Networking in Openbox"
date: 2007-12-20
forum: Desktop Environments
---

### Post by BattlePanic on 2007-12-20
After using GNOME for a few months I got bored and decided to give Openbox a try.  I'm liking it a lot but I noticed that my system would no longer automatically connect to my wireless network after logging into pure Openbox via GDM, even though the NetworkManager daemon appeared to be running.

After some poking around I've discovered that when I used GNOME, it launched a program called nm-applet that seems network-related.  I've added the line "nm-applet --sm-disable &" to my Openbox autostart.sh script and I'm magically reconnected to my preferred wireless network.

I'm currently running Openbox without a panel or task bar of any sort so I'm not sure how I can change my wireless network settings.  What do I do when I want to move to another wireless network?  Are there alternative Openbox-friendly tools for managing wireless network connectivity?

If I need to run nm-applet to connect to my wireless network, what the heck is the NetworkManager daemon there for?

I'd really like to hear other Openbox users' wireless network setups.

---

### Post by cyberdork33 on 2007-12-20
nm-applet is the network manager panel applet... I think the daemon runs in the background, and is configured by the applet.

---

### Post by ugm6hr on 2007-12-20
> **BattlePanic said:**
> I'm currently running Openbox without a panel or task bar of any sort so I'm not sure how I can change my wireless network settings.  What do I do when I want to move to another wireless network?  Are there alternative Openbox-friendly tools for managing wireless network connectivity?


I don't use Openbox, but have used Wicd to connect to wifi networks before.  While it has an option for a panel icon, it is not necessary - you can just run it each time you need to connect or disconnect.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by BattlePanic on 2007-12-20
> **ugm6hr said:**
> I don't use Openbox, but have used Wicd to connect to wifi networks before.  While it has an option for a panel icon, it is not necessary - you can just run it each time you need to connect or disconnect.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Thanks a bunch for the tip.  I'm going to check this out.

---


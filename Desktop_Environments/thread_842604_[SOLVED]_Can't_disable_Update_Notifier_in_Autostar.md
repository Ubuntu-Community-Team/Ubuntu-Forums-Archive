---
title: "[SOLVED] Can't disable Update Notifier in Autostarted Apps"
date: 2008-06-27
forum: Desktop Environments
---

### Post by kortsen on 2008-06-27
I can't stop Update Notifier and Hardware Driver notifier from launching at startup.  They are deselected in "Autostarted Apps" but that does nothing. Here is what I have in Autostarted Apps right now.


[IMG]http://lars.kortsen.googlepages.com/Screenshot.png[/IMG]

[COLOR="Blue"][ ] Panel(panel)[/COLOR] is there but deselected because my panels disappeared one day.  I Googles one tip to put xfce4-panel in Autostarted Apps.  I found another tip to launch the panels with [Alt][F2] xfce4-panel, then right-click on the panel and reset the panel placement. The second tip worked so I disabled (but didn't remove) "Panel" in the Autostarted Apps.  *I'm pointing this out because this seems to be when my other problem started.*

[COLOR="Blue"][X] Mount Network Shares (Launch FuseSMB)[/COLOR] does exactly what it says and behaves exactly as advertised.  I added this myself and it has worked flawlessly since I first did it.

The next 2 items are the ones that don't behave.  They had been behaving fine until the panel problem popped up. Now, as noted above, Update Notifier launches at start-up, and after updating nvidia-glx the driver notifier popped up on the following reboot.

[COLOR="Blue"][ ] Print Queue Applet[/COLOR] is disabled because I don't have a printer.
[COLOR="Blue"]
[X] Power Manager[/COLOR] works just fine on my Toshiba laptop.

---

### Post by x1a4 on 2008-06-27
Hi,

Try looking in ~/.config/autostart/ which contains launchers for user-defined autostart apps.  If it's there delete it, if not (I'm not using it so I can't tell) then purge the Update Manager, remove its configuration files in your home directory.  This should work.  If you want to continue using the UM install it again.

---

### Post by kortsen on 2008-07-05
> **x1a4 said:**
> 
Try looking in ~/.config/autostart/ which contains launchers for user-defined autostart apps.  If it's there delete it,

I did that a week ago and haven't seen the notifier since.  I just ran synaptic, and there are a bunch of updates availabe.  It seems my problem is solved.

---


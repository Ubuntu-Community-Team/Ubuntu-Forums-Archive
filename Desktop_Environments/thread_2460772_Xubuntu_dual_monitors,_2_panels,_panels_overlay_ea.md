---
title: "Xubuntu dual monitors, 2 panels, panels overlay each other with one monitor"
date: 2021-04-18
forum: Desktop Environments
---

### Post by Kilarin on 2021-04-18
I'm using Xubuntu 20.04 on a laptop with an external monitor connected.
I have two panels, panel 0 on the laptop and panel 1 on the external monitor.  Both panels are at the bottom of their respective monitors.

When I disconnect the external monitor and use the laptop only, panel 1 that is normally on the external monitor moves to the laptop monitor and overlays panel 0.
Since all of my notification icons, particularly the status notifier icon that has the network manager applet on it are only on panel 0, the overlay causes these icons to show as greyed out and I can't click on them.
Which is a pain the the behind when trying to hook up to wifi.

[IMG]https://i.imgur.com/Jn4PQFo.png[/IMG]

Took me a while to figure out what was going on.  But now that I understand the problem, I do not know what the solution is.

I mean, I can manually move panel 1 out of the way when this happens, but that is an ugly and clumsy solution.  I can also add the status indicator to panel 1.  That works, but it doesn't really address the root issue.

Is there some way to indicate that when the external monitor is not connected, I want panel 1 to just disappear, not move to the laptop and overlay the panel there?

Thank you

---

### Post by Holger_Gehrke on 2021-04-19
> **Kilarin said:**
> 
Is there some way to indicate that when the external monitor is not connected, I want panel 1 to just disappear, not move to the laptop and overlay the panel there?


Sure there is, unless XFCE has reduced the configuration options in XUbuntu 20.04 from what was included in 18.04. In the 'Panel Preferences' you can select what display to show a panel on with the dropdown menu labeled 'Output'. This can be set to auto, primary or a specific display. You can get to the Panel preferences by right-clicking on a panel, clicking on 'Panel'->'Panel Preferences' or you can run 'xfce4-panel --preferences ***panel-number***' from a shell. A panel that is set to display on a specific display will not show up if that display is inactive or disconnected.

Holger

---

### Post by Kilarin on 2021-04-28
Thank you!  I didn't know that was what the "Output" dropdown did!

---


---
title: "Set default screen layout/configuration"
date: 2012-03-08
forum: Desktop Environments
---

### Post by ergosteur on 2012-03-08
I've been looking for hours now and can't find the option to save a default xrandr configuration in Ubuntu 11.10  (neither Unity or Gnome-shell).

My primary desktop PC has 2 monitors, one of which I use in portrait mode, the other in landscape. I'm using the open-source radeon driver, so xrandr is properly supported (I think).

In Ubuntu 11.04, classic Gnome 2 desktop, if I want to configure my screen layout, I open up "Monitor Preferences" (gnome-display-properties), arrange and rotate to my heart's content. Then I can click Apply, and that will temporarily apply my configuration. I can also click the "Make Default" button and have this configuration saved as default every time I log in AND for the login screen.

In Ubuntu 11.10 I cannot for the life of me figure out where the "Make Default" option has gone. The display resolution/layout is saved for the current user but doesn't apply to other users or the Lightdm login screen. With 12.04 now in beta, my 11.04 system is aging quickly but I can't move to a Gnome3/Unity environment if this feature is not available anymore.

I have no /etc/X11/xorg.conf, everything is done with xrandr. If possible I don't want to have an xorg.conf, as the dynamic mode setting is much better and means I don't have to boot to text mode and edit a conf file every time I change my display configuration.

Ubuntu 11.04 Monitor/Display configuration dialog. Note the "Make Default" button 
[IMG]http://i.imgur.com/Lyxwp.png[/IMG]

When you click the "Make Default" button, the sudo prompt appears for action org.gnome.randr.install-system-wide.
[IMG]http://i.imgur.com/tqfjl.png[/IMG]

Is it possible to do this in Gnome3/Unity?

---


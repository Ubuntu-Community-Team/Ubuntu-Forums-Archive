---
title: "Gnome fallback right panel gone"
date: 2017-07-22
forum: Desktop Environments
---

### Post by James Wilde on 2017-07-22
I'm using Gnome fallback kompiz on Ubuntu 16.04.  I was trying to remove an icon from the right top panel, the one with the icon that gives you the logout/suspend/reboot option, an icon for the network (where I start VPN), the keyboard selection, the state of the battery, etc.  Unfortunately something went wrong and the whole panel disappeared.

It's there if I go to Unity but not with kompiz or metacity.

How can I get it back please?  I have some icons there which I have installed, but I'd like the originals back.  Seen a few suggestions but none have worked.

Thanks in advance.

---

### Post by again? on 2017-07-22
To return the panels back to default layout you can run in terminal
```
dconf reset -f /org/gnome/gnome-panel/
```

The panels should just reload with default layout or it may kick you back to the greeter
to login again.

The icons seen on the top panel right are shown by one single applet, indicator-applet-complete.
To remove indicators you would do that through each individual application or for system indicators use dconf-editor.

---

### Post by James Wilde on 2017-07-23
Wow!  Thanks, Guber2.  It took a few seconds, but suddenly everything jumped back into place.  And thanks for the explanation.

---


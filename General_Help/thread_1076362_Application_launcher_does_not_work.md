---
title: "Application launcher does not work"
date: 2009-02-21
forum: General Help
---

### Post by mogliii on 2009-02-21
Hi,

I am sometimes using openvpn.
As the plugin for the networkmanager seems not to work, or I did not get it running, I tried to make a custom application launcher.

Note: I think this problem is not directly linked to openvpn, so I am !NOT! looking for solutions to run openvpn in a different way.

Here is the code that I am using for the application launcher in Gnome 8.10:
```
gksudo gnome-terminal --working-directory=/home/user/.vpn --hide-menubar --geometry=15x4 --title=OpenVPN -x openvpn client2.ovpn
```

When I execute this withouth the gksudo from a terminal, it works fine. But when I click the application launcher, nothing happens. No dialog, no window, no nothing.
 
What am I doing wrong? Becuase the following works without woes:
```
gksudo gnome-terminal
```

---


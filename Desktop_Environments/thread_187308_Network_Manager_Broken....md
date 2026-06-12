---
title: "Network Manager Broken..."
date: 2006-06-02
forum: Desktop Environments
---

### Post by roostishaw on 2006-06-02
Hello,
When I run 'nm-applet' (without the quotes, to launch Network Manager), it works fine and all with my wired ethernet connection. But when I click on the little NM icon in the task bar, and tell it to connect to my wireless network (WPA encrypted), it asks for the keyring password (which I set up a while back when I first started using Dapper, and have had no trouble until now) and I enter it, then it tries for about a minute, then just goes back to the wired network. Normally I run NM at startup, but to see what was going on I ran the following in the terminal, then went through the above mentioned steps:
```
roostishaw@ubuntu:~$ nm-applet

** (nm-applet:8687): WARNING **: <WARNING>       nma_dbus_send_with_callback_replied (): Error: couldn't find pending call 0x8191768 in tracking table.


** (nm-applet:8687): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:8687): WARNING **: Error saving passphrase in keyring.  Ret=5

** (nm-applet:8687): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:8687): WARNING **: Error saving passphrase in keyring.  Ret=5

** (nm-applet:8687): WARNING **: <WARNING>       nma_dbus_send_with_callback_replied (): Error: couldn't find pending call 0x82d3b30 in tracking table.

** Message: <information>       You are now connected to the wired network.
```

Any help is appreciated!
Thanks!

---

### Post by Cableless on 2006-06-02
Perhaps your keyring is corrupt?  Try renaming your original keyring in a console like this:

mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak

A new one should be created the next time that nm-applet asks for credentials.

---

### Post by roostishaw on 2006-06-03
```
roostishaw@ubuntu:~$ nm-applet

** (nm-applet:5853): WARNING **: <WARNING>       nma_dbus_send_with_callback_replied (): Error: couldn't find pending call 0x818b2e0 in tracking table.


** (nm-applet:5853): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:5853): WARNING **: Error saving passphrase in keyring.  Ret=5

** (nm-applet:5853): WARNING **: <WARNING>       nma_dbus_send_with_callback_replied (): Error: couldn't find pending call 0x836c2a8 in tracking table.

** Message: <information>       You are now connected to the wired network.
```

...That's what I get. Same thing...
Anyone?

---

### Post by roostishaw on 2006-06-03
Just a few minutes ago I reinstalled the following, then reboot, but still have the same problem as in my first post. I just did a search in synaptic for 'keyring', and did a reinstall on any installed programs it found. The ones I reinstalled were gnome-keyring, gnome-keyring-manager, libgnome-keyring-dev, libgnome-keyring0, and ubuntu-keyring.

Anyone had the same problem, or know how to fix it?
Thanks!

---

### Post by roostishaw on 2006-06-06
...bump...

---


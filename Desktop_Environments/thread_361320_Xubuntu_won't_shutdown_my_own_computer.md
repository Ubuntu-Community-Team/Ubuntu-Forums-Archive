---
title: "Xubuntu won't shutdown my own computer"
date: 2007-02-14
forum: Desktop Environments
---

### Post by picpak on 2007-02-14
Hello,

with Xubuntu 4.4.0 from the repo at [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) , it will no longer shut down my computer. After I click shutdown, it asks for my password. I type in the (correct) password, but then I get this:

```
Either the password you entered is invalid, or the system administrator disallows shutdown this computer with your user account.
```

It worked perfectly before, any ideas?

---

### Post by picpak on 2007-02-14
Well, it turns out that gdm will let me shutdown regularly; however, I'd rather not use gdm.

---

### Post by aidanr on 2007-02-14
you could try the suggestion in [this thread]("http://forum.xfce.org/index.php?topic=2890")

---

### Post by picpak on 2007-02-14
xfsm-shutdown-helper isn't anywhere on my system...:( 

Do they mean xfce4-session-logout?

---

### Post by picpak on 2007-02-15
Solved it!

1) Edit /etc/dbus-1/system.d/hal.conf

2) Change where it says

```
  <policy user="0">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>
```

to

```
  <policy user="your_username">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>
```

Put in your username where it says your_username.

3) Save and exit.

Now it shuts down no problem.

---


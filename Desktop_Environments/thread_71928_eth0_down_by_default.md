---
title: "eth0 down by default"
date: 2005-10-04
forum: Desktop Environments
---

### Post by Eleka on 2005-10-04
Hi people!
I want to do that the tittle says: configure the eth0 down by default, because very much times I want to start with othr interface (wlan0) or without any interface when I don't need internet at all.
How can I make eth0 and wlan0 down by default?
Note: Do you know some program or package that allow to put in the task bar a wireless reception graphic?

---

### Post by mlomker on 2005-10-04
> How to put in the task bar a wireless reception graphic?

Get a copy of [GTK wifi]("http://ubuntuforums.org/showthread.php?t=34645") if you are using gnome.

To keep the interfaces from coming up at boot:

```

sudo chmod 600 /etc/hotplug/net.ifup
sudo nano /etc/network/interfaces

```

Place a # sign in front of the **auto** commands that refer to the interfaces (leave **auto lo** in there).  Ctrl-W, Y, Enter to save.

---

### Post by Ampersand on 2005-10-04
If you add a network monitor to the gnome panel (right click on the panel, then 'add to panel') and set it to monitor syour wlan connection, it'll have a signal strength bar. You should also be able to use this to enable and disable connections.

---

### Post by Eleka on 2005-10-11
Hi!

I understood the part of editing /etc/interfaces ... but the first thing to do, this chmod ... what does it make?

I'm with the same problem, because sometimes, the /etc/interfaces is auto-edited and add auto wlan0 at the end. 

When I start the system, it take very much time in "Waiting for network interface to come up" .. How can I take out this task to the startup?

---

### Post by mlomker on 2005-10-11
> I understood the part of editing /etc/interfaces ... but the first thing to do, this chmod ... what does it make?

It disables hotplug for networking interfaces.

> "Waiting for network interface to come up" .. How can I take out this task to the startup?

You can press Ctrl-C to skip it.

---


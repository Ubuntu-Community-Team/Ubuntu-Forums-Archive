---
title: "Show network manager applet by command line"
date: 2011-09-14
forum: Desktop Environments
---

### Post by jBriche on 2011-09-14
Hi everyone,
I am actually running a Ubuntu 10.10 with gnome.
I have network manager applet running fine and can click on the icon in the notification area to show all networks.
Now I 'd like to do is to show this panel with the available networks, not with a click but with a command line.
I tried to dbus-monitor the click but nothin happens, also tried every executable delivered with network manager and nothing worked.
Do you know a way to do this?
Thanks
Julien

---

### Post by johnalexrob on 2011-09-14
What exactly are you trying to accomplish? Are you saying that you want to type a command and see the menu with the networks pop up or that you want to see the available networks from the command-line? If you want the latter, just type the command
```
 
sudo iwlist (device) scanning

```
where (device) is the network device. You can find that out from typing
```
 
ifconfig

```

---


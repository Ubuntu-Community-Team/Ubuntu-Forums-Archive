---
title: "Need a command line upnp client"
date: 2009-01-16
forum: General Help
---

### Post by jlrubin on 2009-01-16
I run Ubuntu 8.04.1. I am looking for a command line upnp client that will allow me to write scripts to enable and disable port forwarding on my router - a Linksys WRT-54GS.

---

### Post by jlrubin on 2009-01-17
bump

---

### Post by jlrubin on 2009-01-21
bump

---

### Post by choom on 2009-02-04
I have the same problem, can anyone help?

---

### Post by mb_webguy on 2009-02-04
MediaTomb is a command-line UPnP server, though it has a web-based GUI to set the shared directories (which isn't a problem as long as you have a web browser on a computer on the same network).  I don't know if it can handle scripts to disable port forwarding on your router, though.

---

### Post by choom on 2009-02-04
after a hour of googling i've found [MiniUPnP Project]("http://miniupnp.tuxfamily.org/") page, which is exactly what i was searching for. 
MiniUPnP client can be easily built from a tarball provided [here]("http://miniupnp.tuxfamily.org/files/")

---

### Post by 'ntoni on 2009-03-13
yeee, this tool just works.
After you compile it, by issuing:
```
make
sudo checkinstall
```
in the directory you've extraced from the tarball, found on miniupnp website, you can place this code in a file called aMuleLauncher, adapting wlan0 to your network interface's name, and 4668 and 4678 to your port numbers
```

upnpc -a `ifconfig wlan0 | grep "inet addr" | cut -d : -f 2 | cut -d " " -f 1` 4668 4668 TCP
upnpc -a `ifconfig wlan0 | grep "inet addr" | cut -d : -f 2 | cut -d " " -f 1` 4678 4678 UDP
amule

```
Next, you can change your system menu and point amule to this amulelauncher, and you'll have a working DHCP+UPNP port forwarding P2P download solution.

---


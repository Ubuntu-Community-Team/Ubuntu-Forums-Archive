---
title: "kbluetoothd.  Make it stop! (Solved)"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mlmurray on 2005-10-15
Does anyone know how to disable kbluetoothd in KDE?  

I don't have bluetooth on my laptop (Compaq X1000), yet this gets loaded up everytime I start KDE.  I wouldn't really mind but it seems to be trying to connect to something every 5 seconds and, when that fails, it writes to the '~/.xsession-errors' file.  Witness:
```
mark@mlmurray1:~$ tail -f .xsession-errors
kbluetoothd: Bind failed: No such device
Warning: more than one line!
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: No such device
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: No such device
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: No such device
kbluetoothd: HciSocket::open()
kbluetoothd: Bind failed: No such device
kbluetoothd: HciSocket::open()

```

Also, it loads the bluetooth kernel module.  I've tried blacklisting the module in hotplug to no avail.

Can anyone help?

Thanks!

---

### Post by mlmurray on 2005-10-15
Sorry everyone!  Found the solution myself!

I edited the ~/.kde/share/config/kbluetoothdrc file and changed the line that read "AutoStart=true" to "AutoStart=false".

Re-started the session and it was fixed.  Duh!

---

### Post by HermanAB on 2005-10-15
Thanks for that tip.  Most people in Europe really like Bluetooth, while it is universally ignored in North America. That causes some cultural issues... ;-)

---

### Post by scokar on 2005-12-18
[QUOTE=mlmurray]Sorry everyone!  Found the solution myself!

I edited the ~/.kde/share/config/kbluetoothdrc file and changed the line that read "AutoStart=true" to "AutoStart=false".

Re-started the session and it was fixed.  Duh![/QUOTE]

Thanks, solved my problem of have >2M a ~/.xsession-errors file.

I wonder where this is in the kde control panel ....

---


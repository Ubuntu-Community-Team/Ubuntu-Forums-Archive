---
title: "KDE Network Config"
date: 2022-06-26
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-06-26
Folks,

Recently installed 22:04 server, during installation a wifi connection was made and this worked fine on reboot after install.

I subsequently installed kde-plasma-desktop - this too went fine.

I cannot find anywhere any utility to alter network settings.  The original wifi is working but I have not found an option to change networks or alter current configuration.

Also, installed plasma-nm and it shows networks disconnected, no wifi access points are shown.  If I issue sudo iwlist scan 12 local wifi appear.

Anyone able to point me in right direction as to where current configuration is and how to get plasma-nm to list SSIDs?

Geoff

Ok, found /run/netplan/WPA-wlp2s0.conf

So found current configuration but still unsure why plasma-nm shows no connection and none available.

Geoff

---

### Post by Geoff_Lane on 2022-06-27
Slowly finding config files, this will enable me to alter via command prompt but still no obvious GUI for wifi editing.

I tried, using tasksel installing 'laptop' as this apparently installs some wifi tools.  plasma-nm still reports networks disconnected.

Geoff

---

### Post by ActionParsnip on 2022-06-27
Does the system move and does the WiFi work despite no icon?

---

### Post by Geoff_Lane on 2022-06-27
There is an icon but no option to scan or connect.  Message says network not connected but I am connected, can surf, terminal updates and install etc

Geoff

---

### Post by ActionParsnip on 2022-06-27
Does the system move or does it only connect to this network?

---

### Post by SeijiSensei on 2022-06-27
First, try running System Settings, then Configuration under Network. You should find what you need there. You can also bring up this application by right-clicking on the network icon in the tool bar and choosing Configure Network Connections.

If you have a wireless connection, click the wireless icon with the partial rings in the toolbar. You should see a list of all the networks available to you. If you click on the active connection and choose Details, you'll see things like the speed and signal strength.

---

### Post by Geoff_Lane on 2022-06-28
> **ActionParsnip said:**
> Does the system move or does it only connect to this network?

Currently it cannot move as I have no option (as yet) to set an alternative network.

Geoff

---

### Post by Geoff_Lane on 2022-06-28
> **SeijiSensei said:**
> First, try running System Settings, then Configuration under Network. You should find what you need there. You can also bring up this application by right-clicking on the network icon in the tool bar and choosing Configure Network Connections.

If you have a wireless connection, click the wireless icon with the partial rings in the toolbar. You should see a list of all the networks available to you. If you click on the active connection and choose Details, you'll see things like the speed and signal strength.

I have a wifi connection but the wifi icon on my toolbar is greyed out and says 'Disconnected'

If I go to the configuration option I can manually create a connection, apply it but no option appears to [B]connect

[/B]This is obviously connected in some way with my installing the server then adding the desktop rather than installing a desktop environment.

Geoff

---

### Post by Geoff_Lane on 2022-06-28
[B]SOLVED


[/B]Under /etc/netplan/[FONT=monospace][COLOR=#000000]00-installer-config-wifi.yaml I had my one and only wifi connection details, same as usually in wpa_supplicant.config

After backing up file I deleted contents and just entered these four lines (one is commented out);
[/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][B][COLOR=#000000]# This is the network config written by 'subiquity' [/COLOR]
network: 
  version: 2 
  renderer: NetworkManager[/B]

Rebooted and on reboot I now have the familiar wifi icon and can scan and connect as before.

I had previously installed plasma-nm which I guess is KDE's version of NetworkManager

Geoff

[/FONT]
[/COLOR]
[/FONT]

---


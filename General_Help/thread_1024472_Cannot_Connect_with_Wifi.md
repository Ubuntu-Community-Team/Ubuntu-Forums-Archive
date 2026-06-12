---
title: "Cannot Connect with Wifi"
date: 2008-12-29
forum: General Help
---

### Post by BigDaveyJ on 2008-12-29
Well recently (about an hour ago) I installed Ubuntu with Wubi on my new laptop, I have yet to be able to connect to my wireless connection. I need to be plugged in for it to work. I went to the help in offline Ubuntu and no help from that, and I have the SSID filled out correctly, the whole system should be working, but I don't know why it isn't. Any help?

---

### Post by nothingspecial on 2008-12-29
Do you know what wireless card you have?

If not type (in accessories > terminal) ```
lspci -v
``` and look near the bottom of the output. That will tell you then post it here.

---

### Post by BigDaveyJ on 2008-12-29
I am pretty sure this is what you are looking for.

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Right?

---

### Post by Seks on 2008-12-29
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

try the madwifi driver

---

### Post by nothingspecial on 2008-12-29
In your menus system > administration > hardware drivers
Disable the atheros driver in there. Then accessories > terminal and copy and paste 
```

sudo apt-get install linux-backports-modules-intrepid-generic
```

Then

 ```
sudo modprobe ath5k
```

to load the driver.

Then to make the driver load every time you boot
```

gksudo gedit /etc/modules
```

add this to the bottom of the file

```
ath5k
```

save
close
reboot

If that doesn`t work we`ll try madwifi.

---

### Post by nothingspecial on 2008-12-29
Oh and before you do that go to system > administration > software sources and make sure all the software in ubuntu software and the third party tabs are checked.

---

### Post by BigDaveyJ on 2008-12-29
This unfortunatley did not work. I followed the instructions to the dot, but did not work......

EDIT*** This was to the madwifi that didn't work. I did not see these.

---

### Post by BigDaveyJ on 2008-12-29
Ok, it connects now, but when I disconnect my ethernet cord, it says I am connected to the wireless, but it doesn't load anything.

---

### Post by 3rdalbum on 2008-12-29
Try pinging Google:

```
ping 66.249.89.104
```

If this works and you get pings coming back, then you need to go to the Network Manager applet in the top panel, right-click and choose "Edit Connections". Go to the wireless connection, select it and click Edit. In IPv4 settings, change it to "Automatic (DHCP) Addresses Only". Then enter the following address as your DNS Server:

208.67.222.222

If the ping command fails, then we'll need to try something else. BTW you can stop pinging by pressing Control-C or by closing the terminal window.

---

### Post by nothingspecial on 2008-12-29
Check my edited post above. I posted wrong, sorry. It`s 

```
gksudo gedit /etc/modules
```

I have modified the original post

:oops:

---


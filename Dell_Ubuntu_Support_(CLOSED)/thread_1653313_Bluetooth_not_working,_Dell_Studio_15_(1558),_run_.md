---
title: "Bluetooth not working, Dell Studio 15 (1558), run hid2hci"
date: 2010-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rackstar on 2010-12-26
Hi,

My Bluetooth has never worked for me on this laptop, however, I tried to have a go with it once more.

I found this on linlap: 
> 
For bluetooth, you may have to run the command &#8220;hid2hci&#8221; to successfully scan/use yoru devices (assuming you have the packages for bluetooth installed).


However if I just type hid2hci, it says "command not found". I did a search and found that I do have a hid2hci command in /lib/udev/ . But it needs parameters.

How do I fix this?

Thx!
Ruben

---

### Post by Rackstar on 2010-12-26
I also tried this 
> 
put "HID2HCI_ENABLE=true" to /etc/default/bluetooth


No changes.

EDIT: no sign of bluetooth in lsusb and lspci

---

### Post by anders_c_ on 2011-01-24
I'm also having this issue, none of the old fixes seem to work.

Edit: Wrong forum...mixed up the tabs and thought i posted in natty section, need coffee :P might still be the same fix though...

---

### Post by DJ DG on 2011-02-22
I'm having the same problem with the same computer (Dell Studio)

---

### Post by mrarm on 2011-08-24
I have same problem. I've tried to install BT drivers for Dell Studio 1558, also, I've tried to replace drivers manually.. My BIOS is up to date. 

BT stopped working suddenly, bluetooth icon and nm-applet stopped to show in tray. I must use wicd now (with nm-applet when I need to connect to new network).. I've tried many things from forums.. 

Bluetooth applet shows, that BT is off. DellWireless ctl show, that everything is going fine - but bluetooth and blueman says, that there is no adapters.

---


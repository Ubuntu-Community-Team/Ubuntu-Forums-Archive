---
title: "iwconfig WPA?"
date: 2009-02-28
forum: General Help
---

### Post by dragos240 on 2009-02-28
Okay i have a linksys connection with a WPA key, how do i connect to it?

---

### Post by thinking2loud on 2009-02-28
Manual method:
1) I'm assuming you have wpa-supplicant.  If you don't, you need it.
2) Open or create (as root) /etc/wpa_supplicant.conf  Here's what's in mine (edited for security reasons :)):
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="*YOUR_NETWORK_ID_GOES_HERE*"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="*YOUR_PRESHARED_KEY_GOES_HERE*"
        pairwise=TKIP
        group=TKIP
}
```
3) reboot

Automatic method:
Network Manager [nm-applet] or Wifi Radar have the ability to find and prompt you for the password for your network.  My albeit limited experience with both of them has been less than stellar.

---

### Post by dragos240 on 2009-02-28
> **thinking2loud said:**
> Manual method:
1) I'm assuming you have wpa-supplicant.  If you don't, you need it.
2) Open or create (as root) /etc/wpa_supplicant.conf  Here's what's in mine (edited for security reasons :)):
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="*YOUR_NETWORK_ID_GOES_HERE*"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="*YOUR_PRESHARED_KEY_GOES_HERE*"
        pairwise=TKIP
        group=TKIP
}
```3) reboot

Automatic method:
Network Manager [nm-applet] or Wifi Radar have the ability to find and prompt you for the password for your network.  My albeit limited experience with both of them has been less than stellar.

Okay so i think i have it, in the synaptic package manager, it says it's installed, although, in the "/var/run" directory there isn't a folder nor file named wpa_supplicant, although there is a folder called wpa_supplicant in the ect directory. Should i move it to the other directory? And should i create a wpa_supplicant.conf in the "/ect" directory.

---

### Post by thinking2loud on 2009-02-28
I think your next problem is that wpa_supplicant isn't running.  It creates the file named /var/run/wpa_supplicant.<foo>.pid when it's running (<foo> is the wireless interface name).  If you don't have a wpa_supplicant.conf in the /etc directory, make one.

---

### Post by thinking2loud on 2009-02-28
Actually, before we continue doing all this fancy stuff, I forgot to ask the dumb question.  If you turn security off on your wireless router, can you connect to it?  Are you sure your problem is WPA?

---

### Post by thinking2loud on 2009-02-28
And I found a new quality clue:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by dragos240 on 2009-02-28
> **thinking2loud said:**
> And I found a new quality clue:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Followed the guide didn't work, i get errors :(

---

### Post by thinking2loud on 2009-02-28
Back to 2 questions ago...

[LIST=1]
[*]Can you turn off security (temporarily) on the network?
[*]If you do, can you connect?
[/LIST]

---

### Post by dragos240 on 2009-03-01
> **thinking2loud said:**
> Back to 2 questions ago...

[LIST=1]
[*]Can you turn off security (temporarily) on the network?
[*]If you do, can you connect?
[/LIST]


I will try

EDIT: Nope, looks like my dad changed the password again, so i can't, but i'll wait for him and ask.

---


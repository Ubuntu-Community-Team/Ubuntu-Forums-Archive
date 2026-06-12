---
title: "IPW2200 and WPA.  Internet Connection"
date: 2006-01-16
forum: General Help
---

### Post by bennettg on 2006-01-16
Hello.  A big nOOb here just one step away from say Bye Bye to Bill Gates Forever, but I need help.


I am soooo close. I wiped my hard drive and did a fresh install of kubuntu/ubuntu. I followed luca_linux's instructions in post 1 of this the thread located at [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

Upon rebooting, I was connected!!!! The speed was much slower than in windows with wpa or in kubuntu with wep, but I was pleased.

However, since that time, I have only been able to connect wirelessly 1 out of 7 times. I wonder if it is something in my /etc/wpa_supplicant.conf file.

To help solve this probelm, I will post a picture of the wireless security settings from my router, and my /etc/wpa_supplicant.conf file. Does it have anything to do with TPIK? My WPA passphrase in ascii and i do not broadcast my ssid.

[IMG]/home/bennettg/Desktop/snapshot1.png[/IMG]

see attached snapshot





Here is my etc/wpa_supplicant.conf:


# Minimal /etc/wpa_supplicant.conf to associate with open
# access points. Please see
# /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
# configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
### Scans/ESSID changes can be done with wpa_cli
network={
ssid=""
key_mgmt=NONE
}

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="acorn"
scan_ssid=1
psk="24334B4A44412423486A736B61"
priority=2
}


If I can just get this to connect reliabily, I will delete windoze from my partitions. Bye Bye M$ and Bill Gates

---

### Post by matthew on 2006-01-16
My first thought is to change "key_mgmt=NONE" to "key_mgmt=WPA-PSK"

EDIT: I just noticed you have yours configured for 2 access points, one with no known ssid nor encryption (ie public) and the other for at home. That said, try commenting out the first entry (I can connect at public access points without needing one like yours) and modify your main one to have similar info to mine. MAKE A BACKUP FIRST so you can undo all the changes if you want/need to.

Perhaps someone else will echo in as well. Here's my wpa_supplicant.conf (with specifics masked)

```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="ssid_name_here"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP    
    psk="psk_value_here"
}

```

---

### Post by bennettg on 2006-01-16
[QUOTE=matthew]My first thought is to change "key_mgmt=NONE" to "key_mgmt=WPA-PSK"

EDIT: I just noticed you have yours configured for 2 access points, one with no known ssid nor encryption (ie public) and the other for at home. That said, try commenting out the first entry (I can connect at public access points without needing one like yours) and modify your main one to have similar info to mine. MAKE A BACKUP FIRST so you can undo all the changes if you want/need to.

Perhaps someone else will echo in as well. Here's my wpa_supplicant.conf (with specifics masked)

```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="ssid_name_here"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP    
    psk="psk_value_here"
}

```[/QUOTE]


I am such a noob.  Can you be more specific about which lines to comment out in the file I posted in the first post of this thread?

Does it matter if I am using a ascii passphrase (i.e. 8-63 characters) as opposed to a hexadecimal (64 characters)?  I tried to use the examples in the /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz file.

Also, why would the laptop have connected 1 or 2 times with the current /etc/wpa_supplicant.conf settings?

---

### Post by matthew on 2006-01-17
[quote=bennettg]I am such a noob. Can you be more specific about which lines to comment out in the file I posted in the first post of this thread?[/quote]Don't worry. I had trouble getting this the first time. We all start out knowing nothing.

I was specifically referring to this section```
 ### Associate with any open access point
 ### Scans/ESSID changes can be done with wpa_cli
 network={
 ssid=""
 key_mgmt=NONE
}
```To comment it out, just put a # in front of each line. Better yet, just backup your current file and start over like this:```
sudo cp /etc/wpa_supplicant.conf /etc/wpa_supplicant.conf_backup
sudo gedit /etc/wpa_supplicant.conf
```Once the file is opened, erase ALL the contents. Then put this in```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="acorn"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP    
    psk="24334B4A44412423486A736B61"
} 
```Save and exit. Reboot and see if it works.
[quote=bennettg] Does it matter if I am using a ascii passphrase (i.e. 8-63 characters) as opposed to a hexadecimal (64 characters)? I tried to use the examples in the /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz file.[/quote]My passphrase is ascii. I am using an Intel ipw2200b/g wireless and Linksys wrt54g router.
[quote=bennettg] Also, why would the laptop have connected 1 or 2 times with the current /etc/wpa_supplicant.conf settings?[/quote]Luck.

Other factors to explore include:

-we may need to update your wireless network firmware. luca_linux's howto describes installing both the latest firmware as well as the latest drivers. Hopefully you were successful in doing that so this shouldn't be necessary. We might try again if you are still having problems.

-Someone nearby may be using a wireless telephone that uses a similar frequency. When I lived in an apartment, whenever my neighbor got a phone call my wireless network went down.

-In my current house, when my wife uses the mircowave oven my wireless internet link can become intermittent, otherwise it is rock solid consistent--it will stay connected for days if I leave the laptop on.

---

### Post by bennettg on 2006-01-21
[QUOTE=matthew]Don't worry. I had trouble getting this the first time. We all start out knowing nothing.

I was specifically referring to this section```
 ### Associate with any open access point
 ### Scans/ESSID changes can be done with wpa_cli
 network={
 ssid=""
 key_mgmt=NONE
}
```To comment it out, just put a # in front of each line. Better yet, just backup your current file and start over like this:```
sudo cp /etc/wpa_supplicant.conf /etc/wpa_supplicant.conf_backup
sudo gedit /etc/wpa_supplicant.conf
```Once the file is opened, erase ALL the contents. Then put this in```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="acorn"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP    
    psk="24334B4A44412423486A736B61"
} 
```Save and exit. Reboot and see if it works.
My passphrase is ascii. I am using an Intel ipw2200b/g wireless and Linksys wrt54g router.
Luck.

Other factors to explore include:

-we may need to update your wireless network firmware. luca_linux's howto describes installing both the latest firmware as well as the latest drivers. Hopefully you were successful in doing that so this shouldn't be necessary. We might try again if you are still having problems.

-Someone nearby may be using a wireless telephone that uses a similar frequency. When I lived in an apartment, whenever my neighbor got a phone call my wireless network went down.

-In my current house, when my wife uses the mircowave oven my wireless internet link can become intermittent, otherwise it is rock solid consistent--it will stay connected for days if I leave the laptop on.[/QUOTE]


Matthew,

Thanks for trying to help.  I followed all your directions and I still cannot connect.  Is there something else I can try?  Is there some command I can enter in the terminal that would help you help me?  All of my formware and drivers are upto date.  Do I need to set a priority somehow?

Does this thumbnail help?

EDIT: ***I just had a thought.  Maybe the wpa_Supplicant is not running when I start up?!  Is there a way to tell if it is running from the command line?

Thanks

---


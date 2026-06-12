---
title: "Dyanmic WEP w/ knetworkmanager problems"
date: 2011-04-15
forum: Desktop Environments
---

### Post by Darth_tater on 2011-04-15
Hello, I am having a bit of a problem connecting to a dynamic WEP WiFi network.

----
```

Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0/wireless): access point 'MyUniversityWifiSSID' has security, but secrets are required.
Apr 15 11:39:31 MyComputer wpa_supplicant[1002]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0/wireless): connection 'MyUniversityWifiSSID' has security, and secrets exist.  No new secrets needed.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Config: added 'ssid' value 'MyUniversityWifiSSID'
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Config: added 'scan_ssid' value '1'
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Apr 15 11:39:31 MyComputer NetworkManager[943]: <warn> Key 'pairwise' and/or value 'WEP40 WEP104 WEP40 WEP104' invalid.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <warn> Error adding pairwise to supplicant config.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <error> [1302892771.84385] [nm-device-wifi.c:3023] build_supplicant_config(): Couldn't add 802-11-wireless-security setting to supplicant config.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <error> [1302892771.84517] [nm-device-wifi.c:3286] real_act_stage2_config(): Activation (wlan0/wireless): couldn't build wireless configuration.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): device state change: 5 -> 9 (reason 9)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <warn> Activation (wlan0) failed for access point (MyUniversityWifiSSID)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Marking connection 'MyUniversityWifiSSID' invalid.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <warn> Activation (wlan0) failed.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr 15 11:39:31 MyComputer NetworkManager[943]: <info> (wlan0): deactivating device (reason: 0).


```


I have googeled that specific error about the WEP line, and it *was* a bug at one time, but according to the bug tracker, it has been fixed.  Not so, me thinks.

So, does the specific error above look familiar and does anybody know of a way to fix it?

Thanks in advance!

---

### Post by Zorael on 2011-04-17
Have you tried [the GNOME network manager applet](apt://network-manager-gnome)? If it works and the KDE network manager plasmoid doesn't, then perhaps the bug has resurfaced and needs [reporting](http://bugs.kde.org).

If neither work then you could try setting it up manually, from a terminal. It's easy with WEP networks, not so much with WPA/WPA2 networks. You'd need to know one of the four hex keys and not the passphrase.

```
$ sudo iwconfig essid MyUniversityWifiSSID key [*n*] **HEXKEYHERE**  # replace *n* with the hex key's order number, 1-4. leave the [] brackets as is, making it [1]
$ sudo dhclient wlan0
```

---

### Post by Darth_tater on 2011-04-17
> **Zorael said:**
> Have you tried [the GNOME network manager applet](apt://network-manager-gnome)? If it works and the KDE network manager plasmoid doesn't, then perhaps the bug has resurfaced and needs [reporting](http://bugs.kde.org).

If neither work then you could try setting it up manually, from a terminal. It's easy with WEP networks, not so much with WPA/WPA2 networks. You'd need to know one of the four hex keys and not the passphrase.

```
$ sudo iwconfig essid MyUniversityWifiSSID key [*n*] **HEXKEYHERE**  # replace *n* with the hex key's order number, 1-4. leave the [] brackets as is, making it [1]
$ sudo dhclient wlan0
```



I have not tried the gnome applet... id rather not install *all* of the gnome dependencies for it.


and i have no idea what the wep key is... it's dynamically generated.

i have a wpa_supplicant.conf file that i know works (i am using it with my rooted nook).  Can you tell me how to disable network manager and just use a config file?

---

### Post by Zorael on 2011-04-17
> **Darth_tater said:**
> and i have no idea what the wep key is... it's dynamically generated.

Oh. I'm way out of my league here, then.

I can only suggest you try the GNOME applet or wicd. You can try to avoid some of the additional cruft by supplying **--no-install-recommends** to apt or **--without-recommends** to aptitude.

```
$ sudo aptitude install **--without-recommends** network-manager-gnome

$ sudo aptitude install **--without-recommends** wicd wicd-kde
```

---


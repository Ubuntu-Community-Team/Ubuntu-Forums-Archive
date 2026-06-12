---
title: "Kubuntu Wireless"
date: 2005-08-19
forum: Desktop Environments
---

### Post by BTJustice on 2005-08-19
I had a heck of a time figuring this out.  I am new to Linux and I hope other new users might use the search feature on this forum and find this.

This is how to get your wireless card (assuming it is found by Kubuntu already) configured to work in Kubuntu...

1) Click the SYSTEM icon and select HOME FOLDER.

2) Go to **/etc/network**.

3) Right-click once on INTERFACES and move your mouse pointer to ACTIONS and left-click on EDIT AS ROOT.  Type in the password you created for root.

4) At the bottom of that file, you will need to add (assuming you are using an Atheros Wireless NIC and your wireless router uses DHCP & WEP)...

auto ath0
iface ath0 inet dhcp
name Wireless LAN Card
wireless_essid *Your Wireless SSID*
wireless_key *Your Wireless WEP Key If Used*
wireless_channel *Channel Number Like 3*
wireless_mode *This Is Usually "Managed" With A Capital M And No Quotes*

So it comes out looking something like this...

auto ath0
iface ath0 inet dhcp
name Wireless LAN Card
wireless_essid FaMiLyWiFi
wireless_key 598235T0F463UB02FBI8F66F95
wireless_channel 3
wireless_mode Managed

Also, in the INTERFACES file, the last line at the bottom will say something like **map ath0**.  If it says something else, simply change the above example from ath0 to whatever it says.

Close the INTERFACES file (be sure you save it).  Log out of Kubuntu.  Reboot.  Log back in and it should be working.

---

### Post by SGC on 2005-08-19
It does not works for, see the screenshot.

Any ideas?

---

### Post by BTJustice on 2005-08-19
Yes, stop using KWiFiManager as it is junk.  As long as your wireless card was found correctly, the directions in the original post will work.

---

### Post by SGC on 2005-08-19
[QUOTE=BTJustice]Yes, stop using KWiFiManager as it is junk.  As long as your wireless card was found correctly, the directions in the original post will work.[/QUOTE]
 Thanks BTJustice for your help, I followed your instruction exactly and tried many other things but still I couldn't connect wirelessly to my router. So I decided to remove Kubuntu from my laptop, but I still using it on my desktop.

---

### Post by BTJustice on 2005-08-19
I wonder if you need to remove configs from KWiFIManager?  I guess it doesn't matter now, lol.

---

### Post by daller on 2005-08-20
What does "map INTERFACE" do?

"auto INTERFACE" is not smart to use - It will timeout (30s) under each bootup, if the wireless-essid is not accessable!

---

### Post by c0rderr0y on 2005-08-20
you could install wifi radar

---

### Post by BTJustice on 2005-08-20
daller: I am not sure what you are talking about.

c0rderr0y:  Someone has to have Internet first in order to downlaod stuff.  The directions in my original post should work.  I don't use KWiFIManager or any other program for wireless.

---

### Post by LabThug on 2005-08-20
[QUOTE=BTJustice]I had a heck of a time figuring this out.  I am new to Linux and I hope other new users might use the search feature on this forum and find this.

This is how to get your wireless card (assuming it is found by Kubuntu already) configured to work in Kubuntu...

1) Click the SYSTEM icon and select HOME FOLDER.

2) Go to **/etc/network**.

3) Right-click once on INTERFACES and move your mouse pointer to ACTIONS and left-click on EDIT AS ROOT.  Type in the password you created for root.

4) At the bottom of that file, you will need to add (assuming you are using an Atheros Wireless NIC and your wireless router uses DHCP & WEP)...

auto ath0
iface ath0 inet dhcp
name Wireless LAN Card
wireless_essid *Your Wireless SSID*
wireless_key *Your Wireless WEP Key If Used*
wireless_channel *Channel Number Like 3*
wireless_mode *This Is Usually "Managed" With A Capital M And No Quotes*

So it comes out looking something like this...

auto ath0
iface ath0 inet dhcp
name Wireless LAN Card
wireless_essid FaMiLyWiFi
wireless_key 598235T0F463UB02FBI8F66F95
wireless_channel 3
wireless_mode Managed

Also, in the INTERFACES file, the last line at the bottom will say something like **map ath0**.  If it says something else, simply change the above example from ath0 to whatever it says.

Close the INTERFACES file (be sure you save it).  Log out of Kubuntu.  Reboot.  Log back in and it should be working.[/QUOTE]
 If you're using the LiveCD, or just don't want to reboot your machine, you can issue (as root)

# ifdown ath0 (Or whatever your WIFI interface is called)
# ifup ath0

I had to do it twice, but that was after confusing my card with kwifimanager, YMMV.

Of course, this has to be after making your config changes ;-)

---


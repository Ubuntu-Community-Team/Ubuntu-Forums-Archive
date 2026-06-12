---
title: "Wireless Networks - Whole Process in Detail"
date: 2006-01-03
forum: General Help
---

### Post by sixtwoten on 2006-01-03
The Ubuntu Wiki is great for bits and parts information to get one kind or another of a wireless network. But exactly what do each of these things do and in what order should they be invoked and/or configured (or even why we invoke and/or configure them):

1. iwconfig
2. ifup or ifdown
3. /etc/network/interfaces
4. /etc/wpa_supplicant.conf
5. /etc/default/wpasupplicant
6. iwlist

The concept here is to create a shell script that can take three inputs: ssid, type of encryption, and encryption key. The script then connects to the network specified. To create this script, the author would need to know exactly what is happening behind the scenes so that the script can replace all the manual labor currently spent on conencting to wireless networks if the user is always on the move.

---

### Post by zoiks on 2006-01-03
1) Allows you to see and edit details of wireless connections.
2) Activates and deactivates network interfaces and possible other things (such as dhclient)
4&5) Allows some g-cards, that have no native linux drivers or no support for wpa in their drivers, to handle wireless WPA encryption.

---

### Post by sixtwoten on 2006-01-03
I have found a working solution to the problem of connecting with multiple networks. However, it is very time consuming, although very intuitive. All you have to do is change two files:

1. /etc/network/interfaces
2. /etc/wpa_supplicant.conf

**/etc/network/interfaces**
Have as many profiles as possible, but keep them commented out. Only keep one profile active, the one which you want to use.

**/etc/wpa_supplicant.conf**
You could have multiple instances of ssid and psk but commented out; only those are not commented which have the values for the network to connect with.

As you can see, there are just two files that need to be modified for multiple networks to work. Is there some way to automate this process? I have no experience with shell scripting so if anyone has a solution or advice, please respond.

---

### Post by sixtwoten on 2006-01-04
I also found out that with ifup or ifdown you can give your own config file with -i FILENAME instead of the default /etc/network/interfaces file:
ifup -i FILENAME wlan0 or ifdown -i FILENAME wlan0

The script could now be made so that it takes as input a config file name and then runs ifup with that file to connect to that network.

---


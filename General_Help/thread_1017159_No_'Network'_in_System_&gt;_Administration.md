---
title: "No 'Network' in System &gt; Administration"
date: 2008-12-20
forum: General Help
---

### Post by dezerith on 2008-12-20
I recently installed Ubuntu 8.10 using Wubi. It's all working perfectly except one thing - I can't seem to find the network manager to see which wireless access points are in range of my laptop. I have managed to connect to the internet but I had to do it manually from the Network Configuration thingy. Any help in finding out why there is no 'Network' option under System  > Administration would be appreciated.

---

### Post by StevenHarper on 2008-12-20
If you open a terminal and run

```
sudo nm-applet
```

Do you see a tray icon or any errors?

also does this help?
```
sudo /etc/init.d/networking restart
```

finally you mention its not in the menu

Should be (System | Preferences | Network Configuration)
If you make a new user and login with them: does it appear?

Steve

---

### Post by dezerith on 2008-12-20
nm-applet gives me an error saying Could not acquire the NetworkManagerUserSettings service as it is already taken.

sudo /etc/init.d/networking restart seems to have been successful although I have no idea what it did. Oh yeah, it reconfigured networking interfaces. Nothing seems to have changed though ...

I have System > Preferences > Network Configuration but it isn't the Network Manager which is what I need to scan for wireless networks in range when I'm out and about.

I noticed that when I click the network icon in the system tray it now shows me the wireless access points detected! Which is good, but still no network manager. Meh.

---

### Post by StevenHarper on 2008-12-20
Ok I want you too look for all processes that have the name **nm** in them

Open a terminal - enter

```
ps -ef | grep nm
```

I get this : what do you have?

```
root      6076     1  0 Dec20 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
steven    6547  6300  0 Dec20 ?        00:00:01 nm-applet --sm-disable
steven   10396 10375  0 00:30 pts/3    00:00:00 grep nm
```

---

### Post by Punisher660 on 2009-02-02
I am new to Linux/Ubuntu and I am having similar issues. I don't think my wireless NIC is installed properly, but how can I tell?
After running the last command you have posted, I get the following:

```


root      4915     1  0 Jan30 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
1000      5538  5234  0 Jan30 ?        00:00:06 nm-applet --sm-disable
root     12932  4904  0 08:23 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/run/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
1000     13680 13513  0 08:35 pts/1    00:00:00 grep nm
```

So can you tell me whats going on with my network?

---

### Post by romuald_geo on 2009-03-08
I have simillar problem. When I enter ```
ps -ef | grep nm
``` command i have output 
```
root      5351     1  0 14:15 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
romuald   5819  5607  0 14:16 ?        00:00:05 nm-applet --sm-disable
root      6516  5344  0 14:25 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-ath0.pid -lf /var/run/dhclient-ath0.lease -cf /var/run/nm-dhclient-ath0.conf ath0
romuald   6793  6767  0 14:37 pts/0    00:00:00 grep nm

```
Can it be solved?

---


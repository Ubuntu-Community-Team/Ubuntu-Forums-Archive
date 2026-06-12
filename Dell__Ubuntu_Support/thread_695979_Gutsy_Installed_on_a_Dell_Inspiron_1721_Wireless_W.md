---
title: "Gutsy Installed on a Dell Inspiron 1721 Wireless Working"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by ymmatt on 2008-02-13
After two days of diligent searching I've managed to get everything, that I care about, working on my Dell Inspiron 1721. I thought that by gathering all of the stuff that I needed to get this to work would save some people a lot of time.

This guide assumes that you have 7.10 installed and at least moderately working. It has been a while since I installed but I believe that this went smoothly. I did choose to use the restricted driver for my display, and it has been working fine.

**Wireless**
The bcm43xx firmware drivers did not work for me at all, and every solution that I found basically said that you MUST use ndiswrapper to get this to work.

I tried about 14 different things before I came across this post: [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")
Once I followed those instructions all worked well (even though I had tried other things)

The network-manager package never worked for my wireless, I actually removed the package, so I did the wireless configuration from the prompt, or by editing the /etc/network/interfaces file. For a public network it should look something like this:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet dhcp
wireless-essid networkName

```

If you plan on using WPA with your wireless this page is invaluable:
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

**MythBuntu(mythFrontend)**
I installed mythbuntu-desktop after all the hardware was working and noticed something interesting. MythFrontend would never start for me. It would freeze when looking for the database (I have a separate backend server that I was trying to connect to)

I found after some unting that this file wan't being changed properly by mythbuntu control centre ~/.mythtv/mysql.txt or (/home/user/.mythtv/mysql.txt)  I had to manually get in there and change the db password, as well as the IP address (it had 192.169.xxx.xxx instead of 192.168.xxx.xxx weird) I also commented out the DBType field. All of the other mysql.txt files (/etc/mythtv/mysql.txt and /usr/share/mythtv/mysql.txt) had the right info.

In the end the beginning of that file( ~/.mythtv/mysql.txt) looked like this:
```
DBHostName=192.168.x.x
DBUserName=mythtv
DBPassword=passwd
DBName=mythconverg
# DBType=QMYSQL3
```

Hope this helps at least one person.

---

### Post by K.Mandla on 2008-02-13
Moved to Dell support forum.

---


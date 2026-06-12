---
title: "Dell 700m Wi-Fi LED"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kareeser on 2008-11-29
Before I begin: The Dell 700m is not a model Dell officially supports Ubuntu on... at least, I don't think so.

Anyhow, Ubuntu installed great on the machine. Everything was installed correctly and appropriate drivers were found. Everything worked out of the box... even the SD Card reader. Sweet. Windows couldn't find four drivers. *thumbs up*

Only problem was the WiFi LED, which doesn't turn on when the wireless radio is on. One supposes the Dell drivers take care of that on windows... probably.

According to: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

I should install the linux-backports module... so I did:
```

uname -r //To find the kernel release
sudo apt-get install linux-backports-module-2.6.27-9-generic
...
sudo init 6

```

System restarted, LED light still wouldn't function. Except now, even though wireless networks could be detected, I couldn't connect to mine (WPA Protected). Weird.

So,

```
sudo apt-get remove linux-backports-module-2.6.27-9-generic
sudo init 6
```

All fixed. However, why didn't it work properly? I think I may have installed the backports module incorrectly, since I remember reading somewhere that I shouldn't install the "linux-backports-module-2.6.27-9-generic" package directly... hrm.

And... any help about the LED? :)

---

### Post by vubunt on 2009-12-29
Had the same problem on an ageing 700m that had outlived Windows/XP but got a new lease of life through Ubuntu 9.1.
Until you first create a connection with the wi-fi it displays all the characteristics of being dead.
However, if you use System/Preferences/Network-Connections you will see the wireless tab, and if you add the wireless information for a valid connection (eg. a valid SSID and the related Security information) then the wi-fi subsystem will magically come to life, at least in part: wifi connections work fine and if you click on the 'antenna' icon at the top right of the screen you get a list of wifi networks in range.
The Wi-Fi led seems quite erratic in it's on/off behaviour, it came on after first establishing a link but on reboot it does not work any more even though the rest of the wi-fi subsystem seems fine.
Of course, it's hard to see how you can convince yourself that the wi-fi is off - for example in flight - if the LED does not work!

---


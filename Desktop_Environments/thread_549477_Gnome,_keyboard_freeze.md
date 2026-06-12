---
title: "Gnome, keyboard freeze"
date: 2007-09-12
forum: Desktop Environments
---

### Post by rocketship on 2007-09-12
I have a problem that seems to be recurrent, but only when I am on my university wireless network.

NetworkManager will not be able to a connection, perhaps getting one and then losing it, and then the next thing I know the keyboard is dead.  I can interact with open windows (the mouse functions), but not type or open new windows.  I am unable to Ctrl-Alt into another terminal, or Ctrl-Alt-Backspace to restart X - though this is probably because the keyboard is unresponsive, not because of X.  Hitting the power button should initiate a shutdown, but does not.

I haven't been able to find any trace of this in the log files - can anybody help?  I've been running NetworkManager in --no-daemon mode to see if something happens, but I have yet to be able to identify any event.

I am running Feisty on a Dell M70 laptop with a Broadcom wireless chipset - using wpa_supplicant and the bcm43xx driver.

thanks,
RS

---

### Post by rocketship on 2007-09-12
Wow, sure is quiet in here.  

Ok, so the last message from NetworkManager (in --no-daemon mode) before the crash seems to always be:

```
NetworkManager: <information>   wpa_supplicant(8496): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
NetworkManager: <information>   wpa_supplicant(8496): WEXT: Operstate: linkmode=-1, operstate=5
NetworkManager: <information>   wpa_supplicant(8496): Associated to a new BSS: BSSID=00:14:1c:c8:27:80
NetworkManager: <information>   wpa_supplicant(8496): Associated with 00:14:1c:c8:27:80
NetworkManager: <information>   wpa_supplicant(8496): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 37 31 39 2d 37 00
NetworkManager: <information>   wpa_supplicant(8496): WPA: Association event - clear replay counter
NetworkManager: <information>   wpa_supplicant(8496): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   Activation (eth1) failed.
NetworkManager: <information>   Deactivating device eth1.
sendmsg(CTRL_IFACE monitor): No such file or directory
sendmsg(CTRL_IFACE monitor): No such file or directory
sendmsg(CTRL_IFACE monitor): No such file or directory
rmdir[ctrl_interface]: No such file or directory
```

Any clues?  I can't be the only person ever to have this problem?

---

### Post by rocketship on 2007-09-12
sorry, I realized the subject was misleading.

---

### Post by rvandam on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/network-manager/+bug/138969](https://bugs.launchpad.net/network-manager/+bug/138969) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You aren't perchance the same person who submitted [this]("https://bugs.launchpad.net/network-manager/+bug/138969") bug are you?

I've been having this exact problem for several weeks now ever since I upgraded from edgy to feisty and decided to finally search around for a fix.  Unfortunately, I can't find a fix, in fact I can only find 2 people (possibly one if you submitted the bug) who have had this problem.

Currently:  
Dell Inspiron 9300 laptop running feisty with Broadcom BCM4306 using bcm43xx driver and network manager

Previously: 
Edgy using bcm43xx driver and first wifi-radar, then wicd when I needed WPA (network manager was always too flaky to use)

Also, I have the exact same problem that this only happens on my university network.  I use two routers at work and one at home and I've never had a problem on any of those.  

There are dozens of routers sharing two different essid's at school and I've had a problem on every single router I've connected to all across campus.

The problem seems to go away late in the evening but that's probably just because the school routers get less flaky as fewer people are using them as so network manager doesn't have to repeatedly reestablish the connection.

The most interesting lock up happened today as I was typing, my keyboard somehow got stuck continuously sending the letter 'g' which I must have had pressed exactly as it froze.  So, just like you, I could interact with existing windows but not start any new processes and the infinite string of g's followed whereever i put the focus.

I am forced every time to do a hard reset which has led me to generally avoid using internet access on campus.  In fact, whenever I turn on my laptop I rush to disable network manager so that I don't randomly freeze while doing something important.

I have a feeling, due to the nature of the crash that this must may be more driver than NM related but then again, I used edgy with wifi-radar and later wicd for more than a year on the same laptop at the same university and never once had a problem like this.

---


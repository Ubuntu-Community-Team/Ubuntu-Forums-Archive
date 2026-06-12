---
title: "Managing Network Interfaces"
date: 2006-01-05
forum: General Help
---

### Post by sixtwoten on 2006-01-05
1. In my /etc/network/interfaces file I see two lines:
```
auto eth0
auto wlan0
```
What does "auto" actually do?

2. Also, what do the following lines do in the /etc/network/interfaces file?
```
mapping hotplug
script grep
map eth0
map wlan0
```

3. I have a USB wireless adapter installed and working. I want to make changes to the system so that during bootup only eth0 is activated; I want to activate wlan0 manually whenever I need it after bootup. What should I do for that to happen?

---

### Post by schilcha on 2006-01-05
[QUOTE=sixtwoten]1. In my /etc/network/interfaces file I see two lines:
```
auto eth0
auto wlan0
```
What does "auto" actually do?
[/QUOTE]
"auto" identifies interfaces that are brought up at boot
Here's the corresponding paragraph from interfaces-man-page:
> 
Lines  beginning with the word "auto" are used to identify the physical interfaces to be brought up when ifup is run with the -a option.  (This option  is  used by the system boot scripts.)  Physical interface names should follow the word "auto" on the same line.  There can be  multiple "auto"  stanzas.   ifup  brings  the  named  interfaces up in the order listed.


[QUOTE=sixtwoten]
2. Also, what do the following lines do in the /etc/network/interfaces file?
```
mapping hotplug
script grep
map eth0
map wlan0
```
[/QUOTE]
Can't really go into details with this. It has something to do with determining the name of the interface... (see man interfaces for details).

[QUOTE=sixtwoten]
3. I have a USB wireless adapter installed and working. I want to make changes to the system so that during bootup only eth0 is activated; I want to activate wlan0 manually whenever I need it after bootup. What should I do for that to happen?[/QUOTE]

remove the line "auto wlan0"
to activate the if, execute "ifup wlan0" (see man ifup for details)

---

### Post by sixtwoten on 2006-01-05
Thanx so much for your reply. It really helped me. Just to clarify things once more: if I comment out all occurences of "auto" in the interfaces file, the computer would not try to bring up any interface during bootup. But then I would have to bring these up manually after the computer starts.

---

### Post by hw-tph on 2006-01-05
Yes, you got it right. You will want to keep the loopback interface, lo, as auto since it provides local networking (which is essential).

You can also look into ifplugd (apt-get it). It will start your network whenever a cable is connected and gracefully bring it down when the cable is unplugged. Great for laptops and desktops alike.


Håkan

---

### Post by jimmychen on 2006-01-05
I already have "auto lo", "auto eth0", and "auto ra0" in my /etc/network/interfaces lines. They're all working fine except auto ra0.
But I can manually type "ifup ra0", and the network interface works properly.
I need to start the ra0 interface automatically at startup.
I'm booting with initng instead of init.
At boot it works with net/lo and net/eth0 but not with net/ra0.
Any help will be appreciated.

---


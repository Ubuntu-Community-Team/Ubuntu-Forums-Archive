---
title: "Dell Inspiron B120(etc) and the Wireless LED being used as a mail notifier."
date: 2009-11-27
forum: Desktop Environments
---

### Post by frubblezuck on 2009-11-27
I'm wondering...

I do not use wireless on this laptop. It either requires and external interface or mini-PCI card(which does not work due to a missing internal antenna) to use wireless.

I've recently downloaded kgmailcheck and set it up. There is a place for setting a command to activate an LED...can anyone think of a way to activate/deactivate this LED with command(dummy driver, on/off switch somewhere in /proc/sys/..., etc)?

I imagine some sort of dummy driver would have to be used...but I think it would be neat to be able to use this unused wireless active LED on the chassis...I'm not inclined to program, but I wouldn't mind trying to hack it up if I only knew where to start looking.

Just point me in a direction...thanks. I'm using Kubuntu 9.04.

---

### Post by Zorael on 2009-11-27
Depends on the wireless card, I think.

Just browsing through /sys/bus/pci, I found the entry for my wireless card (netbook), which had a "leds" directory. (Divine the PCI address via lspci or 'lshw -c network'.)
```
zorael@lethe:/sys/bus/pci/devices/0000:02:00.0/leds$ ls
iwl-phy0::assoc  iwl-phy0::radio  iwl-phy0::RX  iwl-phy0::TX
```
Now, my wireless led only tells me that wireless is active, not whether I'm associated, receiving or transmitting, so I imagine it should have been the "radio" one, as it's basically a led for the killswitch.

Each those had a **brightness** file in them, to which I tried piping **0**, but nothing happened. Perhaps it does for you?
```
zorael@lethe:/sys/bus/pci/devices/0000:02:00.0/leds/iwl-phy0::radio$ ls
brightness  device  max_brightness  power  subsystem  trigger  uevent
zorael@lethe:/sys/bus/pci/devices/0000:02:00.0/leds/iwl-phy0::radio$ cat max_brightness
255
zorael@lethe:/sys/bus/pci/devices/0000:02:00.0/leds/iwl-phy0::radio$ echo 0 | sudo tee brightness
[sudo] password for zorael:
0
zorael@lethe:/sys/bus/pci/devices/0000:02:00.0/leds/iwl-phy0::radio$
```
If it works, you'd have to create a script that toggles (or pulsates) the led, and tell sudoers that it should be able to be run with sudo without supplying a password.

---


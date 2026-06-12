---
title: "Wireless USB - no auto-start"
date: 2005-12-08
forum: General Help
---

### Post by danlo on 2005-12-08
Hello all,

Just jumped into Linux for the first time, and chose Ubuntu.  I have a Zonet ZEW2500P USB 802.11b/g that I got to work following this:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

and replace rt2500 with rt2570 for USB.  I actually got it to work; however, anytime I reboot the machine, the card would not show up under System/Network, and I have to manually run 

insmod rt2570.ko

So the device would show up, and then activate it.  Now I also followed the instruction to update /etc/network/interfaces file:

----
mapping hotplug
        script grep
        map eth0

iface rausb0 inet dhcp
wireless-essid BARRETTO
wireless-key s:<KEY>
----

What am I doing wrong here?  Thanks for any tips!

---

### Post by 23meg on 2005-12-08
Did you try adding rt2570 to your /etc/modules file?

---

### Post by mmusante on 2006-01-02
I have the same problem, and yes rt2570 is in the /etc/modules file.

Any other ideas?

---

### Post by mmusante on 2006-01-03
Well i have another clue as to what could be wrong. When i do modprobe rt1570 it says FATAL: Module rt2570 not found.


Could this be part of the problem?

---

### Post by rachii on 2006-01-03
i had this issue before too, and checking the wiki howto now it has been edited and so the information that was there before is not anymore, and im not on my computer, so cant give specifics.   but i copied the rt2570.ko file to /etc/networking/wireless?   not sure if that location is correct, but after that everything worked perfectly on startups

---

### Post by mmusante on 2006-01-03
ahah, it worked :)

In the tutorial i used it just said to stick it in a drivers folder under 2.6.12 when it should be in the net/wireless folder in the complete kernel directory 2.6.12-9 ... with all of the other wireless_device.ko files... 

Thankyou, i knew it had to be something simple.

---


---
title: "WiFi not working"
date: 2011-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mahendrakariya on 2011-08-21
I have Intel Centrino N-1000 wireless card.
When I check is the driver is loaded, I am getting this output.

```

lsmod | grep iwlagn
iwlagn                225129  1 
mac80211              267522  1 iwlagn
cfg80211              163232  2 iwlagn,mac80211
compat                 18253  5 iwlagn,mac80211,btusb,bluetooth,cfg80211
led_class               2633  2 iwlagn,compat

```

But still, it is not detecting any wireless connections. Any solution?

---

### Post by mikewhatever on 2011-08-25
How about the output of **rfkill list all**?

---

### Post by mahendrakariya on 2011-08-26
```

rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---


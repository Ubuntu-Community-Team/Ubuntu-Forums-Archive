---
title: "cannot put wlan0 to work"
date: 2006-01-06
forum: General Help
---

### Post by klineberger on 2006-01-06
So finally wlan0 appears in ifconfig. I can run iwconfig and network-admin to change all the config. The wireless network is 100% open, no WAP, no encription, DHCP is correctly set, but still I cannot access the internet with my USB wireless device, not even ping the router. The wireless device recognizes the available networks in the area, they use the same frequency band...

  However I get messages like:
Error for wireless request "Set Frequency" (xxxx):
    SET failed on device wlan0 ; Invalid argument
if I try to set the channel with iwconfig.:???: 

  I'm lost: does anybody has any idea, or knows any troubleshooting or FAQS section with a checklist? I'd be grateful: I'm moving to a new place and I need wireless; either it works or I use windows:sick:.

---

### Post by harisund on 2006-01-06
I normally do 

```
iwconfig wlan0 mode Managed essid <name_of_your_essid>
dhclient wlan0
```

I prefer this to the GUI.

If it works, you might be able to see list of wireless with
```
iwlist wlan0 scan
```

---

### Post by klineberger on 2006-01-07
That did it! Glory to halsund!!
  BTW, I have a friend in a High School who is considering introducing Linux all around, but he also had problems with wireless. If this also works for him, then Linux has a chance.

---


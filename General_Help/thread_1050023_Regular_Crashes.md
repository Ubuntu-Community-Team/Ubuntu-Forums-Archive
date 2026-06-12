---
title: "Regular Crashes"
date: 2009-01-25
forum: General Help
---

### Post by JamieKitson on 2009-01-25
Hi,

Over the last couple of days I have been having regular crashes. By this I mean my computer completely hangs, there is no response to any buttons or mouse and the caps and num lock lights flash together and I have to do a hard reboot. I have not been able to find anything useful in /var/log/ and the only real clue I have is this photo I took of the crash while I was using the terminal:

[[img]http://farm4.static.flickr.com/3110/3224426451_261ba23023_m.jpg[/img]](http://www.flickr.com/photos/jamiekitson/3224426451/)

With all the references to iw I'm guessing this looks like something to do with wireless, which could explain why I've only been getting this for the last few days while I've been at my girlfriend's house. Although coincidentally(?) I did do an apt-get upgrade the day or two beforehand. The only thing I've tried so far is to use the previous kernel, 2.6.27-7, which did not help.
```

jamie@jamie-laptop:~$ lspci | grep Wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

jamie@jamie-laptop:~$ lsmod | grep iw
iwlagn                113668  0 
iwlcore               105540  1 iwlagn
rfkill                 19364  2 iwlcore
led_class              13192  1 iwlcore
mac80211              253440  2 iwlagn,iwlcore
cfg80211               37136  3 iwlagn,iwlcore,mac80211

```
Any help or pointers much appreciated.

---


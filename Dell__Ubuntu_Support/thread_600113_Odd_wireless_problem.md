---
title: "Odd wireless problem"
date: 2007-11-01
forum: Dell  Ubuntu Support
---

### Post by doomgazer on 2007-11-01
I'm a newbie to ubuntu and rather new to the linux world in general, so please bare with me.

I've got a Dell Precision M70 with an Intel Pro/Wireless 2200BG wireless adapter. I'm having a really strange performance problem, but only on my home wireless AP.

My AP is a Linksys WAP54G running DD-WRT firmware v23. It is configured to hide the SSID and WPA-PSK using TKIP. When I connect to it, my download speeds are absolutely terrible (50-80kbit), whereas my upload speeds seem completely unaffected (around 700kbit). If I connect to my neighbor's AP who uses the same ISP, but has no encryption on it, I get full speeds.

Initially I thought it was something to do with the WPA, but I disabled everything and set it back to an open and unsecured wireless system with SSID broadcast on - no avail, still getting terrible download speeds.

I run a Windows 2003 server for DNS and DHCP, but I don't think that is the issue, as I tried my ISP DNS servers and it didn't change the situation. Is there some kind of compatibility issue with the DD-WRT firmwares and Ubuntu?

I should also point out that under XP, this laptop performed fine on the wireless end of things on this AP, and none of my other wireless PCs are having issues.

Any help will be greatly appreciated. Thanks!

---

### Post by saru411 on 2007-11-01
what program are you using to download? are the correct ports forwarded to the correct lan address? im unsure if i can help but im throwing out some of the issues common to bt users.

good luck

---

### Post by doomgazer on 2007-11-02
I haven't even gotten as far as trying to do anything on bittorrent or usenet - this is simply in a browser window to my ISP's speed test.

I usually see results around 5mbit download and 700kbit upload, whereas on Ubuntu I'm seeing about 50-90kbit download and 700kbit upload. It's definitelt a noticeable drop, even in regular browsing sessions.

---

### Post by doomgazer on 2007-11-04
Solved the problem - wasn't anything to do with my wireless - had the same issue wired in. Seems it was related to a Cisco 871 router I was using. Replaced it with a Netgear WPN824 and all is working wonderful again.

Not sure if it's a configuration problem on the Cisco or what, but that was the problem.

---

### Post by saru411 on 2007-11-05
I'm glad to hear you got it up and running properly.

cheers

---


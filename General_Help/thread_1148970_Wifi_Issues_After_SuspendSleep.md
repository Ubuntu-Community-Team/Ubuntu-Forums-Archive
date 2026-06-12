---
title: "Wifi Issues After Suspend/Sleep"
date: 2009-05-04
forum: General Help
---

### Post by TheStagesmith on 2009-05-04
Hey there.

I'm running Ubuntu 9.04 Netbook Remix on an Asus Eee PC 1000HE, recently clean-installed after running vanilla 8.10 for a couple months. However, in both of the versions I've run, I've had a problem when the machine comes out of sleep/suspend: it won't connect to a wireless network. It will detect them, it will even sometimes show signs of beginning to connect, but it will never actually connect to the networks. Coming from a full system shutdown/reboot, it works fine, and connects to even unknown networks in a matter of seconds. Any ideas on what's going on? Is it a driver issue (although I'm not inclined to think so since the 1000 series is at the top of the list of supported books on the UNR wiki)? Or is it a problem with one of my config files? (or for that matter, anything else that I haven't a clue about). 

Any help? Thanks. :)

} // close walloftext

---

### Post by HuckleSmothered on 2009-05-06
I had some similar issues. I never looked to intensely into it because once I switched to the wicd network manager everything works peachy. It seems to be a much more reliable network manager.

To get it, enter into a terminal prompt:
sudo apt-get install wicd

---


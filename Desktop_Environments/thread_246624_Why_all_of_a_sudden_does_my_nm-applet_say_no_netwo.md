---
title: "Why all of a sudden does my nm-applet say no network connections?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by orb9220 on 2006-08-29
Am connected and posting right now ath0 is enabled and connected to my default ssid but why all of a sudden does my nm-applet say no network connections?

Any help on this I am ready to give up on nm-applet because of past issue's and no one answering on these forums I guess no one new the answer's.

1) nm-applet on reboot would try to connect to an ssid of USOUTDOOR that was not as strong a signal as my default. And know matter how many times I connected to my default ssid and rebooted it would go back to the one I don't use why?

2) No way to remove ssid's from the list so it displays only one's you want again why?

3) When I run nm-applet in xfce instead of default gnome then it runs three instances of itself which is probally a xcfe issue but still can't an answer on it.

4) version 0.6.2 still in repos even tho 6.3 was released in june and 6.4 in july.

These are my beefs with this program, I kind of like it and want to continue to use it but I don't see anything being done in a hurry to improve or fix it.

Any help is greatly appreciated.

Well I went in and look at my gedit /etc/network/interfaces
and all of sudden these lines were added to bottom of file and I don't  know why?

I just commented them out and rebooted and blingo-blamo it worked. Am a  bit puzzled tho on how they got thier. 

iface ath0 inet dhcp
wireless-essid [www.personaltelco.net](www.personaltelco.net)

auto ath0

---


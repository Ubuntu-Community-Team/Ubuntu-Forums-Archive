---
title: "Wireless doesn't connect"
date: 2005-11-07
forum: Desktop Environments
---

### Post by samba on 2005-11-07
Hi, I'm having problems with my wireless connection since I upgraded to Breezy. First, my card is a D-Link DWL-650+, on a Dell Inspiron 8100.

OK here are three different situations that happen.

1) Suppose I use the usual Ubuntu network management. In my /etc/network/interfaces file, I set "wireless-essid any". Then, it works, but the network management changes my /etc/network/interfaces file for "wireless-essid blabla" where "blabla" is my wireless network essid.
PROBLEM 1: It takes forever at the network interface step at boot time: I have to use a ctrl-c to put the process in the background.
PROBLEM 2: It doesn't work after Suspend, I have to reboot or restart the interface, which takes forever again (so I can't use Suspend).

2) I installed Network Manager, and put "wireless-essid any" in my interfaces file. Then, the Network Manager applet sees my card and the wireless networks, but it just doesn't connect for some reason. If I set manually the essid using say "iwconfig wlan0 essid blabla" and then try to connect using the Network Manager applet, then it sort of connects but for like one second and then disconnect.

3) I can do everything manually and it works. Say "iwlist wlan0 scanning", choose a network, "sudo iwconfig wlan0 essid blabla" and "sudo ifup wlan0". 

So this is all very confusing. I don't really know what's wrong; obviously, my card works. But I would like to be able to use Suspend, and to use a graphical interface (like Network Manager which I really like) to manage my wireless connection. Also, it would be very nice if it didn't hang at boot time, which is quite annoying (it didn't do that with Hoary).

Anyone has any idea what the problem is? Sorry if my post is confused, that's because I'm confused myself at the moment... :-)

thanks
samba

---


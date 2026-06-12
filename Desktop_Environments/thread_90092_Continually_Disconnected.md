---
title: "Continually Disconnected"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Stambo00 on 2005-11-14
I'm using a Netgear WG311v2 wireless device that was automatically detected by Ubuntu which I am very happy about. Unfortunately I sometimes lose connection to the internet every second or thrid time I use my computer which can happen at any stage. My "Network Monitor" in my dock correctly shows that I have been disconnected but when I go into "Connection Settings" my wlan0 wireless connection is labeled as "active". Iv'e tried deactivating and then reactivating the connection but it doesnt work. Is there any other way to re-establish the connection through the terminal or something without having to reboot?

---

### Post by Ronbo on 2005-11-14
Same problem here using the D-Link DWL-G650, haven't been able to figure it out.  If you come up with a solution it would be appreciated if you could post the answer.

---

### Post by holiday on 2005-11-14
Although it's only a temporary fix for your problem,  you can restart networking with 

$sudo /etc/init.d/networking restart

But it sounds like you have flaky hardware - either receiver or sender - or perhaps an overloaded ISP.

---

### Post by Stambo00 on 2005-11-14
[QUOTE=Ronbo]Same problem here using the D-Link DWL-G650, haven't been able to figure it out.  If you come up with a solution it would be appreciated if you could post the answer.[/QUOTE]

I think I may have solved the problem! I came across a program called NetworkManager Applet 0.4.1 in Synaptic that claims to "keep an active network connection available at all times." When my connection seems to become lost I simply just click on the icon and reselect my network connection. It has worked amazingly every single time so far.

After downloading, open the applet by pressing both ALT+F2 and then typing in "nm-applet". 

P.S. Does anyone know how to make this applet automatically begin upon starting Ubuntu? :)

---

### Post by Stambo00 on 2005-11-15
The network applet seemed to only work for a day, untill the same problem started happening again. I found this link:

[http://ubuntuforums.org/showthread.php?t=78446](http://ubuntuforums.org/showthread.php?t=78446)

Has anyone been sucessful with any of these options for an extended period?

---

### Post by [2]BoxingFiend on 2005-11-16
visit [www.freeantennas.com](www.freeantennas.com)

i made an extender from a folger's coffee can, able to get 54megs at 3 blocks now

---


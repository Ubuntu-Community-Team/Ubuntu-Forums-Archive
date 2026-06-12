---
title: "Network problems withn Ubuntu"
date: 2006-01-29
forum: Desktop Environments
---

### Post by bathini on 2006-01-29
Hi Friends

I am having network problems with ubuntu. Basically, when I boot into Windows XP, I get connected to the network with no problems and get assigned to DHCP(IP). Now, when I boot to Ubuntu, I get to Network interface, and waits for a long time and then its says fail.  I log on without logging to  network and then I have to deactivate network setting by clicking the icon on the tray and then activate again, then  I do get connected to the network. When I go to the internet, connecting to a page is slow. However, when I stream broadband TV stations there is no problem.This never used to happen and connection to the internet was fast. Why is this happening ? Anyone knows?

Regards

Bathini

---

### Post by gruepig on 2006-01-29
I'm not sure if this is part of the problem you are having, but there are known issues with IPv6 if your router/ISP doesn't support it.

For Firefox problems, open Firefox, go to "about:config", and change "network.dns.disableIPv6" to "true".  Do you see any improvement?

---

### Post by bathini on 2006-02-01
Thanks Gruepig for getting back to me. I am at a University maybe behind university's firewall.  When I boot into XP everything is normal, the internet is connecting ok. However, when I boot to ubuntu network interface hangs and then it says fail. When I logon to Ubuntu, I have to disable and enable network connection. When I open any browser epiphany, firefox, mozilla, the internet is so slow to connect to web pages.However, when streaming tv broadband I am able to see the video with no problem. This is wierd for me. I will try to tweak firefox as you said.

Bathini

---

### Post by gruepig on 2006-02-02
If it's multiple browsers, it's unlikely to be fixed by modifying firefox.

Another long shot ... are you using the same DNS servers on the Ubuntu side as in Windows XP?

---

### Post by bathini on 2006-02-02
Yes I am using the same DNS servers from XP. 

Bathini

---

### Post by javaTard on 2006-02-05
I have the same issue. I am running 5.10 amb64. My kernal is 2.6.12-10.
I also hang and fail at  "configuring network interfaces" and then again at synchronizing clock to ntp ubuntu.org
When i get in, gaim will not connext and neither will x-chat. I need to go into networking, disable my wireless card, and re-enable. I began noticing a slower boot after I set up ndiswrapper for my wireless card in the laptop.

---

### Post by bathini on 2006-02-06
There must be something we tweaked somewhere, but where?? I wonder

Bathini

---

### Post by pompeyjohn on 2006-03-12
I had a similar problem - search on these forums for a thread with resolv.conf in the subject field. I have posted a solution that worked in there for me, and a few others have working solutions.

Hope that helps :D

---


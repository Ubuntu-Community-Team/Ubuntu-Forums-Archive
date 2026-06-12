---
title: "Windows borders, controls (minimize, etc.) broken"
date: 2017-03-24
forum: Desktop Environments
---

### Post by conualfy on 2017-03-24
A few days ago, I started having this very nasty bug: when it crashes, the borders of windows, the window controls and other things related to compiz (I think) started to not work any more. I do not know why, but it forces me to log-out/restart and in some point it will occur again (cannot find the connection). Not sure when this started as I used the Intel graphics for a while, and I only discovered it when I switched back to nvidia graphics, for better performance.
[COLOR=#333333][FONT=monospace]See the screenshot. If you have any solution, please tell, this is a nogo :(

[/FONT][/COLOR][ATTACH=CONFIG]274282[/ATTACH]

---

### Post by conualfy on 2017-03-24
It seems that it is a driver bug.

[COLOR=#111111][FONT=Ubuntu]compiz --replace

fixed it until the driver is bug free.[/FONT][/COLOR]

---

### Post by larsbjo on 2017-03-28
I'm having the same issue for some time now when resuming from standby and using the Nvidia driver on Ubuntu 16.04 ( currently using nvidia 378.13 ). The problem occurred when using an older version of the driver but I have tried upgrading and reinstalling the driver without luck. My solution has been to restart unity. It's rather annoying and I would really appreciate if anyone had a fix.

---

### Post by scriber on 2017-04-01
> **larsbjo said:**
> I'm having the same issue for some time now when resuming from standby and using the Nvidia driver on Ubuntu 16.04..... 

Interesting as I've had the same problem for a while now.

Started when I was losing wifi connection when resuming from standby, was restarting network manager each time, then I could no longer even get wifi to work, shows it was connected but wasn't, so I had to use my Ethernet connection from the Netflix/TV, to bypass the annoying no wifi problem, then I noticed the corrupted screen thing when resuming from standby.

Have to reboot to fix. So annoying that I'm rarely using Ubuntu now until I get time to troubleshoot it. :(

I had zero problems with all of this until an update seemed to have broke this, and I've noticed a lot of people are having similar problems.

EDIT: Just changed the Nvidia driver from V375.39 to the Nvidia Binary Legacy driver V304.135 and no more screen corruption from standby, I'll have to test more to see if it's broke or changed other things, but it's a good start for me.

EDIT2: Well that was a bust, would crash the computer on shutdown/Restart, Have gone back to 375.39, guess I'll have to not use suspend until I can figure this out. Just for info, I'm using a Nvidia 650Ti

EDIT3: So after trying all the Nvidia drivers I am still having the problem with graphics corruption on minimized screens when coming out of Standby mode. Makes it impossible ( for me ) to use Standby, I have to reboot the system otherwise.
If I could revert back to a previous system setting before an update broke this I would, and maybe that would also give me back the WiFi connection I also lost at the same time.
I don't know if it's even possible to do that, or if so, how to do it.

---

### Post by biologicalneuralnet on 2017-04-09
Are there any updates on this? I'm using the Nvidia driver version 375.39 and didn't play around with other driver versions yet.

---

### Post by scriber on 2017-04-09
Yes, install the new Nvidia driver 3.81.09

Totally fixed the issue for me finally !

---

### Post by biologicalneuralnet on 2017-04-10
Great, thanks:) I'll have to try it out when I have more time at hand as it might affect my CUDA setup as well.

---


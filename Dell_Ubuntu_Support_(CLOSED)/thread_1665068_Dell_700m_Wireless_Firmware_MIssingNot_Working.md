---
title: "Dell 700m Wireless Firmware MIssing/Not Working"
date: 2011-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by superboy321 on 2011-01-11
Total Newbie Here. 
I just installed ubuntu 10.10 
Everything seems to be working fine except the wifi. Seems that I do not have the drivers installed. Tried going to systems-drivers to add but no luck. 

I did some digging around and found the drivers here [http://ipw2200.sourceforge.net/firmware.php. ]("http://ipw2200.sourceforge.net/firmware.php")

Now I downloaded it, but my questions is how do I install the drivers onto ubuntu? 
Can somebody give me a detailed instructions on how to install it? Thanks

---

### Post by mikewhatever on 2011-01-12
Why do you think you have an Intel wireless 2200? Anyway, that card has been reported to work out of the box since about 2005. You can verify the model by looking at the output of the following command:

```
sudo lshw -C network
```

---

### Post by superboy321 on 2011-01-12
My mistake. You are right Mike. I typed in the command and I got this:
BCM4306 802.11b/g Wireless LAN Controller
Vender: Broadcom Corporation

---

### Post by mikewhatever on 2011-01-13
Ok, the System->Drivers utility requires an internet connection to work. Any chance you could plug in a cable and re-run it?

---

### Post by superboy321 on 2011-01-16
Great! It Worked! I connected to the internet through the ethernet port and ran the systems utility and it found the drivers for Broadcom wireless. It automatically installed the drivers and now my Dell 700m recognizes my wireless connection!

---

### Post by ufmurphy on 2011-03-20
Hey guys,

I have been through the same deal with Ubuntu 9.10 and never got it remedied, For some reason the dviers utlility says I have no proprietary drivers in use, When I am also using a Dell m700 with a wireless card:

Intel PRO/Wireless 2200-BG

Stumped. 

Can anyone out there help?

Many thanks,

Jim

---


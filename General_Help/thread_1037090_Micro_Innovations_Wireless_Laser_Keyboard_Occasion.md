---
title: "Micro Innovations Wireless Laser Keyboard Occasionally Erratic"
date: 2009-01-11
forum: General Help
---

### Post by Tweak1029 on 2009-01-11
EDIT: This is 8.04 by the way.

My keyboard will occasionally send two keypresses or none at all for each keypress and my mouse occasionally gets jumpy (not extremely sensitive) and slows down.  I've noticed that when uploading, it's prone to doing this.  Gmail attachments, torrents, DCC on irc, sending files to friends through Pidgin/yahoo, etc., they all make it do it.  Other times, it seems to do it without cause.


Details:
Keyboard/Mouse Model Number: KB1045LSR

```

$ lsusb
Bus 005 Device 002: ID 03f0:2504 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
**Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd** 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 001 Device 001: ID 0000:0000 
```

Emboldened line seems to be the most likely candidate; HP is my printer and Plantronics is my headset, thus Sunplus is presumably my wireless receiver, since out of my four USB slots, one of them is empty.

My wireless internet card is a RaLink RT2500.
```

$ lspci | grep RaLink
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

To be frank, I don't know what information is necessary because I have no idea what exactly is causing it.

I googled around a bit and found some similar issues, like this one: [http://forum.mandriva.com/viewtopic.php?t=94863&sid=9a9df19d5aec55f556c9fa2c8cead941](http://forum.mandriva.com/viewtopic.php?t=94863&sid=9a9df19d5aec55f556c9fa2c8cead941)

---

### Post by Tweak1029 on 2009-01-21
Consider this a bump.

---

### Post by TheLions on 2009-01-21
im not an expert, but maybe wireless keyboard and wireless LAN card are interfering and jamming each other! if you can change the channel on your keyboard or on your router/AP

---

### Post by Tweak1029 on 2009-01-21
> **TheLions said:**
> im not an expert, but maybe wireless keyboard and wireless LAN card are interfering and jamming each other! if you can change the channel on your keyboard or on your router/AP
Crap.  You're right.  I had thought that they might operate on different frequencies. IEEE 802.11b/g are the only two available to me, and they both operate on 2.4 GHz with my keyboard and mouse. I'd guess that my downstream is sent using a slightly different frequency than the upstream is, which is what causes the interference.

Although that wouldn't quite explain why, when doing cpu intensive tasks, I get the same interference.  I have a hypothesis, but I'd rather let someone else offer a solution/suggestion for that before spewing crap on a public forum :P

Thanks.

EDIT: [s]Finding a channel that'll work.  Some work better than others, so I may be able to solve my problem.[/s]  Still having upload problems.

---


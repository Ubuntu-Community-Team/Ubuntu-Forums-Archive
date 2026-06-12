---
title: "Kubuntu and my modem"
date: 2005-04-16
forum: Desktop Environments
---

### Post by turtle_07 on 2005-04-16
I'm going to start off by saying that I have a very nice US robotics modem that has worked under other linux distrobutions. 

I've been using ubuntu on an old bad computer and have been amazed at how well it's been running, so I decided to throw it onto a computer that would be using 56k. I decided to try the livedisk first, just to make sure that the modem would work.

This ([http://www.bcpl.net/help/linux/](http://www.bcpl.net/help/linux/)) is how I get online, so I open up KPPP, and it tells me that /etc/resolv.conf doesn't exist and that I just need to create it. So I do. After that when I tell KPPP to query my modem, it can't find it, /dev/modem doesn't have any information I guess. Luckily KPPP can point to every single one of my /dev/ttyS#'s, so I'm not that worried. This is what happened with the last distro. But pointing to each one of those (0-4) everytime I try to query the modem it gives me a "modem busy" message.

Any idea what I need to be doing? I really want to use ubuntu, as I like it a lot and currently the livecd is outperforming whatever I have currently installed on there.

Thanks.

Edit: Should be pointed out, that before I did "ln -s /dev/ttyS4 /dev/modem" every single time I chose a ttyS# it gave me unable to unlock modem, after that every single one became "modem busy".

Edit #2: I found a thread where someone had a similar problem.
> 
Install setserial

lspci

sudo setserial /dev/ttyS4 port 0x#### irq # uart 16550A


(you get # from lspci) 

that was the response

Here's my lspci after I install setserial (on the liveCD):

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r
ev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia a udio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 139 4) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:04.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Et hernet 10/100/1000Base-T Adapter (rev 13)
0000:01:0a.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 0 1)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 96 00]
0000:03:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Se condary)

There's the modem, where's the o.x#### irq #?

---

### Post by Paki on 2005-04-26
I have the same problem, and the solution you're trying hasn't worked for me. In an attempt to organize the afflicted so that we can get something done, the most recent discussion appears to be here:

[http://ubuntuforums.org/showthread.php?t=29829](http://ubuntuforums.org/showthread.php?t=29829)

Good luck!

- Paki

---


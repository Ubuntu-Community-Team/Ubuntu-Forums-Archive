---
title: "Dell Mini 10v Ubuntu 9.10 Questions"
date: 2010-04-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TerminalClient on 2010-04-11
Hey all,
Just a couple of quick questions.  You'll probably laugh at this, but here goes.
I got a new Dell Mini 10v about a week ago, loaded Ubuntu 9.10 onto it (it came with 8.04), and after sorting out the proprietary Broadcom STA drivers for the wireless, everything has been working fine.  I have been connecting to the net and all is working fine.   
I did iwconfig in the terminal and it reads:

lo        no wireless extensions
eth0    no wireless extensions
eth2    IEEE 802.11  Nickname:""
          Access Point:  Not Associated

Now forgive me if I'm wrong but shouldn't this have printed info on the router I'm connected to?
Also, I've only had the laptop a week, but when battery is fully charged it only registers as 96.4%, the system says it's fully charged but the capacity is only 96.4%.  Is there a way of recalibrating battery, or getting the system to realize it's 100% cause it's a brand new battery?
I've added screenshots of the Terminal, Broadcom STA driver info and battery status.
If you need more information I can post whatever you need, thanks in advance!

---

### Post by aysiu on 2010-04-11
I don't have a Dell Mini 10v, but I do have a Broadcom 4312 in my HP Mini 1120nr, and I'm using the STA driver.

Same deal: ```
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
``` Not sure why that is, but I'm not having any trouble connecting to networks.

---

### Post by latticeguy on 2010-04-11
I see this behavior too on my mini, but somehow wicd (a nice program worth installing) does show the essid.  On my eeepc I used iwconfig to find out if I was at home or not in scripts.  The only way I've figured out to do this on my mini is to use arp, but that is kind of slow in responding.  Does anyone know a fast way to find either the essid or the router mac address in a script?

---

### Post by latticeguy on 2010-04-20
I tried "sudo iwconfig" and it gives much more info.  Apparently an ordinary user isn't supposed to know about the wireless configuration.  My scripts are back to what they were with a few "sudo"'s inserted.

---


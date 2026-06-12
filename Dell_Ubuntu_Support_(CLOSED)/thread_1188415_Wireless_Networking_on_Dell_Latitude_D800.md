---
title: "Wireless Networking on Dell Latitude D800"
date: 2009-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kencrest on 2009-06-15
Hello,
I have a Dell Latitude D800 with a clean install of Ubuntu 9.04 running. I can't get wireless networking to run. I have a wireless Broadcomm Chipsett / 1350. 

What do i need to install in Ubuntu to make wireless networking run? I'm new to Ubuntu. Step by step instructions would be appreciated.

Thx!
Ken

---

### Post by coffeeaddict22 on 2009-06-19
Hi Ken, 
Welcome to Ubuntu!
There's a number of causes for networking not working.  Start by opening a terminal, Applications/Accessories/Terminal, and type in the following commands.  The output will tell you a bit about what's happening; if you need more help, cut and paste it back here.
If you want to know more about the command, type into the terminal ```
man xxxx
``` where xxxx is the command you're interested in; you'll find the man page, which is often a little esoteric but you get used to the style of writing. 
```
lshw -C network
lspci
nm-tool
```
should give you enough information to start with.  Have a look at [this wiki page]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") although some of the commands are deprecated (= no longer used).
Post back if you want more help.

---

### Post by ugm6hr on 2009-06-19
Most likely, if you plug into a wired ethernet port, and then reboot, you should find the drivers available in:
System -> Administration -> Hardware Drivers

---

### Post by kgr132 on 2009-06-19
Ditto ugm6hr's answer. That's exactly what I had to do with my D830. Once you've got the proprietary drivers via the wired connection, you can enable them for both the video and the wireless card.

---


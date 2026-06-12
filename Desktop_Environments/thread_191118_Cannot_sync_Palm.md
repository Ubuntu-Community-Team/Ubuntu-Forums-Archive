---
title: "Cannot sync Palm"
date: 2006-06-07
forum: Desktop Environments
---

### Post by fdimmling on 2006-06-07
Hi,

Syncing the my Palm Tungsten E via USB with JPilot or Pilot applet which worked flawlessly in Breezy seems to be broken after installing Dapper on my travelmate 4652. The palm is recognized as visor on /dev/ttyUSB0 and /dev/ttyUSB1 according to /var/log/messages. But neither JPilot nor the pilot applet get any connection. Both stay waiting for data.

Any one got his palm already synced?

Friedrich

---

### Post by CybaCowboy on 2006-06-07
Yeah, I'm [having the same problem]("http://www.ubuntuforums.org/showthread.php?t=189400")...

---

### Post by wastrel on 2006-06-08
gpilotd is broken in dapper - here's the bug:

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

Are you testing with jpilot using the same port you have configured for the pilot applet?  This won't work - gpilotd will block jpilot from accessing the port.

Either remove the pilot applet and kill gpilotd, or move jpilot to a different port.

jpilot works fine for me, as long as gpilotd isn't running.  

gpilotd is working better since I installed the test fix packages on the bug thread linked above, but it sometimes takes 3 or 4 tries to get a successful sync.  using jpilot until gpilotd is fixed would probably be easier.

---

### Post by fdimmling on 2006-06-08
[QUOTE=wastrel]
jpilot works fine for me, as long as gpilotd isn't running.  
[/QUOTE]

Encouraged by your posting I tried jpilot again - and it worked - ONCE. I have the same behaviour as before: Whe I press the HotSync button of the Palm and then the JPilot button, the message appears: "Now press the HotSync button on the Palm". If I press the JPilot button before pressing the Palm buttom no /dev/pilot exists since it is linked at the time the Palm connects. The Palm is not always connected to the same /dev/ttyUSBx

Friedrich

---

### Post by lulucamargo on 2006-06-22
If you press the first the palm hotsync button and then the J-Pilot hotsync, it works. Sometimes, though, the first time I click the j-pilot button right after, it doesn't work - but then if I wait a couple of seconds and click again, it works.

---


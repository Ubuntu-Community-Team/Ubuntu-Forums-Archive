---
title: "strange network manager problems"
date: 2006-09-15
forum: Desktop Environments
---

### Post by pinegreen on 2006-09-15
When I installed ubuntu, I also switched from default network system to network manager and it worked fine, but since I couldn't convince it to have per wireless static network IP, I deinstalled it and cooked something up using whereami, ifplugd, etc. 

Now I got fed up with that again and I tried to reinstall network manager, removing ifplugd and whereami packages and now it doesn't work anymore, so I must have broken something. So, what happens is that when I plug in a cable it tries to get a DHCP off it, it gets it (basically ifconfig shows the address, I can connect to google, etc.), but this information somehow doesn't get to the manager so after some time it gives up and disconnects... Same with wireless, it connects succesfully, internet works, but applet still shows the rotating dots and times out and disconnects on time-out. When it connects, ifconfig and iwconfig show the normal info, but showing connection info on the applet shows just zeroes, so obviously aplet doesn't know that it   had connected and therefore it gives up after a while.

I tried reinstalling all packages that have dbus, hal and network-manager and it still doens't work. I created a test user and tried applet in there on a fresh desktop and still no cigar. 

Any ideas?

---

### Post by n1xt3r on 2006-11-14
Have you tried reinstalling dhcp3-client? There could be some rogue scripts lying around /etc/dhcp3/dhclient-{enter,exit}-hooks.d causing the problem. Don't just reinstall dhcp3-client, manually remove those rogue scripts if you have to.

---


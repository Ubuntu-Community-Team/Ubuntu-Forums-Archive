---
title: "wierd problem with internet connection!"
date: 2006-01-16
forum: General Help
---

### Post by Age One on 2006-01-16
hi. I have just installed 5.10, and I'm having a very wierd problem with my internet connection. 

my machine is on DLS (qwest) it isn't behind a firewall. its the only machine on the network at this time. it isn't set up to block any IP or websites and its using DHCP

problem is, SOMETIMES when I try to visit a site like google it will just wait and say its loading, then it times out. it also does this while using apt-get. I though it was a problem with the connection so I tryed pinging google, while at the same time using the browser to visit google. ping results come back good, but the site still times out. 

its getting very annoying, as I'm trying to configure this install and seemingly at random the internet connection is working and not working. 

Thanks

---

### Post by cuda70383 on 2006-01-16
(sorry for the double post as i moved my issue to the networking thread)

hi:
i guess i'm in good company as i'm having the same issues.

when i installed ubuntu the first time my wireless worked right out of the box.  the built in wifi card was seen as wlan0.

after the laptop died, i decided to do a dual boot with xp w/the new lappy.  when i reloaded 5.10 it didn't automatically connect to the internet.  i can ping my router and google, but it times out just like yours.

don't know if it means anything, but my card is now seen as eth1, whereas before it was seen as wlan0.

i get a signal strength of 100%.

any ideas would be greatly appreciated!!!

---

### Post by Henrythewound on 2006-07-11
You have probably found your answer by now, but I just got Qwest DSL and had a similar problem. I dont understand all the ins and outs of DHCP/ how routers work, but I'll bet the problem lies in your /etc/resolv.conf file. Go into a terminal and type

sudo gedit /etc/resolv.conf

I'll bet the first DNS address is the router's IP, not the DNS address it should be. You need to find out what your DNS addresses are (go to 192.168.0.1 in a browser and look under "Setup/configuration" and then the "Status" tab. Your DNS addresses should be listed there. 

The next problem you will run into (if you are like me) is that the resolv.conf file will be restored to the wrong version upon deactivation of your ethernet connection or restart of the computer. I am currently looking into how to resolve this issue. Good luck

Wound

---


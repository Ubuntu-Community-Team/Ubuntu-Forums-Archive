---
title: "Internet disconnecting"
date: 2005-12-20
forum: General Help
---

### Post by Nickoladze on 2005-12-20
for some reason, my internet completely disconnects after 10-15 minutes of being logged in and the only way i can reconnect is to reboot my computer. firefox, etc. shows that its not connected but the connection properties window always shows the signal strength with at least 95% (im on a wireless connection). I've never had this problem with windows on this computer so the router and signal is fine so it must be linux

---

### Post by Lambert on 2005-12-20
Post output of this command here.

```
iwconfig
```

---

### Post by professor_chaos on 2005-12-20
can you ping?

---

### Post by Nickoladze on 2005-12-21
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:CA:D0:AC
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-57 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

my connection seems to be fine today though, odd

---

### Post by Lambert on 2005-12-22
Hope it continues to work for you.

My initial thought was power management, maybe the card was being put to sleep. Your output shows powermanagement off though.

If the problem comes up again run the same command and look at the power management line.

---

### Post by Nickoladze on 2005-12-29
it cut out a few more times but i forgot to run the command, but i remembered this last time:

```
eth1      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:CA:D0:AC
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-57 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

the only difference is that the noise level is way way up

---

### Post by Lambert on 2005-12-30
Have you tried using a different channel? Sometimes radio interference can cause connection problems? (wireless is on the 2.4ghz frequency which is a very crowded spectrum. When I do a scan I find 6 devices but none of my neighbors run wireless routers so I still haven't figured out what items are being picked up)

>  Noise level
              Background noise level (when no packet is transmitted)

I also had to buy new phones as it caused me interference and dropped connections. No problems since then.

---

### Post by cwmccabe on 2005-12-30
I have a problem that may or may not be similar.  I'm running Ubuntu 5.10 on a Toshiba L25-S119, using a Netgear WGR614.v3 wireless router.  I've found that my wifi connection is smooth almost all the time, *except* when I try to view certain websites in a browser.  When I view these websites (ex. tvguide.com), whappo, my router stops communicating not just with my computer but with all the computers that are currently connected to it (both Windows and Linux).  I can see that the router is still running because Connection Properties shows that the signal strength is still high, but it just won't communicate with any connected computers.  When I view the same websites from a Windows machine, there is no problem.

What router are you using?

Have you confirmed that the pattern of disconnection is with the time you've been logged on (10-15mins)?  Is it possible that there is any other correlated factor?

Also, for me I don't need to restart het computer to get it running again.  Once I power-cycle the router, I can just open System > Administrtion > Network Settings and Deactivate then Activate the wireless connection.  You might see if that works for you.

Do you need to power-cycle your router as well to regain a connection, or just your computer?

---

### Post by Nickoladze on 2006-01-06
linksys router

no its not at a specific times, its really varied

and ill try deactivating and reactivating next time

edit: it just cut out and deactivating and reactivating doesnt fix it

---


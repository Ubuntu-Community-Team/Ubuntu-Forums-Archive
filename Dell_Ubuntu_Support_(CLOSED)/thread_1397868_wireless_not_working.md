---
title: "wireless not working"
date: 2010-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dukehunter1 on 2010-02-03
I just did a fresh install of 9.10 from a live DVD on my Dell Inspiron 15.  I turned it on and now I don't have any wireless support.  I pulled up a terminal and checked iwconfig and my wireless card isn't even listed.  This is bad news and I could use any help asap.  Thanks.

---

### Post by lidex on 2010-02-03
Start here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
more:
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

---

### Post by bobcollard on 2010-02-03
> **dukehunter1 said:**
> I just did a fresh install of 9.10 from a live DVD on my Dell Inspiron 15.  I turned it on and now I don't have any wireless support.  I pulled up a terminal and checked iwconfig and my wireless card isn't even listed.  This is bad news and I could use any help asap.  Thanks.
In your menu bar open System and find Hardware Drivers.  You will need an Internet connection like Ethernet to download the driver.  After an install and reboot you should be able to find Wireless setup by right clicking the Internet Icon in your task bar.

---

### Post by cjminton on 2010-02-03
If you can hard wire the laptop to the internet momentarily I would try installing and using WICD. I had lots of problems with the default network manager in Ubuntu and just by replacing it with WICD it solved everything.

```
sudo apt-get install wicd
```

---

### Post by mesuhas_sit on 2010-02-04
I also had this issue of wireless not working on my insperion 14. Just reinstalled the .deb package in the restricted folder on the installation USB ( ie i had the ubuntu iso on this USB ) Then my wireless worked and is working now too.

Hope this works for you also

---

### Post by rmsmith87 on 2010-02-04
I have a similar problem.  Just reinstalled 9.1 on my Inspiron 6000 and now the wireless doesn't work.  I tried hardware drivers and all it said was no proprietary drivers found.  So I tried to get wicd and it said "E: couldnt find package wicd"  Any suggestions?

---

### Post by cjminton on 2010-02-05
> **rmsmith87 said:**
> I have a similar problem.  Just reinstalled 9.1 on my Inspiron 6000 and now the wireless doesn't work.  I tried hardware drivers and all it said was no proprietary drivers found.  So I tried to get wicd and it said "E: couldnt find package wicd"  Any suggestions?

Can you find it in the Synaptic Package Manager? [System -> Admin > Synaptic]

If you can't then perhaps you need to enable the universe repository.

To do this go to [System -> Admin -> Software Sources]

Make sure there is a check next to "Community-maintained Open Source software (universe)". Reload if it asks you to, then go back to synaptic and try installing it again, it should be there now.

---

### Post by pajus on 2010-02-07
I have simillar problem.
And I've resolve it:
system->admin->updatemanager (update everything)
and then
system->admin->hardware drivers (and here should be list of your possible drivers, you have to apply them and reboot)


or if you have broadcom wificard try:
```
sudo apt-get install b43-fwcutter
```

---


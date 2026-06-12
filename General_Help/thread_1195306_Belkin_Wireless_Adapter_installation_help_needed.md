---
title: "Belkin Wireless Adapter installation help needed"
date: 2009-06-23
forum: General Help
---

### Post by Road_Rebel on 2009-06-23
My brothers PC died the other week (tut, windows) and today i installed ubuntu.

Pleased with how quick it was with installation and i thought it would be an easy job but i was wrong.

i want to install a usb belkin wireless adapter, model no. F5D7050 but i cant, many threads have said download ndiswrapper but you cant when you dont have an internet connection on the desktop with ubuntu

ive tried copying the driver details to his documents but that hasn't workerd

so what do i do?

---

### Post by ptn107 on 2009-06-23
I have the same adapter.  You don't need to install anything the kernel in Ubuntu supports that hardware out of the box.

---

### Post by Road_Rebel on 2009-06-23
so what did u do to get it working?

---

### Post by RJ12 on 2009-06-23
> **ptn107 said:**
> I have the same adapter.  You don't need to install anything the kernel in Ubuntu supports that hardware out of the box.
If it works you need to enable wireless by right clicking the network icon check enable wireless then click the network icon again then select your access point

Hope this works

---

### Post by Road_Rebel on 2009-06-23
> **RJ12 said:**
> If it works you need to enable wireless by right clicking the network icon check enable wireless then click the network icon again then select your access point

Hope this works

where do i find this "network icon" ? :)

sorry, new to linux

---

### Post by RJ12 on 2009-06-23
At the top bar there should be two computers next two each other

---

### Post by Road_Rebel on 2009-06-23
its enabled but still nothing :(

---

### Post by RJ12 on 2009-06-23
Try putting it in a different USB slot

---

### Post by Road_Rebel on 2009-06-23
ive done that 

i typed in the terminal : lsusb

to see what usb devices are connected and it has it listed....

:(

---

### Post by RJ12 on 2009-06-23
Well I can no longer help becuase I am a beginner with Ubuntu too. If you can buy a new one I will tell you which one I have.

---

### Post by Road_Rebel on 2009-06-23
unfortuantely i can not, but thank you for ur time in trying to help me

---

### Post by Road_Rebel on 2009-06-23
i  have also tried messing around with the settings but they are completely blank

---

### Post by ptn107 on 2009-07-09
I just plugged it in and the light starts blinking.  You should see a list of wireless networks immediately provided you did not right-click network-manager and uncheck 'wireless networking.'

lsusb lists mine as 'Bus 003 Device 002: ID 050d:705c Belkin Components'

You can see more verbose lsusb output for the adapter at: [http://ubuntu.pastebin.com/m1ef7e291](http://ubuntu.pastebin.com/m1ef7e291)

---

### Post by t4thfavor on 2009-07-09
Bus 001 Device 007: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter


you mean that one, It sorks just fine out of the box, what are you having trouble with specifically?

type iwconfig on the terminal to see something like this:

```

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.417 GHz  Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

If you don't see that, then you still have a driver issue in which case something wen't wrong when your driver got installed. Maybe you need updates (which are hard if you rely on wireless for internet)

I just know on the latest kernel, and a few before that one, this adapter has worked just fine for me.

---


---
title: "need some help with wifi"
date: 2009-04-15
forum: General Help
---

### Post by EMKOEMO on 2009-04-15
i tryed ubuntu 8.10 works great with my wifi right way it was up and running. But for my setup i need to use the minimal ubuntu 8.10 which i have hard time using and i have no idea how to get the wifi working. I have atheos pci wifi from the irc i think i learned i need to get ath5k but i have no idea how to get this installed.

---

### Post by Titan8990 on 2009-04-15
ath5k drivers do not need to be installed as they are a part of the 802.11 stack in the kernel.

This is the guide you are looking for: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by EMKOEMO on 2009-04-15
i tried atp-get install linux-backports-modules-intrepid

i get

E: Couldnt find package linux-backports-modules-intrepid

---

### Post by Titan8990 on 2009-04-15
Scratch that, lets take this from the beginning...

Type the following into the terminal: sudo lshw -v

Post the results here.

---

### Post by EMKOEMO on 2009-04-15
i tried -v but that didn't give me any info just showed what commands i could use i did try -C network


  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10

i noticed that. before it was showing something els with driver=ath-pci now that i edit that file and blacklisted ath_pic and ath_hal i get this and i don't have ath0 anymore in iwconfig

---

### Post by Titan8990 on 2009-04-15
Try: 

```
sudo modprobe ath5k
```


I am not 100% but I think that card requires madwifi (ath_pci and ath_hal).

---

### Post by EMKOEMO on 2009-04-15
i get FATAL: Module ath5k not found.

when i try ubuntu live i get the wifi working right away and when i do iwconfig i get a ath0 same as here except now since i blacklisted pci and hal  i don't have an ath0 and for hslw i get unclamied.

---

### Post by Titan8990 on 2009-04-15
I'm guessing it was not working with ath drivers?

When you say you did a minimal install, do you mean you installed the server version? Paste the result of:

uname -r

---

### Post by EMKOEMO on 2009-04-15
i get 2.6.27-11-generic

im using [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
 8.10 32bit one but i tested the wifi on the regular 8.10 ubuntu didnt need to install anything.

---

### Post by Titan8990 on 2009-04-15
How did you test it this time?

---

### Post by EMKOEMO on 2009-04-15
well the guys on irc told me to try modprob ath5k and that gave an error that i don't have it and they told me that i need to have this to get wifi working and i dont know how to get it. But now u say it comes with it the kernel. So i have no idea im really new to linux.

---

### Post by Titan8990 on 2009-04-15
It comes with my kernel... It has to be installed in ubuntu but appears that your card might have been working fine with the madwifi drivers.

Do:

```
sudo modprobe ath_pci

sudo modprobe ath_hal

sudo ifconfig ath0 up

sudo iwlist ath0 scan
```

---

### Post by EMKOEMO on 2009-04-15
wow it  worked ahahaha  thanks :)

do i need to unblacklist pci and  hal or its fine to leave it like this. 

and now how do i configure it and type my wifi password?

---

### Post by Titan8990 on 2009-04-15
Yes, you will need to take it off of blacklist in order for them to load at boot.

Is your wifi password wpa or wep?

---

### Post by EMKOEMO on 2009-04-15
its wpa

---

### Post by Titan8990 on 2009-04-15
Haven't done much work with WPA. The official guide is here: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---


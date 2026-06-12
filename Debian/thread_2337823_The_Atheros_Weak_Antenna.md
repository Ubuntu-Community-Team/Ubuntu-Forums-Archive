---
title: "The Atheros Weak Antenna"
date: 2016-09-21
forum: Debian
---

### Post by Omar_Jair on 2016-09-21
Hello Ubuntu Forums, have asked this before but after a long search and modifications to files i cannot seem to have this working, i currently have installed a Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01) but it seems that this card is bloody weak, in fact i cannot use my normal wi-fi spots because the signal gets so weak it sometimes drops, is it the driver? is it my actual wireless config?
iwconfig throws this results:
```
omar@debian:~$ sudo iwconfig
lo        no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:"INFINITUM523D"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 80:38:BC:DA:76:60   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:94   Missed beacon:0


eth0      no wireless extensions.



```

---

### Post by Omar_Jair on 2016-09-22
bump

---

### Post by Omar_Jair on 2016-09-23
bump again

---

### Post by Omar_Jair on 2016-09-24
bump even more

---

### Post by Omar_Jair on 2016-09-25
Bump to inifity and beyond

---

### Post by jeremy31 on 2016-09-25
Atheros doesn't make the antennas as they are done by the laptops manufacturers if you do have a laptop.  Some of the antennas are not routed in the best possible way.  I get a better signal using my TP-link WN722N 150 Mbps USB adapter than I do from my internal Atheros wifi

---

### Post by Omar_Jair on 2016-09-26
Then Im doomed? Is atheros bad? Now that you mention it i don't know if it has something to do with those tiny cables that most wifi cards have to be connected, my recent pc has only one black cable while the other one had 2 one white and one black.

---

### Post by jeremy31 on 2016-09-26
Some wifi cards only have one antenna connection but I know some newer HP laptops have wifi cards with 2 connectors but only one antenna.  I would just get a USB wireless with an external antenna because I doubt just switching wifi cards using the same antennas is going to make a big difference.

I use a couple of the Atheros wifi cards and haven't done a true test to compare them against the Intel 7260 I have as one laptop I have won't boot with a different PCI(e) wifi card due to the BIOS and the laptop is a Lenovo

---


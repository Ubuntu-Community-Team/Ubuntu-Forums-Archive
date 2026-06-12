---
title: "Router related issues"
date: 2009-04-03
forum: General Help
---

### Post by Trzone on 2009-04-03
My sister's laptop (windows vista home premium) often has connection issues.  Her laptop has a wireless connection, it has no security on it, since any encryption forces the connection to become problematic after a day.  I have a d-link wbr 1310 revision B router with the latest firmware.  I am wondering if anyone has 'expert' knowledge on the following

Beacon Interval -  Beacons are packets sent by an Access Point to synchronize a wireless network. Specify a Beacon interval value between 20 and 1000. The default value is set to 100 milliseconds.

RTS Threshold - This value should remain at its default setting of 2346. If you encounter inconsistent data flow, only minor modifications to the value range between 1 and 2346 are recommended. The default value for RTS Threshold is set to 2346.

Fragmentation - This value should remain at its default setting of 2346. If you experience a high packet error rate, you may slightly increase your "Fragmentation" value within the value range of 256 to 2346. Setting the Fragmentation value too low may result in poor performance.

DTIM Interval - Enter a value between 1 and 255 for the Delivery Traffic Indication Message (DTIM). A DTIM is a countdown informing clients of the next window for listening to broadcast and multicast messages. When the Access Point has buffered broadcast or multicast messages for associated clients, it sends the next DTIM with a DTIM Interval value. AP clients hear the beacons and awaken to receive the broadcast and multicast messages. The default value for DTIM interval is set to 1.

Preamble Type - The Preamble Type defines the length of the CRC (Cyclic Redundancy Check) block for communication between the Access Point and roaming wireless adapters. Make sure to select the appropriate preamble type and click the Save Settings button.

Note: High network traffic areas should use the shorter preamble type. CRC is a common technique for detecting data transmission errors. 

These are advanced settings, which i'm willing to try new things to solve this issue.

---

### Post by lisati on 2009-04-03
A number of things can mess with wireless connectivity, including clashes with other nearby wireless networks.

I found this tutorial after a quick search: [http://www.computerguyslive.com/content/wireless/wirelessindex.asp](http://www.computerguyslive.com/content/wireless/wirelessindex.asp)

---

### Post by Trzone on 2009-04-03
It could be anything from the firewall, the environment (through walls), phones, etc  However i want to change some of the advanced settings and see what goes on, any advice?

---

### Post by lisati on 2009-04-03
> **Trzone said:**
> It could be anything from the firewall, the environment (through walls), phones, etc  However i want to change some of the advanced settings and see what goes on, any advice?

I recently had connectivity problems - my setup includes two wireless routers and some wired connections as well, one of the routers (an integrated wireless and ethernet router with ADSL modem) was having trouble connecting to my broadband connection which was having a ripple effect through my setup. It turned out that replacing the ADSL filter on my phone line went a long way to curing the woes I had. 

Hopefully someone else might have some other suggestions as well.

---


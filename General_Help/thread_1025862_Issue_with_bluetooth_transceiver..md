---
title: "Issue with bluetooth transceiver."
date: 2008-12-30
forum: General Help
---

### Post by meetoblivion on 2008-12-30
I just reinstalled ubuntu and now I'm trying to get bluetooth to work.  I've previously been able to, but with another transceiver.  I have a Microsoft Transceiver 3.0 for Bluetooth that came with my keyboard.  How do I get ubuntu to recognize it?  I've read the docs, bluez is already installed, but I don't get it to popup when I plug it in.  I did see a mention of "supported adapter."  How do I tell if mine is "supported"?

---

### Post by fragos on 2008-12-30
Perhaps this will be helpful. I seen a number of people having trouble getting MS bluetooth dongles recognized. You can do lsusb to see if the hardware is seen but that doesn't mean there's a proper driver for that dongle.

[http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)

---

### Post by meetoblivion on 2008-12-31
Hmm well straight from that link you sent...

> 
Your PC&#8217;s Bluetooth hardware is automatically recognized under Ubuntu


Except, it's not.  I noticed that my hcid.conf was missing, so I looked over another one and created it.  The device is shown under lsusb (the first place I checked).

Any other ideas?

---

### Post by meetoblivion on 2009-01-01
well, i'll take it from everyone's silence there's no other ideas.

just curious if anyone has bluetooth working on ubuntu?  What dongle do you use?

---

### Post by fragos on 2009-01-01
> **meetoblivion said:**
> well, i'll take it from everyone's silence there's no other ideas.

just curious if anyone has bluetooth working on ubuntu?  What dongle do you use?

I've used a TRENDnet bluetooth dongle for a couple of years with Ubuntu and I upgrade with every new release of Ubuntu.  My use is daily both sending to and receiving from my Nokia N810.

---


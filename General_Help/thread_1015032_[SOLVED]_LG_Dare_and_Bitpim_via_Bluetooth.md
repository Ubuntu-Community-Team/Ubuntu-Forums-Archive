---
title: "[SOLVED] LG Dare and Bitpim via Bluetooth"
date: 2008-12-18
forum: General Help
---

### Post by greyfox1 on 2008-12-18
I've been following [this guide]("http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux") to pair my LG Dare with my computer for use with BitPim.  Initially it worked for a day or two but now I can't seem to connect using BitPim no matter what I do.

I can confirm that the phone and the computer are paired because I can browse files on the phone using Nautilus and even pass them back and forth.  However when I use BitPim and open the settings for the phone, the bluetooth port (/dev/rfcomm0) shows as inoperable.  I can't seem to change this no matter what I do (remove the phone and re-pair it, reboot, remove the dongle and plug it in again, restart bluetooth from the command line).

I also noticed that when I issue: 

```
sdptool browse [mac address] | awk '/BT DIAG/,/^$/ {print $0 | "grep Channel"}'
```

as the tutorial describes, a channel number is no longer returned.  It just dumps be back to the prompt again.  Initially this did return a channel of 16.


Any thoughts or input would be appreciated.

---

### Post by greyfox1 on 2008-12-18
BTW, here's the info on my dongle according to lsusb:

Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by mdebusk on 2008-12-19
> **greyfox1 said:**
> I've been following [this guide]("http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux") to pair my LG Dare with my computer for use with BitPim.

Thank you for pointing me to this. I can finally connect my VX-8560 "Chocolate 3" to Bitpim (and Nautilus) via Bluetooth.

> 
```
sdptool browse [mac address] | awk '/BT DIAG/,/^$/ {print $0 | "grep Channel"}'
```

as the tutorial describes, a channel number is no longer returned.

When I run sdptool, there is no listing titled "BT DIAG". There is one titled "Serial Port", though, which returned channel 8. Try replacing '/BT DIAG/' with '/Serial Port/'.

---

### Post by greyfox1 on 2008-12-19
Where does the tutorial say anything about a channel number no longer being returned?

At any rate the specified command DID return a channel number for me just a few short weeks ago.  

I'll give your suggestion a whirl when I am at home.

---

### Post by mdebusk on 2008-12-20
> **greyfox1 said:**
> Where does the tutorial say anything about a channel number no longer being returned?

It doesn't say it anywhere. The awk and grep he used was to filter out the information he didn't want to see. As it ended up filtering out *everything* for me, I decided to leave out the filters and go through everything that was returned. The only thing that made sense was the serial port, and it returned an "8" for me. I tried it and it worked.


> At any rate the specified command DID return a channel number for me just a few short weeks ago.

The only thing I can think of is that Verizon updated your phone's firmware one night while you slept. My phone has that capability, and yours isn't much older than mine.

---

### Post by greyfox1 on 2008-12-22
Oops, I misread your first post.  Sorry about that.

At any rate, your suggestions did the trick for me.  For some reason, the channel I needed to use is 5 now.  I have no idea what must have changed.  It wasn't my phone's firmware-- I know because I checked when I bought it and it's still the same version (05).  But that's neither here nor there. The point is that my issue has been resolved!  Huzzah!  Hopefully others who are having the same problem will come across this.  Thank you sir!

---

### Post by mdebusk on 2008-12-23
> **greyfox1 said:**
> Hopefully others who are having the same problem will come across this.  Thank you sir!

I couldn't have done it without you. :)

---


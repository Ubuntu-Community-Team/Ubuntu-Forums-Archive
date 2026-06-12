---
title: "Problem installing Asus WL-107g pcmcia"
date: 2005-12-23
forum: General Help
---

### Post by KenSentMe on 2005-12-23
I want to install my new Asus WL-107g pcmcia wireless adapter, but i come up some troubles on my way.

I try to use this wiki: [https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/DriverAndRaconfig](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/DriverAndRaconfig)

The problem is when i try to do 'make' it says that my 'build' dir is missing:

> make: *** /lib/modules/2.6.12-9-386/build: Onbekend bestand of map.  Stop.
rt2500.ko failed to build!

And indeed, there is no buid dir there. Should there be one, why don't i have it and how can i get one? Simply mkdir build doesn't do the trick.

---

### Post by linuxbtdsc on 2005-12-23
Do you have the drivers disk that came with the pcmcia card? You can use ndiswrapper to install the card via its Windows .ini file that can be found on the disk (or possibly downloaded off of the Internet)

-linuxbtdsc

---

### Post by KenSentMe on 2005-12-23
We'll i was hoping to find an answer to why i don't have a build dir. This seems strange to me.

---


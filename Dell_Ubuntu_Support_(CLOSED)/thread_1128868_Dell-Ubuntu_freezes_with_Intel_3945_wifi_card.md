---
title: "Dell-Ubuntu freezes with Intel 3945 wifi card"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by huckelberry on 2009-04-18
I'm relatively new to all of this, so go easy on me here.

I wanted to try some other Linux distributions on my Dell Mini 9, so swapped the stock Broadcom 4312 wireless card out for an Intel 3945 wireless card. Many Linux distributions do not yet support the Broadcom card but it is my understanding that the Intel driver has been merged into the mainline kernel since 2.6.24....

Tried my other distros out and wanted to reload Dell's Ubuntu 8.04... Surprise! The DVD would stall and freeze before completing the SSD re-write/re-install, leaving me with an inoperable netbook. Other distros, such as Puppy Linux, still loaded into RAM and fully functioned in frugal fashion.

I removed my internal SSD and cloned it, using Clonezilla Live and a different (completely stock) Ubuntu Mini 9 -- and re-installed the loaded SSD back into my Mini 9 with the Intel 3945 wireless card... This time, my Mini 9 would boot, but immediately freeze up. No user input was allowed via mouse or the touch-pad.

I killed my Mini 9, removed all power sources (including the battery), and re-installed the stock Broadcom 4312 wireless card. All functions returned with the stock configuration.

What does the wireless card have to do with writing to the hard drive from an external DVD or using a mouse / touch-pad? If this is due to the newly purchased Intel 3945 wireless card, why isn't it already supported?

Yeah, I already had the uninformative online chat with Dell reps, who told me to go online at Dell.com (same place that I entered their chat site) and called the US Support telephone numbers they gave me -- connecting to Canonical (sp?), French-speaking Canada (who don't field U.S. issues), India, and the Phillipines... and recieved advice from "just install Windows" to "Windows won't run on the Inspiron 910 [Mini 9]" to absolutely no help at all.

So, does the Ubuntu Mini 9 support the Intel 3945abg wireless card? Why would a wireless card foul up other functions? And, how can I get Dell-Ubuntu lpia support for the Intel 3945 wireless card that other Linux distros already support?

-Bret
Dell Mini 9 with Dell-Ubuntu 8.04LTS, Runcore 64G SSD, 1.3M Pixel camera, Bluetooth, wireless, and external DVDRW.

---

### Post by snowpine on 2009-04-18
Save yourself the headache and install a more recent version of Ubuntu. I am personally using 9.04 lpia on my Mini 9.

The Dell version of Ubuntu is specifically designed for that one hardware configuration. It is not meant to be all things to all people. :)

---

### Post by brianchidester on 2009-04-27
The Dell version of ubuntu does not have the proper driver and is probably causing a kernel panic when it gets to that point.

---

### Post by grenet on 2009-04-27
I've been using the main Ubuntu image on my Dell 1304 since 8.04 and it's worked like a charm.  the Dell images are not needed was my understanding from 8.04 on.

---


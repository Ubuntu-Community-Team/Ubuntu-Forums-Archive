---
title: "Laptop specs"
date: 2009-06-02
forum: General Help
---

### Post by kd0afk on 2009-06-02
I am shopping around for a new laptop and I kind of like the Dell Studio. I am pasting the specs. I have been having graphics problems with intell on my laptop and I was wondering if I will get better results with this:

---

### Post by kd0afk on 2009-06-02
sorry

       Additional Specifications     Processor Brand:   AMD     Processor Type:   Turion 64 X2
Hard Drive Size:   320GB     
System RAM:   4096 MB     
Display     Display Type:   15.4" TFT     
Widescreen Display:   Yes     
Processor     Multi-Core Technology:   Dual-Core     Processor:   AMD Turion 64 X2 mobile technology RM-74 / 2.2 MHz     
Chipset Type:   AMD M780G     Cache 
Memory     Type:   L2 cache     Installed Size:   1 MB     Storage     
Hard Drive:   320 GB - Serial ATA-150 
    RAM     Installed Size:   4 GB / 4 GB (max)     Technology:   DDR2 SDRAM - 800 MHz     
Configuration Features:   2 x 2 GB     Optical Storage     Type:   DVD±RW     
Networking     Data Link Protocol:   Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g     Wireless LAN Supported:   Yes     
Video     Graphics Processor / Vendor:   ATI Mobility Radeon HD 3200     
Audio     Audio Input:   Microphone     
Operating System / Software     OS Provided:   Microsoft Windows Vista Home Premium 64-bit Edition     Software:   Drivers & Utilities, Microsoft Works 9.0, McAfee SecurityCenter (30 days subscription) 
    Battery     Technology:   6-cell lithium ion     Installed Qty:   1     Capacity:   56 Wh     Notebook  Camera     Camera Type:   Integrated     Product Dimensions     Width:   14 in     Height:   1.5 in     Depth:   10.3 in     Weight:   6.2 lbs     
Color:   Black     
Card Reader     Supported Flash Memory Cards:   SD Memory Card, Memory Stick, Memory Stick PRO, MultiMediaCard, xD-Picture Card, SDIO     Power     Voltage Required:   AC 120/230 V ( 50/60 Hz )     Manufacturer Warranty     Service & Support:   1 year warranty

---

### Post by Tipped OuT on 2009-06-02
Yes, ATI drivers are far better then Intel drivers.
Nice computer BTW. ;)

---

### Post by kd0afk on 2009-06-02
> **Tipped OuT said:**
> Yes, ATI drivers are far better then Intel drivers.
Nice computer BTW. ;)

I absolutely hate Walmart but they are selling this model for around $680. My plan is to get it, partition the drive and put ubuntu on it dual boot.

---

### Post by Iusedtowearatie on 2009-06-02
Probably a good plan. However, as you may already know, Dells (and indeed many other makes today) are typically delivered with a factory set recovery partition of a few GB, something that have caused confusion to some Linux users trying to set up a reasonable partition structure.

---

### Post by lisati on 2009-06-02
> **Iusedtowearatie said:**
> Probably a good plan. However, as you may already know, Dells (and indeed many other makes today) are typically delivered with a factory set recovery partition of a few GB, something that have caused confusion to some Linux users trying to set up a reasonable partition structure.

That kind of problem isn't confined to Dells. I was baffled at first by the partition structure on my newer Toshiba laptop that came with Vista preloaded when I was looking to put Ubuntu on it. It came with a recovery partition, a normal Vista partition, and what I think is a "work" partition that's somehow connected with the initial installation - three in all. Strange in its way: my Compaq desktop only came with two partitions, a recovery partition and a "normal" XP partition. 

The other laptop I recently gave to my 13-year old nephew for his homework came with a recovery DVD and an XP partition. (Sorry to the staunch Ubuntu fans & MS haters: I put XP back on it with a couple of family-friendly games, along with copies of e-sword, firefox, open office, thunderbird, MS Encarta, MS works, and AVG free, and removed the IE icon from the desktop; I threw in a spare ethernet cable and a mouse: my in-laws are kinda computer-illiterate and probably wouldn't have the foggiest idea about signing up to the forums to ask for help if I'd left Ubuntu on it)

---

### Post by kd0afk on 2009-06-02
so what exactly does this odd partition set up mean in the way of loading linux?

---

### Post by Iusedtowearatie on 2009-06-02
> **kd0afk said:**
> so what exactly does this odd partition set up mean in the way of loading linux?

Among other things it means you need to decide whether you want to be able to use the recovery partition in the future, should you happen to do something "unexpected" to the Windows part of your dual boot installation. If this is the case, then you need to understand things like "where is my MBR", "where did my /home go" etc when you configure your partitions and "direct" Windows and Linux software to them.
I'm sure there are people out there more knowledgeable in these details, all I can tell you is that its far easier to either go all out with Linux, or wipe the HDD and then perform a dual boot installation on an empty HDD.

---

### Post by kd0afk on 2009-06-02
> **Iusedtowearatie said:**
> Among other things it means you need to decide whether you want to be able to use the recovery partition in the future, should you happen to do something "unexpected" to the Windows part of your dual boot installation. If this is the case, then you need to understand things like "where is my MBR", "where did my /home go" etc when you configure your partitions and "direct" Windows and Linux software to them.
I'm sure there are people out there more knowledgeable in these details, all I can tell you is that its far easier to either go all out with Linux, or wipe the HDD and then perform a dual boot installation on an empty HDD.

Thank you for the information.

---


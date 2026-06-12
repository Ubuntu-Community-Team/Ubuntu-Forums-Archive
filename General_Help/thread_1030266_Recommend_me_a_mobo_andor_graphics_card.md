---
title: "Recommend me a mobo and/or graphics card"
date: 2009-01-04
forum: General Help
---

### Post by happypig on 2009-01-04
I'm in the market for a new Mobo/processor/graphics card due to my slowly dying P4.

It will be running Kubuntu.

Can anyone recommend a decent motherboard/graphics card combination that will be supported ?

Budget is about 250 UK pounds (which is around 350 US $ ??)

Cheers

---

### Post by hotweiss on 2009-01-04
Go for the Intel E8400 and a Gigabyte motherboard with RAID. This combination should only cost you about $300. The E8400 can be overclocked to 4.0 GHz easily and with the extra $50 you can now by the second hard drive for your RAID configuration.

---

### Post by fjgaude on 2009-01-04
I second the notion... and go for a cheap Nvidia graphics card, a 7600 or so. Unless you are into heavy games such a card works fine with fast memory and CPU.

---

### Post by Psylon on 2009-01-06
I just recently tested a bunch of motherboards for some upgrades to various friends and family machines. One of the better boards, that worked out of the box is this one: Asus M2N68-VM. Here is a link to some more information about the board: [http://www.interlinkadvantage.com/blog/?p=22](http://www.interlinkadvantage.com/blog/?p=22)

---

### Post by fenian on 2009-01-06
A few things to consider when replacing the motherboard...

IDE connectors-Your P4 probably has IDE drives the motherboard you buy will need to have IDE connectors so you can plugin your drives.You should get a motherboard with both IDE (for your older hadware) and SATA connectors (for any future drive upgrades)

Memory-The memory in your P4 will probably not be compatible with a newer motherboard so you will also need to buy memory.

PCI card expansion slots-Many newer motherboards only have two pci slots if you have more than two PCI boards you will need to make sure the motherboard has enough slots (motherboards with more slots are usually more $$$)

As for the video card most motherboards have integrated video (I would look for one with Nvidia integrated graphics) if you don't do a lot of gaming these are probably suitable for your needs.

Processor-I wouldn't get anything less than a dual core processor.

Motherboard-Stay away from PC Chips and other cheapo motherboards.Some reliable brands are Asus,EVGA,Biostar,Gigabyte and Elitegroup.Also take into consideration the form factor of your computer case if its micro atx you must get a micro ATX motherboard however if your case is ATX you can put a micro ATX motherboard in it.

---

### Post by wolfen69 on 2009-01-06
[Phoronix.com]("http://www.phoronix.com/scan.php?page=home") is a great place to find linux compatible hardware. lots of reviews.

---

### Post by fenian on 2009-01-06
This would probably be a decent combo at right about the maximum of your price range.

[Motherboard]("http://www.microdirect.co.uk/(26676)Gigabyte-motherboard-GA73PVMS2H-GeForce-7100.aspx")

[Processor]("http://www.microdirect.co.uk/(37289)Intel-Core-2-Quad-Pro-Q6600-95W-Energy-Efficient.aspx")

[Memory]("http://www.microdirect.co.uk/(9851)Corsair-Value-Select-1Gb-DDR2-PC5300-memory.aspx")

---

### Post by Tom Mann on 2009-01-06
I would suggest a 7600GT (if you're after silent ASUS do a card that has heatpipes and no fans) I believe it's a SilentPipe model...

For your motherboard I'd go for ASUS again (I have an M2N-SLI Deluxe which is still going strong after two years, takes an AMD processor) and the fastest AMD X2/X3/X4 with the money you have left (NB: the M2N-SLI Deluxe can take AMD's Socket AM2+ processors, but doesn't give you the extras a Socket AM2+ board would have, however it will still run fine)

I should add I run a 6400+ AMD Black Edition X2 processor, and Kubuntu boots fully working straight off the CD, I just add things like kubuntu-restricted-extras, enable the nVidia driver, etc.

And finally I agree with Corsair memory, but you can also looks at Kingston ValueRAM or [www.crucial.com/uk](www.crucial.com/uk) for memory that works well (in my experience)

---

### Post by hangfire on 2009-01-06
> **happypig said:**
> I'm in the market for a new Mobo/processor/graphics card due to my slowly dying P4.

It will be running Kubuntu.

Can anyone recommend a decent motherboard/graphics card combination that will be supported ?

Budget is about 250 UK pounds (which is around 350 US $ ??)

Cheers

I would strongly suggest getting a cheap 8xxx or later video card. The reason is simple, 7xxx and earlier cards, while having been well supported in Linux, are older architectures, while the 8xxx is the new Unified architecture which will be the primary focus of driver development for a long, long time. 

In other words, expect driver support for anything older than the 8000 series to stagnate.

Another reason to get an 8xxx card is the cheaper ones are the same price or cheaper than a 7xxx card.

As for Motherboard, MSI, Asus and Gigabyte all make good boards. I suggest something with an Intel chipset, not VIA or nVidia, as they are the best supported. Say what you will about Intel, they are very good at assuring kernel.org support of their chipsets.

-HF

---


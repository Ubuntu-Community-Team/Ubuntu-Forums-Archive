---
title: "Upgrade video card on older computer?"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by colllin on 2008-05-13
I don't have the funds to buy a new computer yet and was wondering if upgrading my video card would improve performance (specifically fps).

Here is the output of lshw:

PCI (sysfs)  
collin-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 767MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.2
          size: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 9.1
                bus info: pci@0000:02:09.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: a.1
                bus info: pci@0000:02:0a.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: a.2
                bus info: pci@0000:02:0a.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16 module=ehci_hcd
           *-network:0
                description: Ethernet interface
                product: 82557/8/9/0/1 Ethernet Pro 100
                vendor: Intel Corporation
                physical id: b
                bus info: pci@0000:02:0b.0
                logical name: eth0
                version: 08
                serial: 00:02:b3:98:4e:92
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
           *-network:1
                description: Wireless interface
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications Inc.
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: wifi0
                version: 01
                serial: 00:0d:88:c7:5f:33
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

Browsing around on newegg i saw a some AGP cards in the $30-$50 range. Would upgrading the video card have a significant benefit? and if so, what card would you recommend for my system?

---

### Post by Perfect Storm on 2008-05-13
A nvidia card, less trouble, better performance (due to better driver atm).

---

### Post by mivo on 2008-05-13
Yes, but you should not buy one of the latest models. A 6800 from Nvidia would be as high I'd go for your system. They should be fairly cheap, and you'll get much better FPS than from the ATI 9200.

---

### Post by NR1224 on 2008-05-13
I second that

---

### Post by colllin on 2008-05-13
Thanks guys! Based on your suggestions I'm looking at purchasing this card

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814131014](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131014)

I don't want to spend more than $50 and this seems like it will be a nice upgrade from what I currently have.

---

### Post by mivo on 2008-05-13
I would consider this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814141075](http://www.newegg.com/Product/Product.aspx?Item=N82E16814141075)

It has less memory than the one you picked, but memory doesn't really say much about the performance. You want a fast card, and the 6800XT certainly meets that criterion. It's an AGP card too and is just shy of $50. :)

Take a look at this table:
[http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units)

Mostly you want a high memory bandwidth and decent clock speed.

---

### Post by colllin on 2008-05-13
Thanks mivo! I don't know too much about graphics cards, so i was just looking for one with a higher memory in my price range. I just ordered the card from newegg and should have it by the end of the week. I'll post back here with the results of the upgrade.

---

### Post by mivo on 2008-05-13
Not a problem. :) I think you got a very good deal there and will notice a very major increase in performance. The only remaining concern is your power supply unit. Do you know how much watts it has? You should be fine, though.

---

### Post by colllin on 2008-05-13
I'm at work now, but I'll look at that when I get home. Hopefully it's enough. I'd hate to have to replace the psu too.

---

### Post by Sockerdrickan on 2008-05-13
I would consider getting a GeForce 7600 at least, it might cost more but it's not too expensive and offers official support for more years than the 5 and 6 series.

---

### Post by colllin on 2008-05-15
I finally got around to checking my power supply and it says that it is "250 watts max." A little further down on the sticker said that it was 170 watts at a certain voltage(can't remember the voltage number)

> **Tux0r said:**
> I would consider getting a GeForce 7600 at least, it might cost more but it's not too expensive and offers official support for more years than the 5 and 6 series.

A 7600 is about $35 more than I wanted to spend and I'm not too worried about the support. I just need it to last me for another 1.5 years.

---

### Post by colllin on 2008-05-19
I finally received my new video card today and I'm having a problem. I'm guessing it's the aforementioned psu problem.

When I turn on my computer my monitor displays "no signal." The monitor knows that it is connected to the computer, because when it isn't it displays "not connected"

---

### Post by rocky5051 on 2008-05-19
First, check to see if the video card is firmly attached to the slot. I'm famous for that mistake...especially with AGP slots. It might be wedged just slightly out of place...

Next, if the card has it, you might have to plug one of the power supply cables into the video card itself.

However, I think it might just be the power supply (although you should check the other things first). That 7600 probably sucks down alot of power, and with the combiniation of that P4 CPU (they are pretty power hungry) and the video card you might need at least 500w power supply to run the card with the rest of your machine on a stable note.

My computer has a lousy GeForce 4000MX for a PCI slot, but that itself, dated as it is, needs at least a 300w power supply minimum to function without destablizing the rest of the computer, so yours probably needs at least 400w. It should say on the video card's package.

EDIT: Oops sorry I didn't see which one you intended to get. Still, I believe it to be the power supply to blame.

---

### Post by mivo on 2008-05-19
How is the monitor connected? Through a VGA or a DVI cable? Do you hear the video card's fan when you turn on the computer? The monitor stays black right from the start and there's never a picture at all?

---

### Post by colllin on 2008-05-19
I checked 3 times to make sure the card was installed correctly. It doesn't look like there is any place to plug the card directly into the power supply.

The monitor is connect via vga. When I power on the computer nothing gets displayed on the monitor at all(except for the monitor's "no signal" message) It's hard to hear if the fan on the card is running over the other fans. I'll have to check to see if it spins when i power on the computer.

---

### Post by rocky5051 on 2008-05-19
If the fan on the card is spinning, you could also try clearing the CMOS (mind you, that would clear your BIOS setup data and you would have to go through and set it all up again to be how it should be). I wouldn't recommend it if you don't understand how to setup your BIOS again, though. My reasoning for this idea is that it might fix some possible mis-setting that is keeping it from working properly.

---

### Post by colllin on 2008-05-19
Sorry guys, i must be blind. I just looked at the card again and found that there is a connection for the power supply. I now have the card up and running. Thanks for all your help.

I just installed the nvidia drivers and have to do a restart. I will post an update on how it affects my frames per second in games.

---

### Post by rocky5051 on 2008-05-19
> **rocky5051 said:**
> Next, if the card has it, you might have to plug one of the power supply cables into the video card itself.

I did ask about that. :lolflag:

Good luck. I hope to buy a new CPU and video card for my machine, which I've always only had enough money for upgrades. At my current point in time, I've basically transformed my 8 year old machine into a decent linux box.

So saying, I'll probably be asking the same questions later. :)

EDIT: OH you should also mention if you see any artifacts (glitches such as corrupted graphics, missing textures, and stuff like that) or experience lock-ups. These could also help determine if you need a better PSU. I once had a 200w PSU with my current video card, and I tried running Halo (on an XP machine). Within 2 minutes of playing, it locked up, every time, until bought the 400w PSU I have now.

If you run a game in WINE when you test the video card out, be advised that some of the glitches and such may simply be caused by WINE itself and not your hardware.

---

### Post by colllin on 2008-05-19
Well there is definitely some power issues going on. I did notice some graphical problems in game where some textures weren't rendering. Also my optical drive cannot get enough power to spin a disc. Looks like I'm going to have to scrounge up some more money for a psu. :(

---

### Post by rocky5051 on 2008-05-20
Well, when you buy a PSU you shouldn't just look for the cheapest one with the highest wattage rating, as cheap ones tend to malfunction and fail and destabilize under varying power loads.

I would suggest this one. 500w would give you a decent amount of headroom and be plenty to power your computer with that video card.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817182044](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182044)

It's around $50. You might find something cheaper but, as I said, cheap PSU's are prone to failure.

---

### Post by colllin on 2008-05-20
The only problem is that my computer(Dell Dimension 4400) case doesn't look like it will accomodate that PSU. I'm not sure how to explain it, but the back panel is what's causing the problem. Here is a picture of the back of the computer(it's towards the bottom of the page):

[http://www.devhardware.com/c/a/Computer-Systems/Dell-Demension-4400/](http://www.devhardware.com/c/a/Computer-Systems/Dell-Demension-4400/)

There is a hole that's just big enough for the power connection and a grated area for the fan. Anything with a power switch won't work and anything with a different plug/fan arrangement won't work.

I think I may just return the graphics card and start saving up for a new computer.

---

### Post by rocky5051 on 2008-05-20
There's room. The power supply is bolted in behind the grate. Notice the four mounting screws on the back of the computer, one near the top-left is slightly offset. The screws would bolt into the PSU this way.

The small spot for the plug on the PSU should be placed right for any PSU with the same form factor as the case.

---

### Post by colllin on 2008-05-20
I'm still not sure it would work. When I get home I'll take a better picture of the back of my computer.

Note: the hole for the plug is just big enough for the plug and the volt switch. It's hard to see in that picture.

---

### Post by mivo on 2008-05-20
I'm sorry that it is the PSU. :(  You had already ordered it when I mentioned it, but I should have thought of it before when I recommended the card. If getting a new PSU isn't an option, perhaps keeping the card is still a worthwhile idea. It's a very solid card, even now, and the price was remarkably good (if I could get it at that price over here, I'd put it in my other box). Unless you plan on getting a powerhouse PC and want to play commercial games in super high details, it is likely to meet your needs.

You may be getting a decent machine with sufficient PSU (and without video card) for a good price. Electronics in the US is so enviously cheap.

---

### Post by rocky5051 on 2008-05-20
Yeah I see your point. I looked around and I can't see any power supplies that would fit that arrangement exactly. You could try cutting holes (granted you don't touch the mounting screw holes) so they would fit in place but...that's all I could think of. :( (The way I see it is if it still bolts into place, and there is a space for the plug and switches to fit, it could still work. The mounting screw arrangement doesn't appear to be different than any normal PSU.)

---

### Post by iheartubuntu on 2008-05-21
I would be cautious about buying anything from NewEgg.com. Some items list they can be returned and others say they cant. If you shop with them, just be observant of that in case you may need to return something. My sister bought a computer from them, installed Ubuntu, didnt work good, we put the original XP back on, and when she went to return it they refused her. After browsing their website more, I noticed my sister picked a computer than couldnt be returned (a toshiba laptop). I helped her get BBB involved (better business bureau) and NewEgg finally took the computer back. But it was definitely a hassle.

---


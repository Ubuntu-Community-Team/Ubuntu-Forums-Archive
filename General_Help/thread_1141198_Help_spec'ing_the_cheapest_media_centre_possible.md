---
title: "Help spec'ing the cheapest media centre possible"
date: 2009-04-28
forum: General Help
---

### Post by Scubdup on 2009-04-28
I've just bought a new telly and would like to build a media centre to make the most of it.

I want to be able to:-

[LIST]
[*]Stream HD to the telly
[*]Surf the internet and use BBC iPlayer
[*]Play DVDs
[*]Use a remote keyboard/mouse comfortably on the sofa
[*]Pause and record TV
[/LIST]

I've been looking and come up with this:-

[LIST]
[*]Intel Pentium Dual-Core E2200 "LGA775 Core 2" 2.20GHz (800FSB) -£59.79
[*]Asus P5Q-EM Intel G45 Micro-ATX (Socket 775) PCI-Express DDR2 Motherboard £106.94
[*]Corsair 2GB (1x2GB) DDR2 PC2-5300C5 200-Pin SODIMM Module (VS2GSDS667D2) £20.69
[*]Jou Jye Slim MATX Desktop Case - With 250W PSU	£39
[*]Seagate Barracuda 7200.12 500GB SATA-II 16MB Cache - OEM (ST3500418AS) £43.99
[*]Hauppauge WinTV Nova TD 500/Dual digital PCI TV tuner card £59.41
[*]LG GH22NS40 22x DVD±RW SATA Dual Layer ReWriter (Black) - £18.99
[*]Keysonic KB-616-RF Wireless multimedia mini keyboard with laser track ball and 2 mouse buttons - £31.04

[*]Total: £379.99
[/LIST]
And I'd planned to use Mythbuntu.

[B]Does anyone have any ideas about getting the cost down?

Also, are any alarms ringing regarding linux compatibility?[/B]

---

### Post by northern lights on 2009-04-28
> **Scubdup said:**
> ]Does anyone have any ideas about getting the cost down?[/B]

You're already looking at the cheapest CPU on the market and I'd even consider going for an E5200 rather than the E2200. It's minimally more spendy and is the cheapest 40nm core (as opposed to 60nm with the E2200) CPU currently on the market. Don't be irritated by the E5200 also being called *Pentium Dual Core* and not *Core2 Duo* - it's got a real Wolfdale core.

The only point where I see opportunity to save cash would be the board. You need not spend a hundred quid for the motherboard. It certainly depends what you're looking for in a board, but my recommendation'd be the *Gigabyte GA-73PVM-S2H* - NVIDIA GeForce 7100 graphics chip, HDMI out (important for a media centre, no?!), 2/4/5.1/7.1-channel audio, S/PDIF In/Out. Paid 60 Euros for it two months ago. You have to check British vendors.

You don't have to go with the exact model I recommended, but anyhow, the board's where you should be able to save cash.

---

### Post by Scubdup on 2009-04-28
Thanks Northern Lights. I selected that graphics card because it was recommended on another forum, but I hadn't realised it didn't have a HM out!

Am I right in thinking the Gigabyte GA-73PVM-S2H mobo wouldn't need a separate graphics card? Is this a good idea? I had initially budgeted for a cheap mobo and a cheap graphics card.

---

### Post by northern lights on 2009-04-28
> **Scubdup said:**
> Am I right in thinking the Gigabyte GA-73PVM-S2H mobo wouldn't need a separate graphics card?Yes.

> **Scubdup said:**
> Is this a good idea?Depends on the machine's usage. For media centre or office comp, it definitely is. You will not find a mobo / graphics card combo cheaper than a board with an integrated chip. If you wanted to play high-end games, it'd be a different story.

> **Scubdup said:**
> I selected that graphics card because it was recommended on another forum, but I hadn't realised it didn't have a HM out!
The *P5Q-EM* also comes with an HDMI out. However it offers nothing my recommended board doesn't ship with either and is almost twice as expensive.

---

### Post by Scubdup on 2009-04-28
Thanks!

I like your suggestions. I also found a different case that wasn't a slimline thing.

[LIST]
[*]Intel Pentium Dual-Core E5200 "LGA775 Core 2" 2.50GHz (800FSB) - Retail £62.09
[*]Gigabyte GA-73PVM-S2H - NVIDIA GeForce 7100 graphics chip, HDMI out £57.49
[*]Corsair 2GB (1x2GB) DDR2 PC2-5300C5 200-Pin SODIMM Module (VS2GSDS667D2)£20.69
[*]Novatech Opera Media Centre Case FULL SIZE ATX & MICRO ATX + POWER SUPPLY ATX-500W £46
[*]Seagate Barracuda 7200.12 500GB SATA-II 16MB Cache - OEM (ST3500418AS) £43.99
[*]Nova-T 500/Dual Digital Freeview tuner (watch 1 ch, rec 1 ch or rec 2 at same time) w/RC	£57.50	
[*]Keysonic KB-616-RF Wireless multimedia mini keyboard with laser track ball and 2 mouse buttons	£31.04
[*]LG GH22NS40 22x DVD±RW SATA Dual Layer ReWriter (Black) - OEM £18.99
[/LIST]
Total	337.79

---

### Post by ushills on 2009-04-28
cut the motherboard and cpu.  I have an AMD 64x2 and gigabyte mb with HDMI output built-in. To be honest you don't need high spec with myth I also used P4 1.8 and that was fine just plenty of RAM needed. See signature for specs.

---

### Post by northern lights on 2009-04-28
> **Scubdup said:**
> [LIST]
[*]Intel Pentium Dual-Core E5200 "LGA775 Core 2" 2.50GHz (800FSB) - Retail £62.09[/LIST]

[CPU benchmarks]("http://i11.photobucket.com/albums/a188/pastymuncher/SyntheticBenchies11.jpg")
[E2200]("http://ark.intel.com/cpu.aspx?groupId=33925")
[E5200]("http://ark.intel.com/cpu.aspx?groupId=37212")
I think that's a well invested 3 quid.

> **Scubdup said:**
> [LIST]
[*]Gigabyte GA-73PVM-S2H - NVIDIA GeForce 7100 graphics chip, HDMI out £57.49[/LIST]
I checked again - there's nothing the Asus board has got on it. Plus, Hardy, Intrepid and Jaunty handle every component of this board out-of-the-box.

> **Scubdup said:**
> [LIST]
[*]Corsair 2GB (1x2GB) DDR2 PC2-5300C5 200-Pin SODIMM Module (VS2GSDS667D2)£20.69[/LIST]
This ram bank works. However, the board supports DDR2 at three clock speeds: 533, 677 and 800 MHz. Your choice, *PC2-5300* runs at 677 MHz. The 800 MHz variant is not only faster, but usually as expensive or cheaper than it's 677 MHz counterparts. Check for *PC2-6400* - you might get lucky and score 2x2048MB, i.e. 4 gig, for roughly the same. (see [DDR2 - wikipedia article]("http://en.wikipedia.org/wiki/DDR2_SDRAM"))

> **Scubdup said:**
> [LIST]
[*]Seagate Barracuda 7200.12 500GB SATA-II 16MB Cache - OEM (ST3500418AS) £43.99[/LIST]In my opinion, this is a good choice. Today, I'd buy Western Digital or Seagate drives only. Sata-II, 16MB Cache, 7200rpm - you've got all of todays standards. [WDC WD6400AAKS-0]("http://www.dclstore.co.uk/desc-western-digital-hard-drive-serial-640gb-udma-300-7200rpm-16mb-oem-wd6400aaks-pid-450.aspx") would be another decent alternative (140 extra gig, same specs, quiet).

> **Scubdup said:**
> [LIST][*]Novatech Opera Media Centre Case FULL SIZE ATX & MICRO ATX + POWER SUPPLY ATX-500W £46[/LIST]Without further research on UK prices, this seems to be a really good buy. Case and power supply for under 50 pounds should be the best the market has to offer. Just make sure it's [ATX 2.X]("http://www.playtool.com/pages/psurailhistory/rails.html") (should be).

The DVD ReWriter also appears a good deal, periphery (keyboard & mouse) are a matter of taste and a TV tuner I have never owned except in a laptop, so I don't have an opinion 'em. Google models for Linux compatibility.

---

### Post by Scubdup on 2009-04-30
Thanks for the frank assessment. The system is still a lot more than I’d like to spend even though it’s pretty much “bare bones”.

I think I need to do more research regarding the “integrated graphics v separate graphics card” debate. I can’t get my head around what graphics capabilities are required and how integrated graphics can match a dedicated card, but I think this is because of gaps in my knowledge.

Re the keyboard choice, I want RF rather than IR to get decent range – I’ve read about problems with IR.

Also, I want the system to be able to do two things – function as a PC and function as a media centre – I know this sounds a bit obvios but… - I want PC input – keyboard and mouse – to be as close to a standard PC as possible, but I want the keyboard to be comfortable and useable as a “laptop remote”.

---

### Post by northern lights on 2009-05-02
> **Scubdup said:**
> The system is still a lot more than I’d like to spend even though it’s pretty much “bare bones”.
You can only do significantly cheaper if you'd let go of the "regular PC" requirement.

> **Scubdup said:**
> Also, I want the system to be able to do two things – function as a PC and function as a media centre.
If you'd just want a media centre, that basically serves no other purpose, you could go with a few pieces of second-hand hardware. Since you want the box to be a decent every-day chores system also, I think you minimized cost already.

> **Scubdup said:**
> I think I need to do more research regarding the “integrated graphics v separate graphics card” debate. I can’t get my head around what graphics capabilities are required and how integrated graphics can match a dedicated card, but I think this is because of gaps in my knowledge.
As far as price is concerned, the on-board chip (i.e. motherborad with integrated graphics combo) is always cheaper than a separate PCI-E graphics device of similar or more power. The Gigabyte board that's currently your/our choice ships at around 60 quid. Check and see what the cheapest board possible (forget the HDMI requirement, for instance, just some board with same CPU socket and all) is sold at - the difference to the 60 quid will never buy you a separate graphics device more powerful than that integrated Geforce 7100 chip.

A separate graphics device has got two advantages:

1. Most integrated chips do not have their own memory, but share some of the system's RAM. If you opt for 2 to 4 GB, 256MB being dedicated to the graphics device will not make a huge difference however. While you thus will not be missing the subtracted graphics memory from your regular RAM, it has to be noted that extra video RAM right on the graphics card's platine is usually a tid bit faster (access speed being advantage 1).

2. High-end graphics chips (significance for Windows gamers is DirectX10 compatibility, for instance) are not available as onboard devices at all. Generally speaking, the more powerful solution always is a separate device. However, since price is a concern to you this is just not an option. If you limit your motherboard search to boards with HDMI, you might find a board for 50 quid (probably won't even do that, but for shits and giggles, let's assume that there is a board with integrated HDMI for 50 quid) - never will you find a graphics card for the difference of 10 that beats the integrated one.

Hence, if you really want to consider a separate graphics device, you'd also have to consider a separate audio controller, in order to have a chance of finding a significantly cheaper board.

Conclusively, despite the additional input I've given above, I don't think you can fare much cheaper without sacrificing a load of computing power.

---


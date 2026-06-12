---
title: "Desktop Freeze after following the guide"
date: 2005-09-15
forum: Desktop Environments
---

### Post by d1337 on 2005-09-15
Maybe not where this post/issue belongs.  If so, my apologies.

A bit of background info, I've had this issue before.  Whether sitting idle or in the middle of working, my desktop will freeze up...no mouse, no keyboard, and I'm not able to go to a terminal or ssh from another machine.  Just lockup & crash.  The only resolution is to power it down hard, which I hate to do.  So, I sent my files that I wanted to keep to another machine, tore this one apart & cleaned/reseated everything.  Started with a clean install last Friday.  Things seemed fine, although I hadn't yet followed the guide to make the machine more usable.  This morning, I decide that it seemed to be stable enough to start seeing if/when it would break.  So, I backed up the whole system (using the method as described in the wiki), scp'd the backup to a remote box for safe keeping, then began to add stuff.  Following the unofficial guide, I changed the repos, apt-get updated, apt-get upgraded and apt-get dist-upgraded (mozilla firefox was holding back, so I apt-get upgrade -f to force it).  Seemed fine so I started adding a few bits...first gkrellm and a skin for it.  Seemed to work okay, so I started down the list in the guide with what I wanted, but only got through smeg & partially through java before it froze on me.

Box is nothing special and I have allowed memtest to make 4 passes to insure that my Ram isn't goofing.  It's a dual boot and I can't seem to make it have a problem in XP...so I'm thinking that I've broken something by adding the repos or it's choking on something with gkrellm.  But these additions went smoothly with nothing appearing to be out of the ordinary.

I'm using  2.6.10-5-686 and this may be helpful as well
```
lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

```

Any ideas?
d1337

---

### Post by mlomker on 2005-09-15
What are you dist-upgrading to?  Breezy?  It's a beta...stick with Hoary if that's the case.

---

### Post by d1337 on 2005-09-15
No...not to Breezy (yet).  When I apt-get upgraded, it lists 4 packages being kept back (all 4 related to mozilla-firefox).  When I apt-get dist-upgraded, these packages were the only listed upgrades.  Firefox shows to be v 1.0.6 now, but perhaps I should have left these 4 packages back?

---

### Post by mlomker on 2005-09-16
[QUOTE=d1337]No...not to Breezy (yet).  When I apt-get upgraded, it lists 4 packages being kept back (all 4 related to mozilla-firefox).  When I apt-get dist-upgraded, these packages were the only listed upgrades.  Firefox shows to be v 1.0.6 now, but perhaps I should have left these 4 packages back?[/QUOTE]

I doubt that was it.  

You say in your post that you are unable to Ctrl-Alt-F2 to another terminal when it crashes?  If that's the case then this is a hardware problem, even if it isn't your memory.  Troubleshooting those kind of things can be a pain because sometimes it comes down to replacing one part at a time.  I did hardware support for a few years and you develop a feel for what the problem might be, but there's more guesswork to it than I liked.

Have you started with the basic stuff like cooling fans and double-checking your processor heatsink?  Dried-out heat-sink paste is a common problem...you need good heat transfer to the heatsink

---

### Post by d1337 on 2005-09-16
When the problem first reared it's ugly head, I thought power supply, so I installed a new psu.  Thought my 40G hd that I had Ubuntu on was freezing, so bought a new hd as well.  When I cleaned and reseated everything, I also pulled the heat sink, blew out the fan, added my arctic silver like always.  For cooling, this case is overkill for this system with 3X80mm plus the fan on the heatsink.  I'm down to thinking that the cpu or the board may be failing, which may give me an excuse to purchase more toys.  Strange thing is, it has only froze that one time yesterday when it was freezing 6-10 times daily before.  I'll give it some more time and see.  Thanks for your help and insight.

d1337

---


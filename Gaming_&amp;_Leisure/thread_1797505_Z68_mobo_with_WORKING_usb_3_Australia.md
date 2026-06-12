---
title: "Z68 mobo with WORKING usb 3 Australia"
date: 2011-07-05
forum: Gaming &amp; Leisure
---

### Post by Jagoly on 2011-07-05
I'm planning a build for a new desktop system. I don't play many games, instead doing a lot of other intensive work.

For this reason, I've decided to use the HD Graphics 3000 on the i7-2600k, saving $$$ on a discreet GPU and spending $$$ on epic cpu cooling for a major overclock.

For this reason, I need a Z68 board. I've also worked out a setup involving a lot of HDD's (and an SSD), for which I need at least 2 SATA 3 ports, preferably four for future-proofing.

Problem is 90% of the boards (under $250) you can get in Australia use Etron or ASMedia usb 3 controllers, which don't work in linux.

My dream board would be the MSI Z68A-GD65 with a NEC controller; BUT I CAN NOT FIND IT ANYWHERE IN AUSTRALIA. It doesn't even show up on myshopping.com.au

My second choice is the the Z68A-GD80; but it costs 40% more and has LESS features that are useful to me (esata3 replacing on sata3, designed for SLI/Crossfire setups). I can find this board in a few places, but I don't want it. I want the other one.

So, the question, does anyone know of any other way to acquire one? overseas dealers that ship internationally, ect.

:confused:

---

### Post by An Sanct on 2011-07-05
Hi there!

Could you elaborate a little on why USB 3.0 should not work in Linux?

---

### Post by Jagoly on 2011-07-05
there are no drivers as far as I know

---

### Post by An Sanct on 2011-07-05
Linux was the first OS to support USB3 :) there should be native kernel support.

My USB 3.0 works well (mobo: asus p7p55d pro) came with a fully bloated DVD, full of windows drivers. The Linux support folder had a text file that said "use kernel above 2.3*.something*"

---

### Post by Jagoly on 2011-07-05
that board uses an NEC usb3 controller. Go have a look at the latest asus 1155 boards, the all use asmedia controllers, gigabyte and asrock use etron.

NEC provides drivers, asmedia and etron do not:(

USB 3 isn't part of any of intel's chipsets yet, so third-party controllers are required.

EDIT: And ALL of MSI's boards still use NEC:)

---

### Post by An Sanct on 2011-07-05
This might be of interest for you (bug: marked as fixed)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802541](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802541)

Also take a look [here]("http://www.spinics.net/lists/linux-usb/msg47791.html") and [here]("http://www.linux-archive.org/ubuntu-kernel-team/544990-etron-usb-3-0-controller.html") (sorry :) I was to lazy to read it all ...)

Well, the patch should be in the kernel soon ... in Oneiric, at least... Sorry to hear that, I did not know there was such a "war" between manufacturers of USB 3.0 ...

---

### Post by Jagoly on 2011-07-05
Thanks. I suppose that it's good to know that that we'll get support eventually.

Perhaps I will go with one of the Gigabyte board after all. heck, I'll probably never even use usb 3. I just don't like the idea of forever having a bunch of completely useless ports on my :KSperfect:KS rig.

Also a lot of cases, including the one I have chosen, have usb 3 ports on the front. It would really suck if they didn't work.

---

### Post by Jagoly on 2011-07-05
OOOHHHHHH.......

this board only was released less than three weeks ago...
](*,)
that explains why I can't find it anywhere...
](*,)

---

### Post by CosmicVoyager on 2011-09-18
I'm using a Gigabyte motherboard with an Etron USB 3.0 controller and it is not working.

The Ubuntu 11.04 installer does not show the USB 3.0 drive.

What is wrong?

How do I fix it?

---

### Post by Jagoly on 2011-09-18
That's The problem. The Etron Drivers aren't in the kernel yet, but will be in the 3.0 kernel. So the ports should just start working once 11.10 comes out.

---

### Post by maul9999 on 2011-09-18
> **Jagoly said:**
> I'm planning a build for a new desktop system. I don't play many games, instead doing a lot of other intensive work.

For this reason, I've decided to use the HD Graphics 3000 on the i7-2600k, saving $$$ on a discreet GPU and spending $$$ on epic cpu cooling for a major overclock.

For this reason, I need a Z68 board. I've also worked out a setup involving a lot of HDD's (and an SSD), for which I need at least 2 SATA 3 ports, preferably four for future-proofing.

Problem is 90% of the boards (under $250) you can get in Australia use Etron or ASMedia usb 3 controllers, which don't work in linux.

My dream board would be the MSI Z68A-GD65 with a NEC controller; BUT I CAN NOT FIND IT ANYWHERE IN AUSTRALIA. It doesn't even show up on myshopping.com.au

My second choice is the the Z68A-GD80; but it costs 40% more and has LESS features that are useful to me (esata3 replacing on sata3, designed for SLI/Crossfire setups). I can find this board in a few places, but I don't want it. I want the other one.

So, the question, does anyone know of any other way to acquire one? overseas dealers that ship internationally, ect.

:confused:

You might want to check it out Gigabyte website because they have NEC controller.  I have GA-H55-USB3 and it is all i need in order to get USB 3.  Also you can add SATA PCI or PCIE card.

---

### Post by Jagoly on 2011-09-19
some boards do have NEC controllers, most of Gigabyte's older boards as well as their high end boards. But a lot of them have etron controllers.

So yeah check Gigabyte's website for what's on you're board.

lspci may help too.

---

### Post by maul9999 on 2011-09-19
> **Jagoly said:**
> some boards do have NEC controllers, most of Gigabyte's older boards as well as their high end boards. But a lot of them have etron controllers.

So yeah check Gigabyte's website for what's on you're board.

lspci may help too.

Yeah. NEC is great for my computer.  It have driver download on website i think.

---

### Post by CosmicVoyager on 2011-09-19
> **Jagoly said:**
> That's The problem. The Etron Drivers aren't in the kernel yet, but will be in the 3.0 kernel. So the ports should just start working once 11.10 comes out.

I downloaded 11.10 beta. Ubuntu sees the USB 3.0 disk for the first time, and I am able to install. But when I restart, it does not boot.

---

### Post by Jagoly on 2011-09-19
That's probably because of a problem with 11.10. It's not finished yet, remember.

I'm unsure what situation you're in at the moment; I would think that you don't need to use the usb 3 ports. And 11.10 comes out in less than a month.

---

### Post by maul9999 on 2011-09-19
> **Jagoly said:**
> That's probably because of a problem with 11.10. It's not finished yet, remember.

I'm unsure what situation you're in at the moment; I would think that you don't need to use the usb 3 ports. And 11.10 comes out in less than a month.

There is no such ubuntu 11.10. just 11.04.

---

### Post by Jagoly on 2011-09-19
> **maul9999 said:**
> There is no such ubuntu 11.10. just 11.04.

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview)

---

### Post by maul9999 on 2011-09-19
Ah i get it.  Do you know the risk of beta is right?  Beta is not design to be ready for stable Operation System.

---


---
title: "Installing Ubuntu on Dell Dimension XPS R450"
date: 2007-07-10
forum: Dell  Ubuntu Support
---

### Post by MSP1 on 2007-07-10
I have an old Dell Dimension XPS R450 from which I have evicted Windows 2000 Pro so that I can try Ubuntu. It has 256Mb of memory and an 8Gb disk.

All I want is a simple system to run open office to do some word processing. I don't know much about computers but I think I have followed all the instructions.

I downloaded ubuntu-7.04-desktop-i386.iso and checked the hash value which was OK, burnt the CD and booted from it. I then used the check media option on the Ubuntu boot menu and got an OK report there too.

Next I selected the start Ubuntu in “safe graphics mode” as this seemed the least risky option.

After 90 mins of the CD drive thrashing away a grey dialogue appeared on a yellowish background indicating that something called “GNOME” had had some incomprehensible problem and did not appear to have understood the “last message” it had, or had not received. 

Soon after this the screen went blank but the CD drive continued to thrash away. A further 4 hours or so later a text screen appeared with various “startup” messages on it. The last one of these was “Running local boot scripts”. Soon after this another error message appeared saying that something called “X Server” had got itself in a bit of a state and asking if I would like to diagnose the problem. Not being a computer doctor I declined as the keyboard was functional. The CD light flashed a few more times and then everything went dead.

I have now been through the same process twice with identical results from two different copies of the CD.

As I say I don't know much about computers but I assume it is not supposed to behave like this. Any idea what is wrong?

---

### Post by Ek0nomik on 2007-07-10
> **MSP1 said:**
> I have an old Dell Dimension XPS R450 from which I have evicted Windows 2000 Pro so that I can try Ubuntu. It has 256Mb of memory and an 8Gb disk.

All I want is a simple system to run open office to do some word processing. I don't know much about computers but I think I have followed all the instructions.

I downloaded ubuntu-7.04-desktop-i386.iso and checked the hash value which was OK, burnt the CD and booted from it. I then used the check media option on the Ubuntu boot menu and got an OK report there too.

Next I selected the start Ubuntu in &#8220;safe graphics mode&#8221; as this seemed the least risky option.

After 90 mins of the CD drive thrashing away a grey dialogue appeared on a yellowish background indicating that something called &#8220;GNOME&#8221; had had some incomprehensible problem and did not appear to have understood the &#8220;last message&#8221; it had, or had not received. 

Soon after this the screen went blank but the CD drive continued to thrash away. A further 4 hours or so later a text screen appeared with various &#8220;startup&#8221; messages on it. The last one of these was &#8220;Running local boot scripts&#8221;. Soon after this another error message appeared saying that something called &#8220;X Server&#8221; had got itself in a bit of a state and asking if I would like to diagnose the problem. Not being a computer doctor I declined as the keyboard was functional. The CD light flashed a few more times and then everything went dead.

I have now been through the same process twice with identical results from two different copies of the CD.

As I say I don't know much about computers but I assume it is not supposed to behave like this. Any idea what is wrong?

Actually, that *is* Ubuntu.  It's fun and user friendly, wouldn't you say?







**Just kidding**.  I have used the Desktop version to install Ubuntu on two of my computers, but for the third I had to use the Alternate CD.  I would try that if I were you, as it sounds like the Live CD is giving you a heck of a time.  The Alternate CD is a simple text based installer.  It's just as easy, and it walks you through step by step, so you shouldn't have any problems with it.

On the page where you download Ubuntu, there is a check box to download the Alternate instead of the Desktop.  Let me know how it goes.  :)

---

### Post by MSP1 on 2007-07-10
Hi Ek0nomik

Thanks for the reply. I'll try what you suggest.

The funny thing is that I have just dug out a copy of a Puppy Linux CD and that works without any problems!

I'll post again when I have had time to try your suggestion.

---

### Post by jrusso2 on 2007-07-10
I recommend the Xubuntu alternate cd.  I think you would have a better performing system with Xubuntu.

---

### Post by Ek0nomik on 2007-07-10
> **MSP1 said:**
> Hi Ek0nomik

Thanks for the reply. I'll try what you suggest.

The funny thing is that I have just dug out a copy of a Puppy Linux CD and that works without any problems!

I'll post again when I have had time to try your suggestion.

That doesn't surprise me that another distribution worked.

Let me know how the Alternate CD goes.

> **jrusso2 said:**
> I recommend the Xubuntu alternate cd.  I think you would have a better performing system with Xubuntu.

His computer has the requirements for Gnome.

---

### Post by MSP1 on 2007-07-11
OK. I downloaded the "alternate" CD and that managed to install the system.

The only problem is that it did not pick-up the network card nor the sound hardware.

I had to give up on following the installer's advice after it failed to find the network interface as it kept taking me round in circles! I opted to "configure it later" but I can not find a control panel for doing that. The "system.network" control panel does not seem to help.

Both the sound and network worked OK with Windows 2000 and Puppy Linux.

Any ideas how to get the sound and network to work?

One more thing. For the past 57 years my name, which I always use as my user name, has begun with a capital letter. I'm just a little miffed that ubuntu (see I'm getting my own back)) will not let me spell it correctly! If it has some obscure implementation dependent reason for having user names in lower-case it should keep them to itself and perform appropriate conversions in and out of the user interface. It's small things like this that put people off computers. User interfaces should always be oriented towards the user and never towards the implementation.

---

### Post by xosher on 2007-07-13
> **MSP1 said:**
> I have an old Dell Dimension XPS R450 from which I have evicted Windows 2000 Pro so that I can try Ubuntu. It has 256Mb of memory and an 8Gb disk.

Wow, that's weird.  I have almost the same setup.  I purchased a new Maxtor HDD from Office Depot (80 GB with a $60 rebate) and switched it for the smaller drive.  Bought Win XP Home through Ebay (the Win 2K machine was a gift from a coworker and she didn't have the serial number for the OS anymore). Split the hard disk into 2 partitions.  Dual boots XP and Feisty with no problem (except for the @#$%* num lock key not turning on after boot).

> All I want is a simple system to run open office to do some word processing. I don't know much about computers but I think I have followed all the instructions.

I downloaded ubuntu-7.04-desktop-i386.iso and checked the hash value which was OK, burnt the CD and booted from it. I then used the check media option on the Ubuntu boot menu and got an OK report there too.

Same here.  Had some trouble turning the download into an .iso, but finally got it going after some tinkering with Nero.

> Next I selected the start Ubuntu in “safe graphics mode” as this seemed the least risky option.

After 90 mins of the CD drive thrashing away a grey dialogue appeared on a yellowish background indicating that something called “GNOME” had had some incomprehensible problem and did not appear to have understood the “last message” it had, or had not received. 

Soon after this the screen went blank but the CD drive continued to thrash away. A further 4 hours or so later a text screen appeared with various “startup” messages on it. The last one of these was “Running local boot scripts”. Soon after this another error message appeared saying that something called “X Server” had got itself in a bit of a state and asking if I would like to diagnose the problem. Not being a computer doctor I declined as the keyboard was functional. The CD light flashed a few more times and then everything went dead.

I have now been through the same process twice with identical results from two different copies of the CD.

As I say I don't know much about computers but I assume it is not supposed to behave like this. Any idea what is wrong?

Did you wipe your hard disk before installing Ubuntu?  "Darik's Boot & Nuke" is a good disk scrubbing utility.

Have you tried running the disc as a Live CD first?  That's what I did after installing XP.  (Gave Ubuntu a spin, liked it well enough and then rebooted with the CD still in my drive.)  Selected the first option - install, and went through five or six steps.  Had some trouble with the swap file creation, but otherwise everything went OK.

Took out the CD, rebooted, and got a menu selection to boot either Ubuntu or XP.  Pretty cool.

Hope that helps,

J

---

### Post by MSP1 on 2007-07-14
Well as I said in my last post I got it working using the "Alternative" CD, not the "Live" one.

However, I still have not found out how to make it recognise the sound and network hardware. The sound seems to be part of the mother board but I have not managed to work out what sort of network card it uses as I no longer have the original documentation.

---

### Post by xosher on 2007-07-14
> **MSP1 said:**
> Well as I said in my last post I got it working using the "Alternative" CD, not the "Live" one.

However, I still have not found out how to make it recognise the sound and network hardware. The sound seems to be part of the mother board but I have not managed to work out what sort of network card it uses as I no longer have the original documentation.

Oops-mea culpa.  I didn't scroll all the way down.

Here's my factory setup:

Motherboard Name= **Intel Seattle SE440BX (2 ISA, 4 PCI, 1 AGP, 3 DIMM)**
Audio Adapter= **Aureal Montego Sound Card** *(or maybe a Turtle Beach Montego)*
Network Adapter= **3Com EtherLink XL 10/100 PCI TX NIC (3C905B-TX)**

Don't know how much help this will be, but it never hurts to look:
[http://support.3com.com/infodeli/tools/nic/linuxdownload.htm]("http://support.3com.com/infodeli/tools/nic/linuxdownload.htm")

:confused:It's certainly a stumper all right.  A-googlin' I go...

---


---
title: "Serious Boot Problems"
date: 2006-08-18
forum: Desktop Environments
---

### Post by venkatachar on 2006-08-18
Hi,
 My computer dosent boot up after installing ubuntu 6.06. The the cpu fan is running and the red/green light glows, but the monitor dosent display anything. 

Is this the problem of BIOS? If yes how to reset the BIOS.(I havent  upadated/changed the BISO since I bought my computer)

My Motherboard -- Asus A7n266-vm
CPU -- AMD XP 2000+
Ram -256MB

Thanks

---

### Post by musther on 2006-08-18
This doesn't sound like anything Ubuntu could have done, are you sure nothing is displayed at all, no info from your graphics chip, no bios info?

If this is the case (and you've tried unplugging your box for a few minutes) then the way to diagnose what's wrong is to start pulling things out.  A good solid way to reset the bios it to take out the battery which is found on the motherboard (a little round shiny one), it must be left out for a couple of minutes.  After that try unplugging hard drives, other drives, cards, RAM etc, sooner or later if you're lucky, you'll get something when you turn it on, then you may be able to figure out what's wrong.

I understand that you may not be comfortable pulling apart your PC, so it may be a good time to go to a decent computer shop.  Before you do though, try turning everything off, unpluggging it all for a while, then putting it back together and powering it up.  

Let us know what happens.

------EDIT------
Of course it could be the monitor.

---

### Post by venkatachar on 2006-08-18
Thanks for your reply. I tried removing the CMOS battery, cleaning the jumpers, pulling out the PCI cards etc. But these things did not work.

My hunch is that the BIOS is currupted because every time i booted my computer would BEEP,but thats not happening now and the HDD LED(red) will alaways be glowing.

So is there any other way to reset BIOS apart from removing the CMOS battery.

---

### Post by musther on 2006-08-18
---EDIT---
Before you read what's below I'll clarify (just in case), in order to reset the BIOS, you need to take out the battery *while* the machine is unplugged.
----------

Removing the battery will completely reset it.  So to be clear, you're not getting any beeping when you turn on the machine?  

The HDD light being always on can happen if you have the IDE cable the wrong way round (often not possible on modern ones), but as you havn't taken it out of played with it that can't be it.  

If you're confident playing around inside your PC, try disconnecting all drives from the motherboard, taking out all cards but your graphics, and disconnecting all devices (keyboard, mouse, printer etc) except the monitor, then power on the machine and see if you see anything or get any beeps.  If you see something then your basic system (motherboard, RAM, CPU etc) is working, if not, try removing all but one stick of RAM (if you have more than one) see if you get any beeps.  Finally, if all else fails, take everything off your board, so you have a motherboard with power going to it and the speaker, switches and LED's connected, power it on and see if it beeps.  If at this point you're having no luck it could be that your motherboard or some other important thing (CPU, RAM etc) is dead and you'll have to begin testing your components in another machine (test the hard drive, cards, RAM etc) of course this requires access to another machine.  

I know this sounds silly, and I know I mentioned it before, but have you tested the monitor?

Hope you have some luck, if not post back.

---

### Post by venkatachar on 2006-08-18
Thanks for your advice. Will try removing each component in CPU as you have mentioned and check,  including the monitor

---


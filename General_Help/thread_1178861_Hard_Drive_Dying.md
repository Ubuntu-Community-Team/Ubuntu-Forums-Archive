---
title: "Hard Drive Dying??"
date: 2009-06-05
forum: General Help
---

### Post by Bucky Ball on 2009-06-05
Hi all,

Desktop computer has started doing something a little odd. Using Ubuntu and all is well, suddenly mouse stops working (can't move cursor) and keyboard dies and num lock and caps lock start flashing on and off. Nothing to do but hit the restart button on the box and all is well ... for awhile. Not related to using any app,, just happens at random (even just at the desktop, nothing running as such).

I dual boot this machine so boot into XP and see if that throws any light on the problem. Working away fine and thinking it must be the Ubuntu install needs tweaking when the machine restarts of its own accord! Guess this is a Windows response to the problem as opposed to the lock up/lights flashing of the Ubuntu response. 

I am presuming this is definitly a hardware problem, just wondering if someone can shed some light on what. I am leaning toward dying hard drive. What do people think? Any test I can run to check the health of all hardware in the box?

Cheers and thanks in advance, Ubuntu-ers!

ps: The keyboard is really (really) old; could it be that?

---

### Post by Ocxic on 2009-06-05
It's effecting 2 separate OS's so it's defiantly a hardware issue. you can check your hard drive with utilities from the manufacturer, usually they can be downloaded for free.
I would also use memtest(can be accessed from the grub boot menu) to check your RAM, as a bad memory module can cause weird issues.
I seriously doubt a keyboard could cause this issue, but you could always try a different one to check.

---

### Post by dcstar on 2009-06-05
> **Bucky Ball said:**
> Hi all,

Desktop computer has started doing something a little odd. Using Ubuntu and all is well, suddenly mouse stops working (can't move cursor) and keyboard dies and num lock and caps lock start flashing on and off. Nothing to do but hit the restart button on the box and all is well ... for awhile. Not related to using any app,, just happens at random (even just at the desktop, nothing running as such).
........
I am presuming this is definitly a hardware problem, just wondering if someone can shed some light on what. I am leaning toward dying hard drive. What do people think? Any test I can run to check the health of all hardware in the box?
.........

Linux pushes hardware far harder than Windows - RAM that works fine in Windows fails in the Linux RAMTEST as well as during normal use.

Check your CPU temp (and open your box and clean out dust from the heatsink/fan) to see that things aren't overheating.

---

### Post by Bucky Ball on 2009-06-05
Okay, I ran the memtest and crash it did. I am looking at a screen full of red and blue coloured rectangles (big red block at bottom, rest blue).

The test was working fine until 54% of pass 22 then it just stopped and gradually deteriorated from there. Could have been the system locking up due to something else though. Question is, was it the ram that caused the crash or the hard drive?

---

### Post by dcstar on 2009-06-05
> **Bucky Ball said:**
> Okay, I ran the memtest and crash it did. I am looking at a screen full of red and blue coloured rectangles (big red block at bottom, rest blue).

The test was working fine until 54% of pass 22 then it just stopped and gradually deteriorated from there. Could have been the system locking up due to something else though. Question is, was it the ram that caused the crash or the hard drive?

Memtest tests memory, it has nothing whatsover to do with any hard drives.

---

### Post by mcduck on 2009-06-05
> **dcstar said:**
> Linux pushes hardware far harder than Windows - RAM that works fine in Windows fails in the Linux RAMTEST as well as during normal use.

Check your CPU temp (and open your box and clean out dust from the heatsink/fan) to see that things aren't overheating.

Linux doesn't push it any harder, it's just that Linux tends to stop working if your hardware isn't working correctly, while Windows keeps on running but crashes more and possibly corrupts your data over time..

Anyway, for the original poster. Even a single reported error in memtest is a definite sign of faulty RAM, broken memory slot or compatibility problem with your RAM and chipset. In most cases it's faulty RAM.

If the memtest crashes completely you *definitely* have a *serious* problem with your RAM. (And no, it's not likely to be anything else. After memtest is started it doesn't access your hard drive, and the stress for anything but the RAM is neglible).

---

### Post by yaddoshi on 2009-06-05
> **Bucky Ball said:**
> Okay, I ran the memtest and crash it did. I am looking at a screen full of red and blue coloured rectangles (big red block at bottom, rest blue).

The test was working fine until 54% of pass 22 then it just stopped and gradually deteriorated from there. Could have been the system locking up due to something else though. Question is, was it the ram that caused the crash or the hard drive?

Hi Bucky,

I've been a PC repair tech for about a decade now - and it is very rare, but not impossible, for bad memory to cause a computer to freeze during a RAM test.

You most likely have one of three problems, and you can open your PC to check at least two of them.  Here are the most likely causes of your problem:

1) You are overheating - check to make sure all of your fans are spinning - especially the fan on your processor, video card (if any), motherboard (if any) and power supply.  Even if they are spinning, if they are clogged with dust, or the heatsink they are mounted on is clogged with dust, that is the most likely source of your problem.  If they are not spinning, are spinning slowly, or are noisy, replace them.

2) You have a part with blown capacitors - typically these are found on the motherboard, but they could also be on your video card.  Capacitors look sort of like small batteries, and they should be cylindrical in shape with a flat top.  If any of your capacitors have a bulging top or are leaking/encrusted with something - they are "blown" and you will typically pay more to have them replaced than it would cost to replace the entire part.  If you know someone who is VERY handy with electronics soldering, however, you might be able to repair the problem by replacing the blown capacitors (I personally am not that handy - I usually just replace the part).

3) Your power supply is beginning to fail or is overloaded due to hardware upgrades it cannot handle - you can call your local PC repair shop to see how much it would cost to have your power supply tested.  Most of the time a bad power supply will prevent a computer from starting up, but occasionally it will cause overheating and other strange issues so it is worth checking.  Also, you can check to make sure you have sufficient wattage available for the parts in your system at this site:
[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

This wattage calculator isn't foolproof, but it should give you a good idea of how much wattage your system needs.  You can usually find how much wattage your power supply will provide on the label attached to the side of the power supply, although in some cases you will have to remove the power supply to see the label.  Removal is usually a simple matter of unscrewing four screws.

Based one what you have written it is very unlikely that you have a failing hard drive, but I wouldn't rule it out completely.  If you are able to get your system running better than it is now, I would take the opportunity to make backups of your data, and possibly bring it in to get checked out at a reputable repair shop.  (Avoid The GeekSquad @ Best Buy, and check out your local repair shop ratings at [http://www.bbb.com](http://www.bbb.com)).

---

### Post by Yellow Pasque on 2009-06-05
> and it is very rare, but not impossible, for bad memory to cause a computer to freeze during a RAM test

This actually happened to me recently. It's more likely if the bad stick is in the first RAM slot.

OP: if you have multiple RAM sticks, now would be a good time to try just running with one or at least swapping slots. Make sure you label the sticks, so you know which one is which. Also, make sure your cooling vents and especially, the CPU heatsink, aren't clogged with dust. Closely monitor the temp of the CPU. P4's generally run hot.

---

### Post by Bucky Ball on 2009-06-05
Okay, thanks one and all for the advice.

I will make a coupla things clear and save everyone some typing: I built this machine and have built about a dozen others with cool, clean, energy-efficient, environmentally friendliness top priorities. The inside of the case is blown out a couple of times a year (gently) with a can of compressed air, the PSU was just about the and most reliable and energy efficient at the time and is nowhere near its 'use by' date (Coolermaster iGreen 500w, up to 85% efficiency, RoHS compliant, MTBF 400, 000 hours), so no; PSU, cooling and dust etc are not an issue here. I am very aware of these things. (I will be posting a guide to building a clean, green, energy-efficient computing machine during my uni holidays based on a build I did over christmas). 

So, I'll take RAM for four 512mb sticks, thanks! I'll test 'em one by one and see what I come up with. Odd a stick should just 'break' for no real reason if this is the problem though ... but guess that happens.

In other words, fine with taking the thing apart and putting it back together again if that is required, but think I'll just replace mb if my capacitors are bulging (is that a toffee in your pocket or just your capacitor bulging?). Anyhow, I'll have a poke about on the strength of everyone's advice and report back.

Cheers :)

ps: Arctic Silver thermal paste on the P4 in there and custom CPU fan (Thermaltake Silent 775D) - believe me, this thing has been rock solid hardware-wise since the first time I turned it on. Ambles along around 38 degrees celcius from memory, MB and CPU. It has literally gone down over time rather than up; the thermal paste takes around 50 cycles from hot to cold to reach full cooling potential. Started round 42 degrees I think.

---

### Post by Bucky Ball on 2009-06-05
... just while I think of it ...

If this is a RAM problem, why am I not getting the appropriate beep code to tell me something is wrong at boot?? Could this be cos three are working and one's a dud, so things are okay til it misfires on the dead cylinder/ram stick?

Maybe I am leaning toward HD. That is the only IDE drive in the box with both OSs on it and it is old so I have been half expecting it. I'll investigate.

---

### Post by egalvan on 2009-06-05
> **Bucky Ball said:**
> ... just while I think of it ...

If this is a RAM problem, why am I not getting the appropriate beep code to tell me something is wrong at boot?? Could this be cos three are working and one's a dud, so things are okay til it misfires on the dead cylinder/ram stick?

Maybe I am leaning toward HD. That is the only IDE drive in the box with both OSs on it and it is old so I have been half expecting it. I'll investigate.

The BIOS memory "test" is a very simplistic test, more designed to see if memory is physically present.

Teacher "RAM ?"
Student "Here"

This is why* memtest* has so many different types of test modes.
Memory can fail in may different ways.


Drill Sergeant "RAM!"
PFC "Present"
Drill Sergeant "Drop and give me twenty, then a five mile run, then a ten mile hike to cool off, full kit, let's end at the firing range! Move it!"



Look into the technical aspect of* memtest *to find out more on the philosophy of testing memory

---

### Post by Sef on 2009-06-05
>  Look into the technical aspect of* memtest *to find out more on the philosophy of testing memory

[Memtest site]("http://memtest86.com/")

---

### Post by Bucky Ball on 2009-06-05
Now starting to remember where I got to when this was happening awhile ago.

Switch on computer, doesn't switch on keyboard or monitor. Just black screen. DVD/CD drive just clicks over (active, maybe looking for something?). Hit restart button, but the machine shuts down. Three or four seconds later it boots again, but not for long, then shuts down. Then reboots and ... black screen, gone full circle. And that is where I am at now, six weeks later (it did it once or twice awhile ago but has been getting more frequent; I don't use that machine everyday, so .. ).

This is making me think hard drive still. If I could get it to boot into anything, I could run smartmontools? That might dig up something. Does this sound like RAM still? Like I say, that IDE drive is pretty old.

---

### Post by snkiz on 2009-06-05
I've had two old hard drives fail under Ubuntu. In both cases log files show a I/O error on /dev/sdx (x being the drive in question a,b,c..) even had an old floppy crap out with the same error on /dev/fd0 so what do the logs say?

---

### Post by Bucky Ball on 2009-06-05
Crawling toward a conclusion.

Booted up the desktop this morning. Same thing, blank screen, no keyboard or mouse. Doesn't do anything but the box is on. CD drive clicking away so thought I'd unplug that, see if there's any difference. Nothing still. Plug optical drive back in, boot, same; optical drive clicking away and while I am pondering my next step, low and behold, it stops clicking and hits the grub menu! So I boot into the recovery kernel and drop to a root shell.

I quickly boot up my laptop to remind myself how to run smartmontools so I can check the hard drives on the desktop. I find the appropriate commands and head back to the desktop only to find that ... you guessed it ... the keyboard had quit functioning. No flashing num and caps lock lights; nothing. Next step? Who knows? RAM? Starting to wonder. I might start fiddling with that after I've tried a different keyboard. I have my doubts about the RAM being the problem as:

a) There are no untoward error beeps at start-up
b) The machine seems to run perfectly fine until the random lock-up and
c) I've never known RAM to just die when sitting in the box untouched (although I do know it to die when it has been pulled out and shoved back in and generally knocked about or shorted)

I understand what was said earlier about once you put the RAM under some workload, you are more likely to find a problem, but what about just sitting at a command prompt doing absolutely nothing and under little pressure, locks up? If the keyboard would stay up for long enough I would check out the drives once and for all but alas, no such luck to this point. Any further wisdom?


* UPDATE: I unplugged the IDE (OS) drive to try and get into the BIOS and boot from Gparted LIVE CD but no different. I think I can safely rule out that IDE drive. So back to the RAM. The one not-good thing about my box is the box itself! Small, pokey, fiddly and taking the RAM out is truly a hassle, but ... tried all other obvious tactics so here goes ...

---

### Post by Bucky Ball on 2009-06-06
Latest: Probably complete coincidence; I unplugged my external SATA drive which hasn't been switched on through this whole exercise so shouldn't make and difference, and the machine booted fine straight away.

I installed smartmontools and did a short test and a few other things on the IDE drive and the three SATA drives. All passed everything and fine, at least for the short test. Went back to the laptop (doing two things at once as usual) and when I returned to the desktop, sure enough, frozen again. 

Just for something different, could this be a graphics card problem? Normally the monitor doesn't switch on at boot (or any other peripherals) and if I do manage to get to a desktop for awhile, the monitor 'freezes', mouse and keyboard stop working eventually.

This time around it lasted about thirty minutes.

Ya see, I want to get this correctly identified before I go spend money on buying the wrong component. Tomorrow I will finally start diddling with the RAM sticks and finally rule that in or out.

---

### Post by Bucky Ball on 2009-06-12
Here's the current state of play.

I took the RAM out (all but one in slot one) and booted the machine. Nothing. No connection with screen, keyboard, mouse. Box just sits there humming.

Swapped the sticks over, same result. So, I've checked RAM, smartmontool-ed the hard drives. Could we start to imagine processor? P4 hyperthreader from yesteryear but fine for that machine, possibly until now. Or graphics card? I don't have another to try. Looks like I might have to take this to the computer shop! Agh! I have built and fixed my own for ages, this is gonna be weird ...

It did something new before it finally died and stopped communicating with the peripherals, keyboard and mouse. It said "Grub loading ... Grub Error 17." That was completely new. It had been switching on and acting fine, then locking randomly, or whirring the hard drives but not switching the monitor on. 

All suggestions welcome. I have a bit more time now to experiment. :)

---

### Post by Bucky Ball on 2009-06-12
Okay, I think I've nailed the problem. 

I had four sticks of 512mb in the four slots. I took them all out but the one in slot 1, booted. Nothing.
I tried another stick in slot one. Nothing
I tried a stick in slot 3. Something! The machine booted as per normal and ran for about an hour and twenty minutes without a hitch. I switched off and put a different stick into slot 1 (stick 3) as well as having a stick in slot 3(!). Nothing.

Took the stick out of slot 1, something!

So, could it be that slot one has died? This is unusual? This seems to be the problem from what I can deduce. This, I assume, calls for a new motherboard.

** Update: Yep, got RAM in slot 2 & 4 now and all seems to be fine for the moment. See how it goes.

---

### Post by factorgaming on 2009-06-12
I would think that it could be caused by the defective RAM

---

### Post by Bucky Ball on 2009-06-12
> **factorgaming said:**
> I would think that it could be caused by the defective RAM

Well, I don't think you read my last post very well. :)

I am typing from said machine and it has been up for two hours, not a problem. Please read my last post again, it is definitely not the RAM (three sticks failed in slot 1 but worked in slots 2, 3 and 4; I currently have sticks in 2 and 4 and it's fine).

---

### Post by wpshooter on 2009-06-12
> **Bucky Ball said:**
> Okay, I think I've nailed the problem. 

I had four sticks of 512mb in the four slots. I took them all out but the one in slot 1, booted. Nothing.
I tried another stick in slot one. Nothing
I tried a stick in slot 3. Something! The machine booted as per normal and ran for about an hour and twenty minutes without a hitch. I switched off and put a different stick into slot 1 (stick 3) as well as having a stick in slot 3(!). Nothing.

Took the stick out of slot 1, something!

So, could it be that slot one has died? This is unusual? This seems to be the problem from what I can deduce. This, I assume, calls for a new motherboard.

** Update: Yep, got RAM in slot 2 & 4 now and all seems to be fine for the moment. See how it goes.

Make sure that you try ALL 4 of the sticks in slot 1 before you assume that it is bad.  

Have you taken your canned air and blew directly into all of the slots.  Give them time to dry completely before re-inserting the RAM.  

Also, when you are putting the modules into the slots make sure that you sort of rock them by alternately pushing on one end and then the other when doing the insertion before you pull the locking tabs up firm.

P.S. - Assuming that slots 1 & 3 work together & slots 2 & 4 work together.

---

### Post by wpshooter on 2009-06-12
Also, what the the brand name of your IDE drive ?

---

### Post by Bucky Ball on 2009-06-12
WPShooter, nope, 1 doesn't work at all, but 3 works by itself, but when I add a stick in 1, nothing works. Pull it out, 3 works by itself. I currently have stick in 2 & 4. 

Not sure how dust would have gotten into the slot when the RAM has been sitting in there and everything working fine for the last four years. It just started doing this out of nowhere. Three sticks failing in slot one is pretty convincing for me. I've built a few machines (see link in signature), including this one, so no probs with the RAM insertion, but good tip. Thanks. :)

---


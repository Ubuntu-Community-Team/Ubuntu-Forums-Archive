---
title: "Ubuntu 8.0.1 crashes after 10 min of open arena"
date: 2008-12-11
forum: Gaming &amp; Leisure
---

### Post by JoeSchmoe1971 on 2008-12-11
I've been using versions of ubuntu since breezy badger, and just updated to the most recent 8.1.0 

I play openarena with this system. It's a desk top with 8gb of RAM, Athlon x64 dual-core processor and a Geforce 8800 video card. The appropriate drivers (non-free) have been activated. There should be no issues with memory or speed just to play open arena, in fact the system works great for a while. But after about 10 minutes of play, the screen goes blank (cursor in the upper left corner), I get three beeps over the speakers (not system speakers), then the computer shuts down (crashes, really). 

From what I gather, the three beeps are an alarm that signals low power, but the installed power supply is over 600 watts and there is no battery, this being a desk top. 

So does anyone have a theory?

---

### Post by Toffeeapple on 2008-12-12
> **JoeSchmoe1971 said:**
> From what I gather, the three beeps are an alarm that signals low power, but the installed power supply is over 600 watts and there is no battery, this being a desk top. 

So does anyone have a theory?

PSU may be on its way out, even 600w, with a lot of stuff in your pc, hard drives memory etc, if its a cheep unit it may not be able to supply enough constant power to the GPU. Could be over heating too, or just on its way out : )

Try unplugging some hard drives or cdroms if you have more than one, if you have lots of case fans unplug them and leave the side off if your concerned it might overheat, if your over clocking return to stock.

If you having unexplainable crashes best thing to to is return to a basic set up and slowly add stuff till you find out where the problem is.

If you have another PSU try that.

Remove large deposits of dust, around CPU heat sink and grills on PSU or GPU

:)

---

### Post by Onesimus on 2008-12-12
I have a similar problem.  

I did suspect that the screensaver might be trying to kick in - but I never quite got to the bottom of it.

---

### Post by regor210 on 2008-12-12
You could try turning off your screensaver and using Power Management to put display to sleep instead. see if that helps?

---

### Post by e_torano on 2008-12-12
I had this kind of problem when I had the screensaver activated. After turning it off, everything works perfectly. Could jut try that?

---

### Post by JoeSchmoe1971 on 2008-12-12
Yeah, I had the problem with the screen saver before (game quits and you get funny colors on the screen), but I disconnected that. No problems with video or pictures at all, so not the same situation. 

I noticed that it crashes most often when I'm in a gaming arena with lots of multiplayers and pretty fast ping (precisely the time you really want to play, right?). Then I get the blank screen, the three beeps, then a crash. 

The PSU is brand-damned new and was highly rated on newegg; would hate to think its the center of the problem but will try adding things gradually to see if I can find the overload point.

---

### Post by JoeSchmoe1971 on 2008-12-14
Ok, I replaced the power supply with a new 650 watt unit. Hooked everything back together and went online to test it out. The system played fine for 15 minutes or so, then game slows down, I get four beeps (from the speakers, not the mobo), the game crashes, then the computer eventually turns itself off. 

This sounds like a text book power supply problem but WTF - how much juice do I need? And though people talk about beep codes, I think this is different since the beeps are coming thru the pc speakers, not the mobo speaker. 

I'm figuring it must be some grounding issue, or something I left unhooked,but so far no luck. 

I'm all ears....](*,)

---

### Post by JoeSchmoe1971 on 2008-12-14
Doh - I think I figured it out. The BIOS for my motherboard (ABIT NF-M2) has some instability problems with Athlon 3800+ processors are installed, which is what I'm running. So I got the new BIOS, but the install for Award bios is usually done in DOS. 

I know there are ways to do this in ubuntu, but flashing a BIOS is one thing that's risky enough without extra variables. Hate to have to install XP just to run a BIOS installer - anyone have any luck flashing in Ubuntu? Thx.

---


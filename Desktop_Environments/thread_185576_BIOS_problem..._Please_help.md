---
title: "BIOS problem... Please help"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Sukarn on 2006-05-31
I had a problem with my processor being detected as AMD Athlon XP 1800+ instead of AMD Athlon XP 2400+
The nice people at [http://www.ubuntuforums.org/showthread.php?t=182289&page=2](http://www.ubuntuforums.org/showthread.php?t=182289&page=2) told me that it might be a problem with FSB settings and I changed that setting from 100 MHz to 166 MHz.
After rebooting, the Post BIOS screen showed it as Athlon XP 2400+, but the computer would not boot again after that. It was able to boot just once.
The computer boots with if I remove the BIOS battery, but it does not reboot unless I cut off the power supply for a few seconds. The screen just remains off and the CPU just makes the initial sounds of starting up, but I dont think it gets as far as booting, because the hard drive isin't accessed.

PS: I am not sure which section to make this thread in, so I made it in Desktop Support.

---

### Post by glotz on 2006-05-31
1800 / 100 = 18
18 * 166 = 2988 >> 2400 (124,5 %)

2400 / 18 = 133.333...

I hope the overclocking didn't damage your CPU. I don't know what else to make of it...

---

### Post by coolclassic on 2006-06-01
Although your processor says it's a 2400 it actually runs at 2000
the clock frequency should be set at 133.

---

### Post by Sukarn on 2006-06-01
OK, I understand now that it should be set to 133 MHz, but, like I said in my first post, I can only run the comp if the BIOS battery is removed. Hence, I cannot save my preferences in BIOS. That said, I cannot even restart my system. I have to perform a shutdown instead and then turn the power off, wait a few seconds and then restore power to make it work.

I am alright with buying a new battery for it, but do you think that it would work? I am not sure about this since after shutdown the power has to be cut off (making the BIOS settings reset themselves). This makes me wonder whether the BIOS got damaged. Any ideas? Or is it just that if the power supply is not cut off, it keeps looking for the battery and that is why it does not start?

PS: I am now STUCK with my 2400+ behaving like a 1800+.
coolclassic is right, AMD naming has it named as 2400+, but it actually is about 1998 MHz

---

### Post by go2dell on 2006-06-01
Sounds to me as though you've been manually entering some settings in your BIOS and went a bit too far somewhere.  You probably need to back off some of your settings by a step or two and you'll be fine.

It would be helpful to know which motherboard you're using, but even without that information I'd recommend setting everything in your BIOS setup to an Auto setting, provided there is one.  Several manufacturers have a "reset to optimal defaults" which is a good way to start, although the defaults are rarely optimal.  For instance, on my motherboard I have used the reset to defaults option to return to a nice baseline after playing with settings and breaking things.  Setting everything else to Auto should get you booting at manufacturer spec settings again.

After that, time to play again. :twisted:

EDIT:  For clearing the BIOS completely there is probably a jumper somewhere on the board that will let you do this, although removing the battery will work equally as well (just not as quickly).  It's an option if you still can't even get into the BIOS settings.

---

### Post by Sukarn on 2006-06-01
hmm... a jumper. I'll have to look for that.
My motherboard is nForce2 (nvidia).
I can't remember having seen any "auto" setting, though there probably is a reset to defaults setting. Anyway, with the battery removed, it should be using the defaults.

I'll just try to find the jumper, reset the BIOS, put the battery back in, turn the comp on, choose reset to defaults setting in BIOS, and then i'll try to restart the comp and see whether it restarts or not...

Thanks for the help so far guys

---

### Post by go2dell on 2006-06-01
Actually I was looking for the motherboard manufacturer, not the chipset manufacturer (nVidia doesn't make motherboards).  If you bought just the motherboard then it's something like Abit, Asus, MSI, or if you bought a whole computer, what brand is it?  If all else fails, at the first screen (as the memory is counting) there's generally a manufacturer listed.  Once we know who made the board, we can narrow down the correct choices.  Until then, it's a shot in the dark. :-k

---

### Post by Sukarn on 2006-06-02
"M7NCG 400 - VER: 1.0" is written on the motherboard. Searching google for "M7NCG 400" lead me to Biostar, so I suppose its a Biostar motherboard.
The PC is a 3 year old assembled (built with seperate parts) PC.

---

### Post by go2dell on 2006-06-03
BINGO!

I found a BIOS Setup Guide for your motherboard at:
[ftp://ftp.biostar-usa.com/manuals/M7NCG%20400/M7NCG400bios.pdf]("ftp://ftp.biostar-usa.com/manuals/M7NCG%20400/M7NCG400bios.pdf").  You'll probably want to look at that to guide you.

Here's what I would recommend to get a stable system.  Once you have some good baseline settings, you'll at least know what works.  If you break it after that, you'll know why it broke. ;) 

Before you start, be certain you **write down every change you make** so when things don't work you'll know what to avoid next time.

[LIST=1]Go into the BIOS and on the top right (on the very first screen), select the "Load Optimized Defaults" setting.  I have yet to see one where these are actually optimized, but the settings they pick are almost guaranteed to let your system boot.
[/LIST]
[LIST=2]Reboot once to see if the system boots.  I'm guessing it will be slower than normal, but you never know.[/LIST]
[LIST=3]Now go back into the BIOS and look in the "Advanced Chipset Features" screen.  Verify that "System Performance" and "CPU Interface" are both set to *Optimal*.[/LIST]
[LIST=4]On that same screen, verify that the "FSB Frequency" is set to the correct setting.  If memory serves, it's 133 for your processor.[/LIST]
[LIST=5]Leave "Memory Frequency Settings" at "SPD".[/LIST]

Those settings should be enough to make the board recognize the processor correctly, and it should be running within spec.  You can just press F10 to save and then try rebooting.

Later you'll probably want to go back into the BIOS and disable things like memory shadowing, as well as check that the AGP settings are correct for your video card.  In fact, go through each screen slowly and double-check it all.  Tedious, but worth it.

While you're at it, buy a battery to replace yours. :-D
Hope that helps.  Good luck!

---

### Post by Sukarn on 2006-06-05
Rebooting doesn't work no matter what I do...
Loading optimized defaults is useless, as I have to reboot after visiting the BIOS, and rebooting doesn't work as I wrote above.
[quote=Sukarn]after shutdown the power has to be cut off (making the BIOS settings reset itself). This makes me wonder whether the BIOS got damaged. Any ideas? Or is it just that if the power supply is not cut off, it keeps looking for the battery and that is why it does not start?[/quote]
If I dont cut the power off before starting it up again, or if I just try to reboot/restart the comp., it just makes the normal boot-up sounds (CD-ROM check, fan sounds) but the screen remains blank and I know its not loading any OS because the hard drive remains unaccessed (the red light that indicated that the HDD is being accessed does not light up).
However, a shutdown, power cut-off (switching the plug off) for 5-10 seconds, then starting it up works just like normal (loading the defaults for BIOS). So, I am stuck with the BIOS being such that I cannot change its settings. If I do, I have to restart which I can't...
Any ideas?

I'll get myself a new battery anyway.

**EDIT :** I am thankful that Ubuntu syncronizes the time and date during the boot process. Unlike Windows, it is able to syncronize the date/time even if the date is incorrent (in my case, '1 Jan, 2002' at every bootup). Windows gives an error if the date is set incorrectly.

---

### Post by go2dell on 2006-06-05
I do have another thought, but you won't like it. :) 

Based on the age of your system, you could have some failing capacitors in either the power supply or motherboard.  Happened to me, and I was using a "reliable" Big-Name-Brand power supply.

You might want to take a look at [http://en.wikipedia.org/wiki/Capacitor_plague]("http://en.wikipedia.org/wiki/Capacitor_plague") and [http://www.badcaps.net/]("http://www.badcaps.net/") to find pictures and explanations of how to figure out if you have bad capacitors.

Other than that, you're getting into an area where you may have to test every single component for problems.  Sometimes faults exist but work fine for a year or two, and only show up as the equipment starts to age.

Good luck!

---

### Post by Sukarn on 2006-06-06
The problem wasn't the battery, thats for sure. A new battery didn't make any change in the situation.

My vendor is taking the comp tommorow for a new heatsink and to check whether he can identify whats the problem with my motherboard.

If all else fails, I'll be reading through the whole of these articles, trying to see whether I can find something to make it work like "normal".

Thanks for all the help so far **go2dell**.

**EDIT : ** _Venting from the top of the capacitor, visible as brown deposits, or a visible hole in the vent_ from page [http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague) under section Identifying "capacitor plague" is evident on my board
Brownish deposits can be seen on some of the capicitors just like in the image [img]http://upload.wikimedia.org/wikipedia/en/thumb/9/96/Badcaps-tayeh-4.jpg/180px-Badcaps-tayeh-4.jpg[/img]

EDIT 2 : _Spontaneously rebooting_ - This had also been happening very frequently before I shifted to Linux. I had been blaming overheating for it. Thats the reason that I'm getting a new heatsink.


Now I'm in big trouble. Theres no way I can afford getting a new motherboard.


MORE EDITS:
1)Resetting the system after a freeze and the system will not repost.
      (You have to completely power down then power back up.)
2)BSODs were common to me while I used Windows and fired up some application that required heavy HDD access and accesing sound at the same time. I shifted (but still have Win XP installed) to Ubuntu about 2 weeks ago.

---

### Post by coolclassic on 2006-06-06
I checked out the manual for this motherboard and you have two jumpers that can effect your settings one is the cmos check and see that it is not at the clear cmos setting and the other jumper sets your clock speed at 100mhz as safe mode you need to set this to default see here for jumper settings.

[ftp://ftp.biostar-usa.com/manuals/M7NCG](ftp://ftp.biostar-usa.com/manuals/M7NCG) 400/M7NCG400manual.pdf

page 12 for frequency
page 9 for cmos

---

### Post by Sukarn on 2006-07-23
OK, I sent the motherboard to the company and they fixed whatever was wrong. I was in the warrenty period so I didn't have to pay for it.

---

### Post by go2dell on 2006-07-27
Ah, the under warranty fix.  Gotta love it!  Now if they'd just stop putting faulty caps on everything...

---


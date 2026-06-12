---
title: "I Sunk My Computer/Grub"
date: 2009-05-20
forum: General Help
---

### Post by lakelovers on 2009-05-20
I think I may have activated malicious key strokes as a way to restart a stalled PC, or coincidentally, my drive failed (or both). I happened on to a Linux or Ubuntu site that suggested this action when you computer stalls. Here's what it said:
"The Linux kernel includes a secret method of restarting your PC when it hangs.
1. Hold down the Alt and SysRg keys
2. While holding hose down type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB."

Your computer will restart.

My better judgment wasn't working.

How can I get my computer back? It could be a failed drive because the drive spits out a "click" noise.

---

### Post by VMC on 2009-05-20
> **lakelovers said:**
> I think I may have activated malicious key strokes ...
1. Hold down the Alt and SysRg keys
2. While holding hose down type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB."

...

My better judgment wasn't working.

How can I get my computer back? It could be a failed drive because the drive spits out a "click" noise.Those key-strokes are NOT malicious. It's been documented before. He one [example]("http://kember.net/articles/231/reisub-the-gentle-linux-restart").

Try the Recovery Mode and see if you can find any errors. Also Alt+F2 and use the terminal to find errant process.

---

### Post by mcduck on 2009-05-20
Just like VMC said, nothing bad in those commands. They simply do the same kind of soft reboot you'd get by selecting reboot from the menus, closing all programs, syncing the drives etc. unlike what would happen if you just pressed the power/reset button.

Really useful commands if your computer freezes and you want to boot it cleanly instead of doing a hard reset.

Unless you pressed the keys really quickly, without any pauses between them, there should be no way how doing that could cause any damage. (pressing them too quicly without allowing each command to finish could result in booting the machine before it has finished syncing the drives. Which would be pretty much the same thing that happens if you just press the power button to force the computer to boot.

Clicking hard drive sounds like either the drive isn't properly connected, or it's broken.

---

### Post by lakelovers on 2009-05-20
Whew. . . that's a relief. I got my computer working. The problem was that the hard drive was not designated at the 1st boot device in the Bio. What puzzles me is that I have not accessed the system set up in ages. Somehow it got changed without me touching it, and no body else uses this computer or has access to it. What do you supposed caused the change? Is it possible that somebody got access through the internet and changed it and if that's possible, why?

---

### Post by jbruced on 2009-05-20
> **lakelovers said:**
> Whew. . . that's a relief. I got my computer working. The problem was that the hard drive was not designated at the 1st boot device in the Bio. What puzzles me is that I have not accessed the system set up in ages. Somehow it got changed without me touching it, and no body else uses this computer or has access to it. What do you supposed caused the change? Is it possible that somebody got access through the internet and changed it and if that's possible, why?

More likely a weak battery and power surge scrambled it.

---

### Post by mcduck on 2009-05-21
> **jbruced said:**
> More likely a weak battery and power surge scrambled it.

I agree. Based on my knowledge it shouldn't even be possible to access BIOS settings through network. While weak CMOS battery and any cut in power will definitely reset BIOS settings.

---

### Post by lakelovers on 2009-05-25
Thanks for your replies. Is there a way to test the battery or should I just replace it?

---

### Post by raymondh on 2009-05-25
> **lakelovers said:**
> Thanks for your replies. Is there a way to test the battery or should I just replace it?

Open BIOS and check the clock and date ... way out of date can mean that BIOS has reset probably due to a weakening battery.

regards,

---


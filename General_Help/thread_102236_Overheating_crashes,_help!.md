---
title: "Overheating crashes, help!"
date: 2005-12-11
forum: General Help
---

### Post by The Warlock on 2005-12-11
My laptop tends to overheat from time to time.

Under Windows XP, when my laptop starts to get hot, the operating system scales down my processor speed, so everything goes slower but nothing gets damaged, the computer doesn't crash, and I don't lose my work.

Under Ubuntu Linux, when my laptop starts to get really hot, the computer shuts down and I lose all my work.

How do I make Linux deal with overheating intelligently instead of just crashing?

---

### Post by taurus on 2005-12-11
What kind of laptop do you have:  brand name, model, processor, etc.?  There is a way to scale down your processor when it's not in use and "spins" up when the OS needs it...

---

### Post by mherring on 2005-12-11
[QUOTE=taurus]What kind of laptop do you have:  brand name, model, processor, etc.? ...[/QUOTE]

I would use this info to make sure I didn't get one like it.  I've never seen a laptop overheat enough to crash.
What does the manufacturer say?

---

### Post by The Warlock on 2005-12-11
[QUOTE=mherring]I would use this info to make sure I didn't get one like it.  I've never seen a laptop overheat enough to crash.
What does the manufacturer say?[/QUOTE]

The manufacturer says he doesn't give a shit about Linux users (in nicer words, of course). 

It's a Uniwill 256KA0. It's got an Athlon 64 Mobile 3200+.


The processor does scale down and spin up when I need it. The problem is, if I keep using the processor at full speed for long periods of time (such as compiling a kernel or generating a GPG key or playing UT2004 or whatever), the computer overheats and crashes. It doesn't do this in Windows: Windows scales down the processor when it starts to get hot, even when I'm using it 100%, so it doesn't get to dangerous heat levels and shut down. How do I do this under Linux?

---

### Post by Noelinho on 2005-12-11
[QUOTE=mherring]I would use this info to make sure I didn't get one like it.  I've never seen a laptop overheat enough to crash.
What does the manufacturer say?[/QUOTE]

Some of the Toshiba P4's overheat after 30 - 60s minutes on :???:

---

### Post by taurus on 2005-12-11
Never heard of that company before but I don't believe the generic kernel has powernow compiled in it!  I think you need to rebuild your kernel to include powernow so it can handle the scaling for your AMD64...

---

### Post by The Warlock on 2005-12-11
[QUOTE=taurus]Never heard of that company before but I don't believe the generic kernel has powernow compiled in it!  I think you need to rebuild your kernel to include powernow so it can handle the scaling for your AMD64...[/QUOTE]
It has powernow! It has scaling. It scales the processor; it's running at 800MHz right now. The problem is, if I crank it up to the full 2.0 GHz for some reason (say, generating a 4096-bit DSA key), and it stays there, the computer overheats and crashes. Under Windows, if I'm running the processor full speed and it's in danger of overheating, it scales back down automatically, even though I'm running at full speed. How do I make Linux do this?

And the company is one that makes barebones laptops for other manufacturers to buy, add processor, RAM, etc. and sell. I believe iBuyPower and eMachines both buy the exact same model for one of their laptop lines.

---

### Post by Ocxic on 2005-12-11
if the laptop over heats enough to crash, I would bring it back to the store for a refund. it's obviously a poorly designed laptop. NO computer should crash due to overheating, espesially if it's designed properly. If my laptop EVER did that for any reson, that was not my fault I would return it immediatly, it not worth the money.

or right click on your panel, click add to panel, and add the CPU scaling monitor, that should let you control you CPU speed

---

### Post by The Warlock on 2005-12-11
[QUOTE=Ocxic]if the laptop over heats enough to crash, I would bring it back to the store for a refund. it's obviously a poorly designed laptop. NO computer should crash due to overheating, espesially if it's designed properly. If my laptop EVER did that for any reson, that was not my fault I would return it immediatly, it not worth the money.

or right click on your panel, click add to panel, and add the CPU scaling monitor, that should let you control you CPU speed[/QUOTE]
The scaling monitor only monitors scaling (I have it up right now). You can't control scaling from there, and besides, I shouldn't have to. It should do it automatically when it's in danger of overheating.

The laptop only heats enough to crash under Linux. Besides, the warranty expired months ago.

**This works under Windows. How can I make it work under Linux?**

---

### Post by 23meg on 2005-12-11
[QUOTE=The Warlock]The scaling monitor only monitors scaling (I have it up right now). You can't control scaling from there, and besides, I shouldn't have to. It should do it automatically when it's in danger of overheating.[/QUOTE]
Do this```
sudo chmod +s /usr/bin/cpufreq-selector
```and now you can control scaling from the applet while powernowd isn't working.

---

### Post by Teedyo on 2005-12-12
Can't you use lmsensors to monitor temperature and user breakpoints + scripts to control fan speed and cpu freq.?  Googling for powernow lmsensors overheat seems to turn up a few solutions.

I also think that there is a way for linux to default to ACPI for scaling.  No quick answer for you tho'.

---

### Post by The Warlock on 2005-12-12
[QUOTE=23meg]Do this```
sudo chmod +s /usr/bin/cpufreq-selector
```and now you can control scaling from the applet while powernowd isn't working.[/QUOTE]

Thank you! Doing that and setting the governor to "conservative" solved my problems.

---

### Post by mherring on 2005-12-12
[QUOTE=The Warlock] Besides, the warranty expired months ago.
[/QUOTE]

This is straying a bit but remember that warranties are written to protect the seller--not the buyer.
A vendor has the responsibility to ensure that their products perform the intended function.  I would at least lean on them a bit.

Perhaps more the point:  I cannot think of why the machine would crash sooner under one OS vs another--it seems to me that heat-realted malfunctions are more hardware related.

---

### Post by The Warlock on 2005-12-12
[QUOTE=mherring]This is straying a bit but remember that warranties are written to protect the seller--not the buyer.
A vendor has the responsibility to ensure that their products perform the intended function.  I would at least lean on them a bit.

Perhaps more the point:  I cannot think of why the machine would crash sooner under one OS vs another--it seems to me that heat-realted malfunctions are more hardware related.[/QUOTE]

Sure, the malfunctions are hardware-related, but Windows controls them. (Linux does, too, I just had to do some configuring, it seems). If I tried to lean on them they'd tell me "we only support Windows" and there'd be pretty much nothing I could do. 

And from what I've heard, it's more of a design flaw in this model than a single hardware malfunction. Ah, well, live and get screwed, I guess.

---

### Post by Robgould on 2006-05-11
I have a Toshiba P4....It has never creahsed from heat running winxp.  With Ubuntu...even with my CPU scaling correctly, I would have to elevate the laptop just for it to run for over 10 minutes.  I am not sure why

---


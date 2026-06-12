---
title: "Startup Problem, i.e. It Won't"
date: 2009-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jjtstan on 2009-08-23
I have a Dell Inspiron 530 that came factory installed with Gutsy Gibbon.  Upgraded to Hardy Heron at home.

For the past few months, the computer would suddenly lockup while using Firefox, usually if I had too many tabs open.  I would have to turn it off manually, turn it back on manually, and then everything would be fine.

It locked up just now, and now it won't turn back on again.  Or rather, when I try to turn it back on, it starts up, then turns off after 2-3 seconds.  Pauses a few seconds, then starts up again.  But when it starts up, the fan remains on high-whirr.  I don't know the technical term for this - when the computer starts up, usually the fan (or some other part of the machine) makes a louder/heavier whirring noise that dies down after a few seconds.  Now, the loud noise persists.  But no signal is ever transmitted to the monitor.

Eventually I turn the machine back off, manually.

Any suggestions?

---

### Post by ugm6hr on 2009-08-23
Maybe over heating?

Clear all the vents with a vacuum, and consider opening the case to remove all the dust.

---

### Post by Diskotekno on 2009-08-23
I would try a new power supply, I have witnessed many a strange happening on computers with faulty power supplies....

---

### Post by RabbitWho on 2009-08-23
To see if it's over heating next time you're on that computer and connected to the Internet you can follow the instructions on this website: 

[http://blog.taragana.com/index.php/archive/lm_sensors-guide-or-how-to-monitor-cpu-temperature-in-linux-fedora-core-6-26-kernel/](http://blog.taragana.com/index.php/archive/lm_sensors-guide-or-how-to-monitor-cpu-temperature-in-linux-fedora-core-6-26-kernel/)

then you just type in sensors in the command line and it'll tell you your core temperature. (I found it today..  it's very funky!)

---

### Post by jjtstan on 2009-08-23
Thanks for the advice.  So far we've switched power strips, with no effect.  [the power supply is the computer plugged into a power strip].  I'm going to take the machine apart and clean its interior when I get home from work tonight.  

Thanks for the sensor link.  Right now, though, I can't get the machine to start up or send a signal to the monitor, so that'll have to wait till later.

Any other advice would be greatly appreciated.

---

### Post by jjtstan on 2009-08-24
So I opened up the case, and found a small dustball.  The air intakes themselves were relatively clean.  I vacuumed everything, put the computer on a new power strip, and basically nothing's changed.  Instead of turning off and turning back on again, it turns on, and then stays in high-whirr or loud-sound mode, while sending no signal to the monitor.  

What now?

P.S. I'd be thanking folks for their advice, but I'm not seeing any active thanks buttons.  So advice on how to do that would be appreciated as well.

---

### Post by jjtstan on 2009-08-24
Ok, a friend of mine suggests that we get someone to come and test the hard-drive to see if it's still functioning.  And then if the hard-drive is functioning, decide whether to replace the motherboard or whether to replace the system entirely.

Any suggestions?

---

### Post by cascade9 on 2009-08-25
I doubt its your hdd, if it was a hdd problem you would have got a 'boot device not found' message, or something similar. I think it could be overheating, and that overheating has a good chance of being the old 'thermal grease has dried out and stopped conducting heat' issue. 

Ohh, and when Diskotekno said 'change the power supply' he did not mean the power strip, he meant the little box inside your case that converst mains 110/120/220/230 volt AC (depending on where you are) into 3.3, 5 and 12volts DC.

---

### Post by jjtstan on 2009-08-25
> I doubt its your hdd, if it was a hdd problem you would have got a 'boot device not found' message, or something similar. 

This makes sense.  I'm not getting any signal to the monitor.  No BIOS, no nothing.  I guess my friend's thought was that maybe both the motherboard & HDD were fried, so that replacing the motherboard alone might not be worth it.
 
> I think it could be overheating, and that overheating has a good chance of being the old 'thermal grease has dried out and stopped conducting heat' issue.


If this is the problem, we need to add thermal grease to the CPU? Is that correct?  Or are there some other locations that need thermal grease as well (e.g. my brain).

> Ohh, and when Diskotekno said 'change the power supply' he did not mean the power strip, he meant the little box inside your case that converst mains 110/120/220/230 volt AC (depending on where you are) into 3.3, 5 and 12volts DC.

This makes a lot more sense than changing the power strip.:P  

I'll look into these options and report back.

---

### Post by cascade9 on 2009-08-25
> **jjtstan said:**
> If this is the problem, we need to add thermal grease to the CPU? Is that correct?  Or are there some other locations that need thermal grease as well (e.g. my brain).

Yep, if it is dried out thermal grease, you need to pull of the heatsink, clean off the crud and apply some fresh grease. Methylated spirits and a bit of clean rag works pretty well for the cleaning, dont use anything abrasive. You only need a tiny bit of grease, dont coat the whole CPU in the stuff. Depending on what your using, about the size of a grain of rice, maybe a 1.5 grains, is perfect. 

Just out of intrest, thermal grease isnt that great at conducting heat. Even toothpaste beats Artic Silver3-

[http://www.dansdata.com/goop.htm](http://www.dansdata.com/goop.htm)

What thermal grease is good at is staying 'wet' for a long time. The toothpaste might be better, short term, but it will dry out in no time at all. Then it changes from being something to help get maxium contact between the heatsink and the CPU into a little blanket to keep your CPU warm. This is not good.  

Good luck ;)

Edit- dont forget to put the heatsink back on. I could have, see, I just totally forgot to say that, its only one small step from saying to doing (or not doing as the case me be) Not putting a heatsink back on would be bad.

---

### Post by jjtstan on 2009-08-25
Thanks.  I'd offer electronic thanks too, but can't figure that out.

The repair guy showed up and did something to the motherboard - wife is unclear exactly what.  Machine's working just fine now.

---

### Post by cascade9 on 2009-08-25
I would have liked to know what he did. Guess I'll have to work on the time machine if I want to find out. :D 

Good to hear its working again ;)

---

### Post by jjtstan on 2009-08-25
Just got in touch with him.  He says it was a CMOS problem, and he he "discharged" (?) the motherboard.  Basically that the motherboard had built up a static charge and he released the charge.  Or that he pulled the batteries out of the motherboard and put them back in.  Something like that - releasing an electric charge.  Apologies for the wacky description, but I'm trying to translate from Chinese into English, and I don't even know how to talk about these things in English.

---

### Post by cascade9 on 2009-08-26
CMOS problems :| He could have fixed it by removing the battery, or normally theres a 'clear CMOS' jumper. 

Thanks for letting me know ;)

---


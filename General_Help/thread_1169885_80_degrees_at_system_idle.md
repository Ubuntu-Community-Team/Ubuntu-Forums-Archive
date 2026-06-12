---
title: "80 degrees at system idle??"
date: 2009-05-25
forum: General Help
---

### Post by shleena on 2009-05-25
just gone back to ubuntu gnome from kubuntu kde because of heat problems, restored user session defaults such as themes, fonts etc, hoping that that would sort out the problem, idle the system runs above 76 celsius and any apps send it up to 82-83, but curiously no higher than that. fan works fine, cpu is at 10% and ram is at 250mb. any help or suggestions would be great. running acer 1640z pentium m processor 1.7 ghz (intel centrino) and 1 gig ram. ive googled for half the day but no luck so far. if anyone wants me to put some stuff in the terminal if it helps then go ahead. thanks for your feedback

---

### Post by stefangr1 on 2009-05-25
I assume you are using a notebook? How have you measured the temperatures you're reporting? Are you sure your system wasn't also very hot in windows?

---

### Post by clhsharky on 2009-05-25
Have you checked the temp in BIOS?

---

### Post by shleena on 2009-05-25
> **stefangr1 said:**
> I assume you are using a notebook? How have you measured the temperatures you're reporting? Are you sure your system wasn't also very hot in windows?

yup, notebook, about 2 or 3 years old i think. temps have been got from acpi -t, and there was also a widget in kde reporting the same thing, and the laptop is so hot that i cant rest it on my lap without feeling like im running a marathon...

well i havent used windows for a while, but i dont remember it being anywhere near as hot even when running games. to be honest, i cant find where to view my temperature in the bios, im assuming there isnt a way because its pretty basic, just info about the netbook and where to boot from, etc. not detailed.

the only curious thing is that i think my battery is a bit knackered, it shows 0% on full charge, and i cant boot off it. but surely that wouldnt change anything?

---

### Post by clhsharky on 2009-05-25
BTW which version of Ubuntu, and what video card + drivers are you using?

---

### Post by paradigm2 on 2009-05-25
The problem likely isn't either Gnome or KDE, rather more hardware related.  Acers are HORRIBLE for this.  I have an Acer laptop which was almost destroyed (The LCD was likely fried in part due to heat) on the native XP because the fan always seemed to kick on too late or at too low of a speed.  My system routinely would get to 79 degrees Celsius -- often shutting down or freezing in the native XP.  The only thing I could do was mount an external fan which blows on it (It usually sits on a desk) and raise it so t is two inches off the table for ventilation.  I suppose a more elegant solution is a good cooling pad or perhaps other upgrades.

Unfortunately the board on mine could not be set to always keep the internal fan on either.  Either with the windows speedfan or the native linux utilities (might be different for yours).   suppose if one is willing to do a little hardware hacking, you could probably rig it so the fan always stays on high.  That might help.

Acer really needs to get their heads out of their posterior over heat and LCD issues...

---

### Post by clhsharky on 2009-05-25
The reason I asked is because Proprietary drivers do a little better job of controlling a lappy. In Jaunty ATI legacy cards only have open course stack and aren't as good controlling power. And Intel is not doing good right now in Jaunty. 8.10 might help some in those cases, and if you have Nvidia I don't know what to say.

---

### Post by kerry_s on 2009-05-25
> **shleena said:**
> just gone back to ubuntu gnome from kubuntu kde because of heat problems, restored user session defaults such as themes, fonts etc, hoping that that would sort out the problem, idle the system runs above 76 celsius and any apps send it up to 82-83, but curiously no higher than that. fan works fine, cpu is at 10% and ram is at 250mb. any help or suggestions would be great. running acer 1640z pentium m processor 1.7 ghz (intel centrino) and 1 gig ram. ive googled for half the day but no luck so far. if anyone wants me to put some stuff in the terminal if it helps then go ahead. thanks for your feedback

those temp monitors have to be adjusted to match what the bios is reading, if you got a section in your bios that shows the temp than jot down the idle temps. in the sensors applet adjust "sensor value mutilpier" till it matches your bios temp at idle. other wise the temp reading is just wrong.

have you tried cleaning the fans?

---

### Post by shleena on 2009-05-27
well, thanks people, i agree i think it is more or less hardware related... but from what ive seen in forums regarding the issue, even a cooling pad doesnt make that much of a difference. the drivers ive fiddled about with and changed and put back but it doesnt make much of a difference. the only option i can think of is to downgrade to something like 8.04 and see what that does, or buy a new laptop.

...which is a distinct possibility since this one is a fair age now and is starting to fall apart at the seams. just a quick question slightly off topic, which would you say is the best make or model of laptop in general for smooth running of ubuntu systems? im talking in terms of running it fresh out of the box with little to fiddle about with, and no headaches like drivers or temperature

---


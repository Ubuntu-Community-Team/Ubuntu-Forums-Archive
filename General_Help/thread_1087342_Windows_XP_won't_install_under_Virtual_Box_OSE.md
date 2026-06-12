---
title: "Windows XP won't install under Virtual Box OSE"
date: 2009-03-04
forum: General Help
---

### Post by unplugged23 on 2009-03-04
Hey there,

I easily installed some slackware linux in virtual box, to prevent having to deal with booting up and shutting down all the time to switch back and forth between The two os's however when i tried installing XP, XP (not virtual box) gave me an error that looked like this:[IMG]http://img211.imageshack.us/img211/8433/screenshotxpsp2runningv.png[/IMG]

Does anyone know a good fix for this? :D

---

### Post by Therion on 2009-03-04
It may sound stupid but blow out the CD/DVD drive with some canned air, physically clean the WinXP install CD with something like Windex and an old cotton t-shirt and try using it again.  This really is a common solution to this particular problem.

---

### Post by unplugged23 on 2009-03-04
Alright, I don't have canned air; but will a hair dryer work on a cool setting? Thanks for the tip!

EDIT: After I did all that i realised i was using an .iso
Any other suggestions?

---

### Post by linuxuser21 on 2009-03-04
Did you change the IDE Controller?  It should be PIIX4.  I had some what of the same problem.

---

### Post by unplugged23 on 2009-03-04
> **linuxuser21 said:**
> Did you change the IDE Controller?  It should be PIIX4.  I had some what of the same problem.

I have no idea what that is, Let me go through the set up process again, to see if I can't figure it out.

---

### Post by lykwydchykyn on 2009-03-04
I'd be concerned the hair dryer would generate static electricity, but that may be excessive paranoia.  Probably it's not going to generate a concentrated blast of air sufficient to knock dust loose.  Might be just as well to stick a straw in there and blow through it.

---

### Post by linuxuser21 on 2009-03-04
It's under settings, then click on the "advanced tab" & you should see the "IDE Controller Type" menu.  Just make sure it's on PIIX4 and not PIIX3.

---

### Post by unplugged23 on 2009-03-04
> **lykwydchykyn said:**
> I'd be concerned the hair dryer would generate static electricity, but that may be excessive paranoia.  Probably it's not going to generate a concentrated blast of air sufficient to knock dust loose.  Might be just as well to stick a straw in there and blow through it.

Like I said, I'm not using the Cd drive, I'm using an iso of the xp cd that i ripped from the cd, I heard this makes it go faster? :D Thanks though

---

### Post by unplugged23 on 2009-03-04
> **linuxuser21 said:**
> It's under settings, then click on the "advanced tab" & you should see the "IDE Controller Type" menu.  Just make sure it's on PIIX4 and not PIIX3.

It is.

---

### Post by Therion on 2009-03-04
> **unplugged23 said:**
> 

EDIT: After I did all that i realised i was using an .iso ...
"Reburn" the .iso then.  This is a data-corruption  or read-error most likely; so try recreating the .iso you're using.  This IS a legitimate install CD you're working with, right?  Because if it's not, all bets are off.




/Just sayin' is all...

---

### Post by unplugged23 on 2009-03-04
> **Therion said:**
> "Reburn" the .iso then.  This is a data-corruption  or read-error most likely; so try recreating the .iso you're using.  This IS a legitimate install CD you're working with, right?  Because if it's not, all bets are off.




/Just sayin' is all...

As far I know, the copy IS legitimate. The disc came in a laptop given to be by a friend with a broken windows installation. The laptop, however did not support booting form cd's. Any ways,the copy is not on the original disc, it was copied, so the my friend could keep the original. So never mind, I guess it isn't legit after all. The disc is pretty scratched up though.

EDIT: why would an illegitimate copy not work?
EDIT 2: We'll have to continue this discussion tomorrow; just didn't want to leave you hanging

---

### Post by cariboo on 2009-03-04
The forums don't support software piracy, what you do is your own business, just don't bring it up here.

Jim

---

### Post by Therion on 2009-03-05
I didn't mean to bring up piracy issues, actually.  My point was simply that I've spent countless hours working with people trying to get Windows installs working only to find they're using pirated software of one kind or another.  This frequently is a recipe for frustration.

Ethical issues and forum policy aside, it's just that an illegitimate install CD introduces a huge, gaping "X Factor" into the whole equation.  You have no idea, really, what you're working with in that instance.  That, combined with Microsoft's ACU error messages (**A**rchaic, **C**ryptic, **U**nintelligible) make troubleshooting the problem a fool's errand.

---

### Post by unplugged23 on 2009-03-05
> **cariboo907 said:**
> The forums don't support software piracy, what you do is your own business, just don't bring it up here.

Jim

> **Therion said:**
> I didn't mean to bring up piracy issues, actually.  My point was simply that I've spent countless hours working with people trying to get Windows installs working only to find they're using pirated software of one kind or another.  This frequently is a recipe for frustration.

Ethical issues and forum policy aside, it's just that an illegitimate install CD introduces a huge, gaping "X Factor" into the whole equation.  You have no idea, really, what you're working with in that instance.  That, combined with Microsoft's ACU error messages (**A**rchaic, **C**ryptic, **U**nintelligible) make troubleshooting the problem a fool's errand.

Ok, I guess I can live with that, but what's odd is that I watched the disc copied from a LEGIT windows CD How this could screw up the process I don't know. But I guess I'm off to go get a clean CD. Thanks for all your help!

---


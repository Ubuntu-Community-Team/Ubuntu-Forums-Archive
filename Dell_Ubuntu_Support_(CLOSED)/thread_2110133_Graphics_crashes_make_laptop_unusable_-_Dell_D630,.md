---
title: "Graphics crashes make laptop unusable - Dell D630, v. 12.10"
date: 2013-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ffyncimynci on 2013-01-29
Recently, I had to reinstall ubuntu when I woke up one morning and found that the OS kept booting to grub. At the time I also had a windows partition and that worked fine while ubuntu didn't. I am wondering if this was due to the same problem.

There were always a few graphics problems (i.e the thing that runs programs from the loader wouldnt display, and the computer would struggle when I tried to alt+tab between programs) but it was working ok until today.

Now, a week after reformatting and reinstalling, it's crashed to the extent that the OS won't *visibly* do anything at all when I turn it on. Or, intermittently, it will work and then crash after a little while.

Is this a hardware or a software problem?

Is there anything I can do other than reinstalling ubuntu?

Thank you all in advance...

P.S I should note I'm not very experienced in terminal but I'd be more than willing willing to give more technical fixes a try if I can get step-by-step instructions.

---

### Post by Bashing-om on 2013-01-29
ffyncimynci; Hi ! Welcome to the forum.

What desk top (unity?) in ubuntu are you running ?
When you (re)installed did you check in the installation to install the 3rd party software (ie drivers) ?
ubuntu Software Center: top tool bar-> Software sources; are all boxes checked under the  "Ubuntu Software" tab,  Uner the "Other Software" tab is  "Independent" checked" ?

Have you attempted to install another Graphics driver in the "Additional Drivers" utility ?

Have you updated/upgraded the (re)install ?
[INDENT][INDENT][INDENT]Just try'n to help 
[/INDENT][/INDENT][/INDENT]

---

### Post by ffyncimynci on 2013-01-29
Hey, thanks a lot for your response!

I just tried to find out the answers to your questions above but the graphics quickly started breaking and the computer crashed before I got the chance to open software centre...

However, when I rebooted the graphics were also a bit pixellated on the Dell BIOS screen and the OS launcher. Am I correct in thinking this means it's a hardware problem?

In case not the other answers are: I have not attempted to install another driver. I have, however, updated the OS.

---

### Post by Bashing-om on 2013-01-29
ffyncimynci; 

I am more inclined to think that an appropriate driver for the graphics card needs to be installed.
What results when kernel mode setting for graphics is disabled; thus:
Boot up the ubuntu installation, soon as the bios screen clears, depress shift -> grub menu.
choose a "recovery" kernel to boot -> "resume normal boot" -> GUI login:
Good so far ? Then :
login as usual:
Ubuntu Software Center ->Software Sources (task bar menu) -> Additional Drivers tab:
Install the recommended driver.
Reboot.

[INDENT][INDENT]please advise status
[/INDENT][/INDENT]

---

### Post by ffyncimynci on 2013-01-29
Began to try that, and noticed the graphics on the BIOS screen deteriorating even more. Was forced to restart. For a while, couldnt even get the BIOS screen to display - just a backlit black screen when turned computer on.

Managed eventually to get into recovery mode and changed the graphics driver to the proprietary one at the top of the list. Restarted and it still isn't working. There is another driver by the same company in the list, so will try that ASAP. Going away for two days for business so won't be able to try til Friday now.

Many thanks for your help so far. Am hoping you'll stick around to help see it through.

---

### Post by Bashing-om on 2013-01-29
ffyncimynci;
I'll Be around.

Your last > "graphics on the BIOS screen deteriorating" does strongly indicate problems other than software. (no operating system is leaded at this point)

1st thing now is to open that box up and give it a good cleaning. If you have not done this procedure before, I'll give you some general hints.

A desk top box is much easier to get into, but in any event open it up, pay attention to the wiring and find all the cooling fans. OK, couple of cans of expensive canned air to blow the dust all out of the case; pay close attention to hold the cooling fan blades from spinning under the influence of the air blast - use a ink pen to hold the blades stable - if those fans spin up can ruin them ! Try not to blow into your cd/dvd drives, the lenses are delicate.

Paying attention to the wiring right ? Now make sure all wiring connection are tight.
Sata drives ? Make sure there are no sharp bends in the cables.

Next apply a bit of pressure on each chip on the mother board and slightly wiggle your finger in an attempt to reseat them, in particular the ram chips. Would be a good idea to hold a ground wire in your other hand, lacking a ground source keep one hand on the metal case - do not want an electrical charge to blow any components !

How old is this box ? When was the last time the CMOS battery was changed ? Now might be a real good time to change the battery.

Exercising care and caution, aint no big deal.

If this is a desk top machine leave the covers off and hook the box back up to the monitor and power supply. Boot up the machine to the bios set up and let it idle there. Observe that all the cooling fans are operational.

Are the graphics on-screen stable at this time ?

edit: laptop; maybe easy - likely not to open up the case, might be prudent to google around for info. As it is a lap top, overheating could be a sure cause.
 [INDENT][INDENT]just try'n to help



[/INDENT][/INDENT]

---

### Post by ffyncimynci on 2013-02-02
I could buy canned air and do that but before I do - BIOS and everything else no longer display at all when I turn the laptop on. Nothing visibly happens, but the busy light flickers and eventually wireless card switches on. I just get a blank screen whenever I turn it on now. Any idea what this might be?

I bought the laptop as used a couple months ago and I think it was a couple of years old. I think the fan is working fine, and don't feel the laptop overheating (have had that problem before).

What should I do?

---

### Post by Bashing-om on 2013-02-02
ffyncimynci;

What pops into my mind is the power supply has failed . As no access to bios to read what bios reports for voltage levels, one must need use a volt meter and find out the various voltage levels at the different points connecting the hardware. With time and effort you can locate the manual for your mother board and trouble shooting sections giving the respective voltage expectations.

Another probability is that the graphics card has failed. Purchase a "cheap" card and swap it out . Any graphics at all, then purchase a better card.

Laptop: I have seen broken wires from the power supply leading to the computer connection. Also in this respect check and insure that the pinning connections are tight.

These three cover 80% of the hardware problems.
[INDENT][INDENT]learning -> knowledge is a good investment
[/INDENT][/INDENT]

---


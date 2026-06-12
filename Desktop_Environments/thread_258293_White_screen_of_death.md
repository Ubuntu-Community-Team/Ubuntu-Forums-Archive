---
title: "White screen of death ???"
date: 2006-09-15
forum: Desktop Environments
---

### Post by jfl on 2006-09-15
Got a minor problem, but it annoys me because it makes Ubuntu look as(more ?) unstable than Windoze.

Box is Intel celeron 1.8 MHz  -  256 Meg RAM - no exotic hardware
OS is Breezy. Power filtered with UPS 800 va (South Florida in summer !)

After 1 - 2 - 3 days idling, the screen turns white with a few vertical thin lines; one of the line moves laterally with the mouse. The keyboard is INOP. The only way I found to get out is the power switch !!!

Then I switched to Dapper, now using the 6-15-26-686 flavor, it still happens sometimes.
However if OOCalc is left open, it *seems* to be OK.

I don't really need a fix, but I would really like to understand ....] (*,)

---

### Post by Odinist on 2006-09-15
Possibly an overheating vid card?

---

### Post by jfl on 2006-09-15
My MB has on-board basic video; more than enough for office apps.
Same hardware works fine under W2K ... ???

---

### Post by Odinist on 2006-09-15
Could possibly be the low amount of RAM... I know X-Server is kind of a resource hog sometimes, especially with that low about of RAM and running for a few days straight. Best suggestion I can give you is when it happens, do CTRL-ALT-Backspace. This will restart the X server, effectively defragging your RAM without having to do a full reboot.

---

### Post by jfl on 2006-09-16
Thanks, I didn't think of the RAM; I'm coming of an era when RAM was counted in bytes, (before DOS) then later in kB ... LOL.
I'll try that.
It annoys me, though, that Ubuntu would be more RAM-hoggish than Windoze ...
Can't do CTRL-ALT-BS, the keyboard is completely INOP ...

---

### Post by cptnapalm on 2006-09-16
Wouldn't happen to be an ATi chip would it?  I seem to remember seeing something about a white screen with some configurations.  It could be worse: I know this machine with an ATi card that will crash the system if you try to switch to a console.

Insofar as RAM usage goes, it might be that there is more going on behind the scenes, so to speak, as there may be apps running which you don't know are running.  For example, I had installed crossfire, which is a game.  I didn't know that it would automatically start up the crossfire server on boot up.  I also (knowingly) have MySQL and Apache running.  Even so, when I get to the desktop to login, about 240MB are used out of 1GB (I don't count the stuff which is cached.)  Even so, Linux requires far more resources than it used to (I swear I could do 90% of the same stuff with 1/4 the resources a few years ago) but I am pretty sure that Vistas impending release will swap your experience of which uses more.

---

### Post by Odinist on 2006-09-16
> **jfl said:**
> It annoys me, though, that Ubuntu would be more RAM-hoggish than Windoze ...
Can't do CTRL-ALT-BS, the keyboard is completely INOP ...

It's not that Ubuntu is RAM-hoggish, it's that X is ram hoggish. If the RAM indeed the culprit, it'd be an issue you'll have with any distro that uses the X server, not just Ubuntu. =)

---

### Post by jfl on 2006-09-16
> **cptnapalm said:**
> Wouldn't happen to be an ATi chip would it?  I seem to remember seeing something about a white screen with some configurations.  It could be worse: I know this machine with an ATi card that will crash the system if you try to switch to a console.

Insofar as RAM usage goes, it might be that there is more going on behind the scenes, so to speak, as there may be apps running which you don't know are running.  For example, I had installed crossfire, which is a game.  I didn't know that it would automatically start up the crossfire server on boot up.  I also (knowingly) have MySQL and Apache running.  Even so, when I get to the desktop to login, about 240MB are used out of 1GB (I don't count the stuff which is cached.)  Even so, Linux requires far more resources than it used to (I swear I could do 90% of the same stuff with 1/4 the resources a few years ago) but I am pretty sure that Vistas impending release will swap your experience of which uses more.
Can't remember what chip this machine has; I'll have to open it Monday ... and I'll bring the RAM up to 512 MB.
It is strictly an office box; the only app installed is OO v2.0.2 and of course the stuff that comes with Ubuntu, Firefox, Evo, Gimp, etc...
I'll keep you posted.

BTW, I'm running Windows 2000 and I think it will be the last. It took me a few years to understand, it is fairly stable and runs all what I need ...
If only Linux could run Quickbooks !!!

---

### Post by Neobuntu on 2008-04-02
Still looking for the white screen of death solution...

But note: Kmymoney is an easy addition and is nice for basic Quicken users. Don't try to covert anything (you could use WINE for history on last years Quicken) just start fresh with your balances.

DO NOT upgrade Quicken, you can't go back and you'll have to wait a year for WINE to catch up!

Intuit is a lock-in company to be avoided.

---

### Post by Neobuntu on 2008-04-09
I adjusted her shared video memory in the BIOS to 32MB and the white screen of death is gone! FYI.

---


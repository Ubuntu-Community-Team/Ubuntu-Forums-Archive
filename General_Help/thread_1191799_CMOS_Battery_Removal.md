---
title: "CMOS Battery Removal"
date: 2009-06-19
forum: General Help
---

### Post by Ian-on-the-Trent on 2009-06-19
This thread is related to another ([http://ubuntuforums.org/newreply.php?do=postreply&t=1190851](http://ubuntuforums.org/newreply.php?do=postreply&t=1190851)). I've repeated my request for advice here hoping to reach a broader audience.

============================================================
HP Pavilion N5415 Laptop.

As per the suggestion of removing the battery to clear the CMOS and related password lock; well, it ain't so simple after all. 

I've downloaded a service manual and have disassembled the laptop to the motherboard. Surprisingly, the service manual states that problems with CMOS battery requires a motherboard replacement. What's with HP and their security concerns...further reading of the manual has all of these stipulations about resetting the password which only a service centre is permitted to do.

Anyway, I've found the CMOS battery on the underside of the motherboard. However, there is no quick release type clasp, the battery appears to be soldered in place.  A picture of this is shown below. The penny is there for scale.

[IMG]http://www.itsa.ca/pi/Pavilion_Motherboard/CMOS_Battery_003.jpg[/IMG]

I've got my soldering iron heated up...I was thinking of delicately removing the batteries at the soldered connections (two similar silver blobs at 10 o'clock from the battery). However, I'm asking for suggestions/hindsight for what I am about to do.

---

### Post by wojox on 2009-06-19
Have you tried [http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)
cmos password recovery for linux and HP

Ive seen this before with Compaq they glued there batteries in so instead of paying a couple of bucks for a new battery you payed a couple hundred for a new motherboard.

---

### Post by Ocxic on 2009-06-19
Be Careful, try not to touch any other components. If possible use a heat sink to keep the surrounding components cool. And try not to over heat the board, if you lift a pad by applying too much heat your screwed. Try and find some solder wick to assist with removing the solder as you remove the part. good luck.

Thought: see if you can find a data sheet for the BIOS chip, you may be able to just short some of the pins to get it to reset.

---

### Post by DeMus on 2009-06-19
> **Ian-on-the-Trent said:**
> This thread is related to another ([http://ubuntuforums.org/newreply.php?do=postreply&t=1190851](http://ubuntuforums.org/newreply.php?do=postreply&t=1190851)). I've repeated my request for advice here hoping to reach a broader audience.

============================================================
HP Pavilion N5415 Laptop.

As per the suggestion of removing the battery to clear the CMOS and related password lock; well, it ain't so simple after all. 

I've downloaded a service manual and have disassembled the laptop to the motherboard. Surprisingly, the service manual states that problems with CMOS battery requires a motherboard replacement. What's with HP and their security concerns...further reading of the manual has all of these stipulations about resetting the password which only a service centre is permitted to do.

Anyway, I've found the CMOS battery on the underside of the motherboard. However, there is no quick release type clasp, the battery appears to be soldered in place.  A picture of this is shown below. The penny is there for scale.

[IMG]http://www.itsa.ca/pi/CMOS_Battery%20003.jpg[/IMG]

I've got my soldering iron heated up...I was thinking of delicately removing the batteries at the soldered connections (two similar silver blobs at 10 o'clock from the battery). However, I'm asking for suggestions/hindsight for what I am about to do.

I can only say: Be very careful with soldering on a multilayer board. First of all: what is the size and capacity of your iron? For these delicate things you need an iron with a very small tip and low power, otherwise you will damage something.
The solder has to become soft enough to loosen the grip on the pins and the island on the board, but letting the iron stay too long on one place may overheat components.
As long as the solder is not soft enough don't start pulling on the battery to get it out, since you only tear the copper from the board.
The sides of the holes in the board are covered with a copper layer also to get the same signal from one side of the board to the other. This also means the solder has gone from the island on one side of the board through the hole to the other side of the board. Making it hard to remove.
One thing is very important: don't start pulling before the solder has melted and don't overheat.

Success.

---

### Post by Ian-on-the-Trent on 2009-06-19
Whoa....thanks for all the suggestions. I will pause for now and reread and reconsider what you have all written. Thank you ever so much.

---

### Post by Ian-on-the-Trent on 2009-06-24
> **Ian-on-the-Trent said:**
> Whoa....thanks for all the suggestions. I will pause for now and reread and reconsider what you have all written. Thank you ever so much.

Before undertaking the battery disconnect, I did try the other suggestions first:
1. cmos password recovery for linux and HP (Could find one for an HP laptop of this vintage.)
2. I couldn't find any reference to what pins might be to crossed.

So...I've paused and attempted to refresh the CMOS.

After looking at the solder connection for the battery my first inclination was to release one of the two connections.

[IMG]http://www.itsa.ca/pi/Pavilion_Motherboard/MB-pointer.jpg[/IMG]


As it turns out, there was sufficient space to safely use my soldering iron. Under a magnifying glass, I carefully softened the solder and using a watchmakers screw driver, I ever-so-gently pried the battery connector arm from the solder joint. I slipped a piece of static bag plastic between the arm and the motherboard to keep the connection broken.

[IMG]http://www.itsa.ca/pi/Pavilion_Motherboard/MB-discharge.jpg[/IMG] 

I left it this way for 30 minutes.

I then reattached the battery arm by using a very tiny amount of solder. The reattachment was successful. *(It did take a bit of coordination to look through a large magnifying glass, heat the joint, apply a tiny amount of solder, hold the connection still, and then blow on the joint to rapidly cool the solder. Of paramount importance was controlling the tip of the soldering iron and minimize unnecessary heating)*

[img]http://www.itsa.ca/pi/Pavilion_Motherboard/MB-finished.jpg[/img]


When I rebooted the system the first screen prompt indicated to me that I had successfully cleared the CMOS. However, I don't quite understand what happened next. I was able to look at the BIOS setup, no changes were required so I didn't save anything, rebooted, after a considerable period time (many minutes) the old Post choices appeared...it was as if nothing changed. To enter the BIOS I need to enter a password once again. Talk about a pisser.

I pretty much had to completely take apart the laptop on account of the CMOS battery being located under the motherboard. And unless I did something incorrect when I restarted the laptop for the first time, I'm not inclined to repeat what I did.

Could HP have done something funky with the CMOS/BIOS design?

---

### Post by Ocxic on 2009-06-24
the bios recovered itself due the power loss. you MUST save the config after removing the battery to ensure this does not happen. you'll have to do it again, and ensure you save the config afterwards

---

### Post by Ian-on-the-Trent on 2009-06-24
> **Ocxic said:**
> the bios recovered itself due the power loss. you MUST save the config after removing the battery to ensure this does not happen. you'll have to do it again, and ensure you save the config afterwards

Just to square things up in my mind, I need to:
1. Disconnect/reconnect battery.
2. Reboot, first time into BIOS save the settings.
3. Reboot and I should be good to go?

:confused:

---

### Post by milton1 on 2009-06-24
> **Ian-on-the-Trent said:**
> Just to square things up in my mind, I need to:
1. Disconnect/reconnect battery.
2. Reboot, first time into BIOS save the settings.
3. Reboot and I should be good to go?

:confused:

That should do it. Though some systems will revert completely to factory settings if the battery is removed for extended time (often ten minutes or more).

---


---
title: "X58 compatibility?"
date: 2008-12-07
forum: General Help
---

### Post by rmjohnson144 on 2008-12-07
I just purchased a new nehalem cpu and a Gigabyte X58 motherboard and I was wondering if Ubuntu will work with it?

-=Mark=-

---

### Post by yutrero161 on 2008-12-07
if you wish to be the best man, you must suffer the bitterest of the bitter.*----------------------------THE website offer Fast and Secure wow powerleveling service. [wow power leveling](http://www.wow-power-leveling.org/) 60-70, Cheap [WoW gold](http://www.live4game.com/)  10000G. The Professional [wow power leveling](http://www.wowgoldcc.com/)! Powerlevel  now. WOrld of warcraft Power Leveling,  [World Of Warcraft gold](http://www.live4game.com/) bloom of true love associated with this time of year! [Warcraft gold](http://www.live4game.com/),*

---

### Post by cszikszoy on 2008-12-07
The best way to check would be to spin a copy of the latest LiveCD and find out!  When you boot up with the LiveCD you will be able to tell if your hardware is detected or not.

---

### Post by starfry on 2008-12-17
Hello have you tried this yet? Can you report on your findings?

---

### Post by rmjohnson144 on 2008-12-17
> **starfry said:**
> Hello have you tried this yet? Can you report on your findings?

I hooked up my old hard drive from my x48 and everything seems fine except no internet.  Probably need new drivers.  Even windowws choked on them for my board (GigaByte GA-EX58-Extreme)

On the windows driver install it says it is installing drivers for the 8169E/8168E/8102E/8101E chipsets.  but when I download the windows update drivers. they report 81111 drivers and I losr internet.   I figured they would be 81xx drivers, but maybe not.

anyway, all seems fine so far other than that.

-=Mark=-
ps. I even did a reinstall of Ubuntu (8.10) and same issue.

---

### Post by rbmorse on 2008-12-17
How odd. That board uses the Realtek 8111D LAN chip.  My Gigabyte EP-35-DS3R uses the Realtek 8111B. 

You have two LAN ports. I recall reading somewhere else someone else was having LAN trouble with his Intel X58 board...port0 didn't work but port1 worked fine. Have you tried the other port?

---

### Post by rmjohnson144 on 2008-12-18
> **rbmorse said:**
> How odd. That board uses the Realtek 8111D LAN chip.  My Gigabyte EP-35-DS3R uses the Realtek 8111B. 

You have two LAN ports. I recall reading somewhere else someone else was having LAN trouble with his Intel X58 board...port0 didn't work but port1 worked fine. Have you tried the other port?

yeah, the port works fine in windows, but no I didn't try trhe other one.

anyway, I got it to work when I installed 32-bit Ubuntu 8.10.  Must be a 64-bit thing?

-=Mark=-

---

### Post by starfry on 2008-12-20
Hi, could you do me a favour and look in your BIOS and tell me what the floppy drive options are? Specifically does it have options for two floppies (drive A and drive B) and what drive formats does it support (2.88, 1.44, 1.2, etc) ?

Before anyone says "why do you need floppies - they're obsolete?" I provide an archiving service and need to access both a 3.5 and 5.25 floppy drive. I hope to decommission a legacy box that I keep for that service.

---

### Post by rmjohnson144 on 2008-12-20
> **starfry said:**
> Hi, could you do me a favour and look in your BIOS and tell me what the floppy drive options are? Specifically does it have options for two floppies (drive A and drive B) and what drive formats does it support (2.88, 1.44, 1.2, etc) ?

Before anyone says "why do you need floppies - they're obsolete?" I provide an archiving service and need to access both a 3.5 and 5.25 floppy drive. I hope to decommission a legacy box that I keep for that service.

Not sure, I don't use floppies.  I do remember disabling it though so it won't give me the warning of device missing.  I can't check for it as it was giving me issues so I returned it.  I have a DFI X58 board on the way.

Maybe try the gigabyte website.

-=Mark=-

---

### Post by ramen on 2008-12-23
Have an i7 working on ex58-ds4
64 bit wouldn't load. Had to go for 8.04 32 bit works fine..
networking carked it but booted fine with a usb network  but had to disable the on board networking in bios.

Waiting for the PTB to update 64bit will be straight into when the word is out that all works

Any one at all got this combination to work in 64bit 8.04 or 8.10

---

### Post by ramen on 2008-12-23
> **starfry said:**
> Hi, could you do me a favour and look in your BIOS and tell me what the floppy drive options are? Specifically does it have options for two floppies (drive A and drive B) and what drive formats does it support (2.88, 1.44, 1.2, etc) ?

Before anyone says "why do you need floppies - they're obsolete?" I provide an archiving service and need to access both a 3.5 and 5.25 floppy drive. I hope to decommission a legacy box that I keep for that service.

Drive A only

options
none
360k -5.25
1.2m - 5.25
720k - 3.5
1.44m - 3.5
2.88m - 3.5

Floppy 3 mode support

options 
Disabled 
Drive A

---

### Post by rmjohnson144 on 2008-12-23
> **ramen said:**
> Have an i7 working on ex58-ds4
64 bit wouldn't load. Had to go for 8.04 32 bit works fine..
networking carked it but booted fine with a usb network  but had to disable the on board networking in bios.

Waiting for the PTB to update 64bit will be straight into when the word is out that all works

Any one at all got this combination to work in 64bit 8.04 or 8.10

hmmh, that's strange.  I have the extreme version of the board and mine worked fine with the exception of no lan driver.  the DS4 is identical with only a few minor differences.  I was using the 8.10 version.

---

### Post by starfry on 2008-12-24
Thanks for that. As I feared - drive A only. Will have to keep that old box lying around ;)

---

### Post by starfry on 2009-02-23
> **rmjohnson144 said:**
> I have a DFI X58 board on the way.
-=Mark=-

Is that the DFI UT X58-T3eH8 you mean? Have you got it yet? How is it?

It's my current board of choice so I'd be very interested in how you're getting on with it. I've also spoken to DFI about it and they tell me it even supports drive A and B which would make us very happy here :) It'd be great if you can confirm that and also any info about your experiences with Linux on it.

It looks like a great board!

---

### Post by rmjohnson144 on 2009-02-23
The board works great!  I even bought a second one for my backup/server machine.  Not sure on the floppy issue as I don't have floppies anymore.  It does have a floppy connector though, so I would assume it supports two.

-=Mark=-

---

### Post by GSF1200S on 2009-03-07
Kind of bringing back an old thread, but I thought Id share my experience.

I purchased an Asus Rampage 2 Extreme x58 mobo with the 920 i7 and 2 9800GTX+'s. Ubuntu 8.10- Surround sound out of the box, ethernet out of the box, and with a minor tweak in the xorg.conf, I have dual monitors running seperate X screens.

However, a few words of caution that might help: The first Rampage 2 I recieved had a bad pcix16_slot1, so I had to RMA through Newegg. Also, the Rampage is supposedly pickey about components that go with it, causing many people to have cold boot issues. I both researched alot and got very lucky, but I have 0 problems (knock on wood)-

6GB DDR3 Corsair Dominator 1600mhz 8-8-8-24 (NOONE on newegg has problems with this RAM so far)
Silverstone 1000w power supply (this is a great deal, but it is NOT modular and youll be routing cables everywhere!)
Asus Rampage 2 Extreme (it is a little bigger than normal, so make sure the case fits it- it is also too expensive, period. I only bought it because I found the exact ethernet and audio chipsets listed as working on various forums/sites)
Cooler Master HAF 932 Case (4 fans is good, but this case is huge. Overall, good deal and fits everything..)

Mainly RAM and the power supply are what cause problems so I hear..

I hope this helps, and do like I did and install Ubuntu first before those other distros ;)

---

### Post by xixor on 2009-03-18
Howdy Folks,

Just adding my experience:  i7 920, ATI 4870x2, Giga-Byte X58 UD3R board.  I believe this to be running the Realtek 8111D 10/100/1000 chipset.

8.10 64 bit seemed to install fine, and I thought it appeared to configure DHCP fine during the installation.  Boot into the system and the network card doesn't load.  I run lspci -v and I don't see it anywhere on the list.

Does the installer perhaps somehow load a 32bit driver and that is why it appears to load?

Anyone have any advice on how to get the network card installed using 8.10?  32 bit is not an option I'd like to try: I do numerical modelling that requires more memory that 32 bit can provide.

Thanks,

xixor

EDIT: after finding a similar post on the opensuse forums, I tried shutting down the computer and unplugging the power supply.  Then, on the reboot, I enabled the boot rom of the onboard lan in the bios.  I have no idea what the boot rom of the onboard lan is or does.  But, on the next reboot into 8.10, the drivers were loaded.  lspci -v shows RTL8111/8168B Ethernet controller.

Interesting to say the least.

---


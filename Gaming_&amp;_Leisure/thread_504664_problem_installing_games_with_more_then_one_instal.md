---
title: "problem installing games with more then one installing cd in wine???"
date: 2007-07-19
forum: Gaming &amp; Leisure
---

### Post by doh224 on 2007-07-19
hi all... I'm trying to install, jedi academy, and empire earth 2. both these games have two installation cd-roms. (both these games should be able to run with wine) The installation runs fine   until I have to change to cd 2... it didn't allow me to eject, so I searched some threads and found one saying that, sudo umount -l /media/cdrom(nummer), and then, sudo eject /media/cdrom(nummer), would work... and it did. but when I set in the cd rom nummer two, and mounted it.. it only sees it as disk 1 and not disk 2?? ?? 
I've also tried wine eject.. but with no success... what to do? if some would give me some help solving this problem, then I would be very thankfully...

-doh

---

### Post by FunkyJack on 2007-07-19
On my ubuntu cd-s are mounted under /media/(name of the CD)

So if cd name is EE2CD1 them it is mounted under:

```
/media/EE2CD1
```

So then

```
sudo eject /media/EE2CD1
```

---

### Post by smah77 on 2007-07-19
wine eject usually works for me but I often have to enter it twice for some reason...

---

### Post by doh224 on 2007-07-22
> **smah77 said:**
> wine eject usually works for me but I often have to enter it twice for some reason...

I can eject the cd... but i can't set another disk in the drive and get the computer registering it, so I can't get on with the installation

---

### Post by dragonwings on 2007-07-22
what i did was installed game on my windows hard drive 
then used an install maker program(freeware) made an install disk 
from installed files from c drive programes (i added a nocdcrack before making disk)
bingo got a sweat as install disk of the game for linux/wine

may help to use the latest version of wine see below

July 13, 2007: Wine 0.9.41 Released

Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.

---


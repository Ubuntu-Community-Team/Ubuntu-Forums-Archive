---
title: "HP Printer Support"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Brando569 on 2006-07-04
where am I supposed to get the modules/drivers for the two HP printers that I own?? Ive tried to install my HP 1610 AIO several times and it has never worked for me, now i have to install an old Deskjet 870cse for my parents but I dont know where to get anything for it...

thanks

---

### Post by AndyCooll on 2006-07-04
Not sure about the first one, but as far as I'm aware the DeskJet 870cse already has the driver pre-installed you just need to select it. I'm not at my Linux box at the moment, however I think the process is something along the lines as follows

Administration-->Printers-->Add Printer

Choose local printer. Then select "HP" followed by 870cse (or 870c or 870cxi if cse isn't listed). This is what I do for my 990cxi and it works fine for me.

:cool:

---

### Post by tonyr1988 on 2006-07-04
Ditto. I have an old HP DeskJet 682C, and it worked beautifully. Just plug it in, select which type it is, and it will automatically configure it for you. You don't even need an Internet connection (I didn't have one).

---

### Post by dimitrif on 2006-07-04
Does anyone know what driver one can use for an HP Laserjet Color 1600?

The web searches claim a foomatic driver for HP 1600, but the problem with it is I can choose color till it comes out my ears - it ALWAYS prints in Grayscale... :confused: 

Any ideas??


Dim.

---

### Post by toorima on 2006-07-04
Also have a problem with a HP printer, I have a Deskjet 710C and it prints but won't use the black cartridge, it uses the color cartridge to make black. Anyone else seen this and might have a solution?

---

### Post by Brando569 on 2006-07-05
from what i see there are only 4 printers listed under HP and they are all Laserjets (1000,1005,1020 and 1500 i believe)

---

### Post by Brando569 on 2006-07-11
the 870cse was easy to install (aptitude purge hplip then reinstall it) but the 1610 never wants to work in dapper for me. worked fine in breezy...

---

### Post by Silen on 2006-08-13
I can see that I'm not the only one with this problem:

I have installed the foo2hp driver for my HP Color LaserJet 1600 .......BUT it will only print in b/w (the HP 1500 driver is incompatible) - colours enabled in CUPS

Can anyone help? Has it something to do with the ghostscript version? Do I need to enable the colours elsewhere? Any suggestions are much appreciated.

Cheers,
Kim

------------

edit: sorry, it CAN print in colours - just not the test page in CUPS, that's in b/w... so, if you have any problems with HP Color LaserJet 1600: Install the foo2hp driver: [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/)

---

### Post by stengah on 2006-08-16
I've just (reletively) successfully installed HP Color LaserJest 1600 on Ubuntu Dabber 6.06 using the instructions on this homepage: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Only problem; poor color adjustment options (Blue is rather purple in test prints). Also cannot print .gif files unless embedded within an Open Office file (at least I could not).

I'm currenmtly looking for solutions... think the color issue might improve using some ghostscript options, but I'm completely in the dark concering GS. If anybody have any ideas please post'em!!

TIP: Remember- use cups management

[INDENT]sudo gnome-cups-manager[/INDENT]

to change the profile from 'monocrome' to 'color' (right click -> properties ->. Test page prints appear b/w unless you do so.

---

### Post by Johnathon on 2007-07-09
You also need to restart cups "sudo /etc/init.d/cups restart" after you've set for colour, to fix a bug.

---


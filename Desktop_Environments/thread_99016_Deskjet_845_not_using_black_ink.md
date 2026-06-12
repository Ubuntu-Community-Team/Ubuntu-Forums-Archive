---
title: "Deskjet 845 not using black ink"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Tristan_B on 2005-12-04
Hi all,

I've been using Ubuntu for a while, but only just joined the forums -- so hello to everyone.

Unfortunately, despite loving Ubuntu, I have a slight problem. I've just been given an HP DeskJet 845C printer for free. I've read that HP printers have excellent Linux support, and when I plugged it in (via USB), it was indeed automatically detected in the "add printer" dialogue, adn I was able to set it up to use the (recommended) HPIJS driver.

However, no matter what I do, the printer seems to insist on using the colour cartridge to print black, rather than the black cartridge. This is slow, wasteful, expensive and just plain bad. I've done a bit of Googling, and it seems I need to use an "RSS patched" HPIJS driver?

Does anybody know where I can get this driver for Ubuntu? Or is there another solution that I haven't yet discovered? Has anyone else with a DeskJet experienced this?

All and any help is appreciated.

Many thanks,

Tristan

---

### Post by eradusfalk on 2006-02-09
Go to Linux Printing Org......... there you will find that driver.
Have the same problem with my HP deskjet895Cxi and that's why I am here. The patched driver did not work for me.
You can try Gimpprint. It does not do a nice job on photo's but at least you can print black and color at the same time.

Eradus

---

### Post by yigal.weinstein on 2006-02-14
hp 940c same problem - if you read old threads please reply if you have found a solution.  I just want to print some work I mad - pdf files mostly, just black ink.

---

### Post by Zalbor on 2006-02-14
If you go to System>Administration>Printing, right-click on your printer and select Properties, in "Advanced" there's printout mode and you can choose "Black cartridge" there. I don't know if it will work, I never tried it, and I assume in that case the photos would be in grayscale... But it might be worth trying.
Mine is a 3550, and yes, with the "normal" setting it doesn't use the black cartridge.

---

### Post by mihai10 on 2007-04-08
I have  Deskjet 845C that was also refusing to use blank ink cartridge. It only started to work after I changed a setting. System > Administration > Printing > right click on the printer icon > Properties > Driver > Select "High Quality Image (Gutenprint) (en). As you might know, the default (recommended) setting is hpijs.

---

### Post by chibiace on 2007-04-08
my HP printer would print out red instead of black because it didnt like some of the draft options, trying each of the print out modes might give different results.

---


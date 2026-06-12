---
title: "hard drive crash xp"
date: 2009-03-05
forum: General Help
---

### Post by kawika molon labe patriot on 2009-03-05
need help my xp hdd crashed. I am on the ubuntu live cd. I tried to do the dual boot and it would not let me partition the hard drive. I think I have bad sectors. what are my option, can I save xp, can I just wipe xp off and load ubuntu, will games I play on xp work on ubuntu, if I backed up my personal files can I load them on ubuntu.is my hdd junk. I had just run chkdsk from command and it froze on me on the restart it went into chkdsk again. made it to step 3 and then the screen went black and now xp will not start. I get the boi screen (if that is what it is called) then a flashing dash at the top of the screen and that is where it stops. mahalo for any help anyone can give me!

---

### Post by taurus on 2009-03-05
It's time to get a new harddrive.

---

### Post by Darkoan on 2009-03-05
mmmm not necessarily taurus

This a very newbie speaking, so much respect to you but....

I had problems with Ubuntu and XP set up recently - turned out my XP was just a bad copy - It installed XP and Ubuntu separately fine, but the combination of the two (dual boot) was bad - and Im sure it had something to do with the partitioning and bad a XP boot disc.

Before buying a new HDD, acquire (download for free and burn if you can) a program like Parted Magic to totally erase your HDD ('zero' it), and then try reinstalling your two OS. Obviously, wiping your hard disk is TOTAL wipe of your entire hard disk - this should be your last option before buying a new HDD! Its what I did.

And re games, many Windows games can be played in Ubuntu through various linux application (eg Wine) BUT many very modern games have problems, and because of the delay in linux pros in 'assimilating' new games it can be an inconsistent experience. This is the reason I dual boot.

---

### Post by ramjet_1953 on 2009-03-06
You could try downloading the latest Hiren's Boot disk image and burning it to a CD.

Then boot from the CD and use the recovery tools on the disk to see if you can recover and repair.

You can get the image from RapidShare:

[http://rapidshare.com/files/179229975/9Down.COM___Hirens.BootCD.9.7.with.keyboardpatch.rar](http://rapidshare.com/files/179229975/9Down.COM___Hirens.BootCD.9.7.with.keyboardpatch.rar)

Regards,
Roger :D

---

### Post by lykwydchykyn on 2009-03-06
On the live cd, please open a terminal and run this:

sudo badblocks -v /dev/sda

That will scan your hard drive for bad sectors.  If you have a bad sector, the number will be printed on the screen.  If you get a big long list of numbers, that means you have a lot of bad blocks.  Time to get a new hard drive.

If it passes with zero badblocks, your hard drive is likely (though not guaranteed) ok, and you may just need to reinstall XP from scratch (or switch to Ubuntu!)

---


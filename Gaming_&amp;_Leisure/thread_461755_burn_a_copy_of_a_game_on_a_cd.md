---
title: "burn a copy of a game on a cd??"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by Fittersman on 2007-06-02
does anyone know how to make another copy of a (windows) game CD? (command and conquer generals)

my cds are getting pretty beat up, so i want to make a copy of them incase they break, but when i try it wont let me...

i tried alcohol 120%, but it goes at a rediculously slow speed

are there any programs out there that will allow me to burn the CDs properly? i would really like be able to continue playing the game if my cd breaks...

---

### Post by hikaricore on 2007-06-02
Well you can easily copy a cd from the command line like so:

> dd if=/dev/cdrom of=~/diskimage.iso

This will make an ISO image of the disk you can then burn to another CD.

If your original disc is in terrible shape and has read trouble, you can try:

> dd if=/dev/cdrom of=~/diskimage.iso bs=512 conv=noerror,sync

This sets the blocksize to 512 (this will take a long time but copy as best your drive can read) and noerror means it will not fail on read errors, it will try again.

Other than that there are dozens of cd rippers and burners in the software repos that you can find quite easily if you just look.


p.s. If your game has copy protection it may or may not cause issues, be aware that some copy protection schemes CAN make your game disc unreadable on certain operating systems.
This kind of crap has stopped happening as much in the last few years, but I have seen the odd cd be a pain in the *** from time to time.

---

### Post by Cappy on 2007-06-02
This is somewhat off-topic, but worth sharing:
[http://www.g4tv.com/screensavers/features/37127/How_to_Remove_CD_Scratches.html](http://www.g4tv.com/screensavers/features/37127/How_to_Remove_CD_Scratches.html)

---

### Post by hikaricore on 2007-06-02
> **Cappy said:**
> This is somewhat off-topic, but worth sharing:
[http://www.g4tv.com/screensavers/features/37127/How_to_Remove_CD_Scratches.html](http://www.g4tv.com/screensavers/features/37127/How_to_Remove_CD_Scratches.html)

Great info.

Now, if only I could educate my girlfriend and her children about how to handle CD/DVDs...

I don't even want to remember how many times I've purchased "Shrek".

---

### Post by Ripfox on 2007-06-02
hahah...I don't even want to see shrek....EVER

---

### Post by Fittersman on 2007-06-02
yeah, it has copywrite protection, so that suggestion doesnt work, any other ideas?

---

### Post by anjilslaire on 2007-06-02
Check this out:
[http://club.cdfreaks.com/showthread.php?t=141629&highlight=command+conquer+generals%29](http://club.cdfreaks.com/showthread.php?t=141629&highlight=command+conquer+generals%29)
For more details regarding SafeDisc:
[http://www.cdmediaworld.com/hardware/cdrom/cd_protections_safedisc_v2.shtml](http://www.cdmediaworld.com/hardware/cdrom/cd_protections_safedisc_v2.shtml)

From what I 've seen C&C Generals uses SafeDisc 2.8

---

### Post by Nehvrook on 2007-06-02
Just use a no-cd crack, couple of Megabites at the most and easy to use. Google it

Or download the game from a file Sharing site. The reason all filesharing sites aren't just closed down instantly is because it's not illegal to make backups. If you actually OWN generals you're allowed to download it as a backup

---

### Post by Fittersman on 2007-06-04
> **Nehvrook said:**
> Just use a no-cd crack, couple of Megabites at the most and easy to use. Google it

Or download the game from a file Sharing site. The reason all filesharing sites aren't just closed down instantly is because it's not illegal to make backups. If you actually OWN generals you're allowed to download it as a backup

i tried a no cd crack, but when i tried to play online it didnt let me because it said i have a different version of hte game

and ill try the other suggestions too, thanks

---

### Post by DarkW0lf on 2008-05-31
Have you actually tried the dd method ?

My attempt has been running for two almost three hours now (0.8kB/s).

I am trying to get a good copy (iso) to run in a VM.
It's weird, I can install from the disc but not run it ???
Disc two copies fine but not one, only the first one is protected.

---

### Post by DarkW0lf on 2008-06-03
2nd dd method works, I have a good copy of disc (took several hours).

Virtual Box though does not have proper video support for game.

---


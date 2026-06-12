---
title: "Installation problems"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Oren on 2005-11-03
Hey guys (and gals)

I am at wits end. Just do not know what to do next.

This is my set-up - I have three drives (this is their order in BIOS).
1. IDE master disk - NTFS with Windows XP pro
2. SATA drive - which I would like to have Ubuntu on
3. IDE slave drive - FAT32 which is a file pool.

I have originaly started with Windows XP.
Now I am trying to install Ubunto and dual-boot.
I go through the install and partition my drive with EXT3 for '/' and swap.

The install goes well and then comes the GRUB part.
I let the installation take over and it tells me it is installing GRUB to HD0 (first IDE drive). Then the compuetr re-boots and gives me an error 17.

Now I have tried all sorts - I tried specifiying the IDE drive with /dev/hdc I tried to install the grub on the sata drive and specif /dev/sda for grub and then set the sata drive as first drive (in BIOS). But all I get is error 17. 

I used to have Windows on the sata drive and Ubuntu on one of the IDE drives and it worked fine. I am really lost and I do not know what to do next....Any help will be appreciated and I hope I included all the details.

---

### Post by jvictor on 2005-11-03
SATA drives can b a pain some times on linux... only some manufacturers Sata drives work on linux. I came to know abt this and opted for a barracuda instead of a SATA when i bought my machine...

chk this link 
[http://ubuntuforums.org/showthread.php?t=65575&highlight=Error+17](http://ubuntuforums.org/showthread.php?t=65575&highlight=Error+17)

As far as I can say y dont u use the config u used earlier ? IDE for linux and SATA for win ?

---

### Post by Oren on 2005-11-03
mmmmmm
Interesting.

I wanted to use Ubuntu as my main installation therefore decided to install it on my main, largest best drive - the SATA drive.

But obviously if this is going to turn into a major pain I will have to go back to the original set-up. Or get rid of windows and start fresh from Ubuntu and then install Windows.... see if that works.

Thankfuly I do not rely on my computer for work and use it just as a hoby :razz:

---

### Post by jvictor on 2005-11-03
Well just its too early to switch just hang on , there maybe some SATA guru who can help u out, i'm not knowledgable enuf on SATA probs, I'm v sorry i cant b of much help in this :(

---

### Post by Oren on 2005-11-03
No, no rush for me.

Like I said this is a hoby.
I am sure I can live another day using Windows......:o 

Thanks anyway, and hey - noone knows ***everything***

Take care and thanks for the help.... :smile:

---

### Post by nolan- on 2005-12-13
Hi,
I have just completed a Ubuntu install on SATA, my system has 2 SATA and 1 IDE.
It was a bit of a struggle but here's how i got it done.

I was having the same problem where the install would run through until it installs grub, spits out the cd and reboots to complete the install. 
Then nothing it just hangs after bios info......i also noticed that grub was installing on the IDE. 

After numerous unplugging HD's and reinstalling the only way i found to install on SATA is to unplug every drive apart from the SATA that you wish to install on then the install works fine.

The only thing is that when you shutdown and reconnect the other drives you then have to edit /boot/grub/menu.lst if you have windows on another drive.
Grub will have done this ---> #hiddenmenu  just uncheck it and add windows info into grub.

My windows entry in grub is :-
```

title           Windows XP
root            (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader     +1
```


Windows on my system is on another SATA drive, i imagine if you add this and simply replace the 2's with 1's it *should* boot.......

---


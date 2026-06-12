---
title: "new build- CRC errors and other problmes"
date: 2009-06-05
forum: General Help
---

### Post by blur xc on 2009-06-05
I'm going to back this up a bit, some of which is unrelated to ubuntu but still, maybe someone here can shed some light on anyway...
 
So, I built a new pc, fist time build too, btw-
Antec 300 case
Western Digital Caviar Black 500gb sata hdd
gskill 4gb ram- 2 x 2gb ddr2 1066 pc2 8500
sony optiarc 24x sata cd/dvd rw
edimax ex-7128g pci wireless card (said linux compatible on the box)
aft pro 35u usb2.0 card reader
gigabyte ga-ep45-ud3p lga775 mobo
bfg tech nvidia geforce9600 gt 512mb 
intel core 2 duo wolfdale 3ghz
thermaltake 750w psu
 
grand total just about $1000
 
Ok, so last night was the maiden voyage, plugged it in, turned it on, and nothing.  Black screen- no post- no bios...  yay
 
I try a different monitor- still, no dice...  So, off to google I go..  after some research I resolve to just remove some junk from the mobo and try again.  I yank out the wirelss card and BAM! Post!  So, I get to bios, mess w/ some settings.  Set boot priority- and start installing ubuntu...  
 
Problem 2- I guess I burned my disk too fast or something, so I throw that one away, and back to the pc that works, I download a new iso (for safe measure) and burn a new boot disk at the lowest speed setting...
 
Install take 2- success!  So now I'm ubuntu-ing, I install drivers (nvidia), wirelss sets up quickly (so somehwer up there, I put the wireless card back in, and it booted up ok)...  
 
I do some more reboots while I configuring everything, and all is aok...   I go to bed a happy man.
 
So, I wake up today, push the power button, and bam- no post.  After a few tries, I remove the wireless card again, it boots up, so i put it back in, and it booted up agian.  got online, etc...  now, a lot happened in a short amount of time so I don't know exactly in what order it occured, but I did a few test boots, and I got some CRC - system halted errors, a few kernel panics, etc...  So I've got some kind of intermittent problem.
 
So, finally I just had to get dressed and come to work (yay), so I left it at that, a computer that won't boot.  
 
When I get home I'll try removing the wireless card again, and maybe WRITE DOWN the errors I'm getting.
 
I'm mostly concerned about the crc errors and the kernel panic.
 
thoughts??
 
thanks in advance
BM

---

### Post by Yellow Pasque on 2009-06-05
Did you verify the md5sum of the .iso and/or run the Integrity test from the LiveCD menu?

Other thought: Perhaps updating the BIOS will help with the POST issue? If you do that, make sure the wireless card is NOT connected when you do the flash.

---

### Post by blur xc on 2009-06-05
ok- I'm pretty sure I don't know what the md5sum is and I'm also pretty sure I didn't do an integrity test.  How do I go about doing either of those things?
 
Also, I'll have to read my mobo manual again, but I recall the bios flash instructions were written for a windows os....  
 
BM

---


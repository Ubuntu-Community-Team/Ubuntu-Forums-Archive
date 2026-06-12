---
title: "Tricky Compaqs"
date: 2006-01-05
forum: General Help
---

### Post by SoulReaper on 2006-01-05
I heard that Linux has issues with running on Compaq MB's because of Custom BIOS.  Is this true?  I'm beginning to think yes because I was having trouble booting last night.  Just after the grub loader the computer just freezes.  There is a cursor in the upper left hand corner and it does not flash.  The computer actually seems completely frozen.  I can't even figure out how to get into the bios on this computer now either.  

I was thinking of swithching the HD into another almost identicl Compaq, but if it is a compatibility issue with Compaq then that would be a waste of time.

---

### Post by byen on 2006-01-05
Im not sure about the older versions but i do have a 2003 compaq laptop with a compaq motherboard and I havnt faced any issues related to motherboard so far (in almost 2 years of linux use).
Now After looking at your previous posts I see that you have had trouble with the integrity of the cd that you installed Ubuntu from. 
1.Did you download a new copy when you installed Ubuntu or did you just re-burn the same iso onto a different cd?
2.Did this happen during your first boot or when you tried tweaking your hardware.
3.Can you give us more info on the configuration of your system (graphic card etc)
Hope this problem can be solved quickly.

---

### Post by srt4play on 2006-01-05
I'm running breezy on a compaq evo desktop and have no issues. 
I think it's the delete key to get into the bios, I can't remember.  Try delete and F1.  And all the other function keys if they don't work.  Sorry, I'm too lazy to reboot and find out. :)

Have you tried booting into rescue mode?

---

### Post by SoulReaper on 2006-01-05
[QUOTE=byen]Im not sure about the older versions but i do have a 2003 compaq laptop with a compaq motherboard and I havnt faced any issues related to motherboard so far (in almost 2 years of linux use).
Now After looking at your previous posts I see that you have had trouble with the integrity of the cd that you installed Ubuntu from. 
1.Did you download a new copy when you installed Ubuntu or did you just re-burn the same iso onto a different cd?
2.Did this happen during your first boot or when you tried tweaking your hardware.
3.Can you give us more info on the configuration of your system (graphic card etc)
Hope this problem can be solved quickly.[/QUOTE]

1.  The integrity issue is fixed.  I redownloaded and burned a new CD and did the check which it passed.

2.  My first boot I got in, unfortunately I was getting ready to leave and I shut the computer down because I wanted to add my NIC Card, Graphics Card, and Soundcard when I got back.  I added the cards, and that is when I ran into issues booting.  Could the cards be a problem?

3.  I don't have the comp in front of me but off the top of my head here is the config:  Pentium III, 128 MB SDRAM, 250 GB Western Digital IDE drive (Brand New) Graphics Card-NVidia Gforce 64 mb (I believe), Soundcard is an OLD Soundblaster (nothing fancy just a basic card) and the NIC card is a D-Link ethernet card.




SRT4play:  I tried F1 and I swear that's what worked originally, but after I installed Linux it is not working.  I had a little trouble getting to the BIOS originally to change the boot order so I could install Ubuntu.  Now I want to change the boot order back to see if that is causing a problem and I can't get back into the BIOS. I am going to try delete when I get home.

---

### Post by SoulReaper on 2006-01-05
Ok, so I got it to boot up again.  It wasn't the Compaq, it was actually the video card strangely enough.  After I removed the video card it booted right up no problem.

But now, I cannot connect to the internet/network.

Would this have anything to do with the fact that while installing Ubuntu I didn't have the NIC card installed?  Do I need drivers?  


Eventually I'll stop asking so many questions and I may be able to answer some.

---


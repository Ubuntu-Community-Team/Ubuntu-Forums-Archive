---
title: "SD Cards"
date: 2009-04-10
forum: General Help
---

### Post by PhilM44 on 2009-04-10
I have been using Ubuntu Hardy Heron since it first came out and have had no problem transferring data to and from SD Cards.  All of a sudden this week I have not been able to write to any SD Cards.  I have not made any changes to my system save from the automatic system updates.  Connection is via a plug in card reader which has not changed nor has the USB port I use.

I have checked the SD Card tags and they are all unlocked and I can write to the cards using Windows or Windows Mobile 6.

I have tried changing the properties but this does not make any difference.

Can someone please help as this is very annoying?

---

### Post by mp035 on 2009-04-10
Can you check your card reader on another machine?  I have had several card readers (read: from China) fail after about 2 months.

Also, try the lsusb command from the console, check the results to see whether the system is recognizing your card reader.

These are both lame solutions, but it's a starting point.

---

### Post by Sef on 2009-04-10
>  These are both lame solutions, but it's a starting point.

They are not lame solutions.   It is best to start with the simpliest ways to resolve a problem before getting more complicated.

---

### Post by mb_webguy on 2009-04-10
I haven't had your specific problem, but I have had problems with SD cards.  A little less than half of the SD cards I've tried in my laptop's internal reader under Ubuntu will work fine -- up to a point.  While the system will correctly detect the size of the card, when copying files to a card I'll get an error saying the disk is full at about half the actual (and detected) capacity.  And of course the cards would work just fine on the same computer under Windows.  I found the solution was to reformat the cards using mkfs (since GParted wasn't detecting the device).  After that, I no longer had any problems with any of the cards, regardless of the OS.

As mp035 said, it's a crap solution, and almost certainly won't help your particular problem, but it's worth a try.

---

### Post by PhilM44 on 2009-04-10
Thank you - this appears to be the problem - my card reader appears to have just stopped working properly.  I have tried another reader and it works fine.

Thank you.

---


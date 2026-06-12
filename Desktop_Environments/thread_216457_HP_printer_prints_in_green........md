---
title: "HP printer prints in green......."
date: 2006-07-15
forum: Desktop Environments
---

### Post by vinayasurya on 2006-07-15
I have a HP deskjet 3325 printer installed to my ubuntu system. But print color is always set to green even if i print black text. I haven't tested color printd though. What may be the problem? How can I fix that?

---

### Post by vinayasurya on 2006-07-17
Someone answer please.........

---

### Post by Joeb on 2006-07-17
> **vinayasurya said:**
> I have a HP deskjet 3325 printer installed to my ubuntu system. But print color is always set to green even if i print black text. I haven't tested color printd though. What may be the problem? How can I fix that?

If I'm not mistaken, that printer only allows for a color cartridge OR a black cartridge, but not both to be installed at the same time.  If so, and the color cartridge is installed, it will mix the colors to produce black (many inexpensive ink jets do that). However, if one of the colors is out or the jets are plugged, you will get some other color besides black.

To test that theory, print something in color and see if the colors look right, most likely, they won't.

The solution will be to buy a new cartridge.  I would recommend, however, that if you are going to be printing a lot of text, that you purchase a black cartridge.  Both black and color cartridges hold the same amount of ink, however, the color cartridge uses all three colors to make black so it gets used up much quicker.  Use the black cartridge for normal text and put the color cartridge in when you want to print color.

If you try printing in color and it looks correct, it could be that the cups driver in linux thinks you have a black cartridge installed even though you have a color cartridge and therefore isn't telling the printer to fire all of the ink jets needed to produce black.  To check for this, you would need to go into the printer configuration and see if it has a setting for the type of cartridge (black or color) and whether it is set appropriately.

If it turns out that the problem was just the wrong cartridge type being set, I would still consider using a black cartridge as described above.

---

### Post by vinayasurya on 2006-07-18
The printer has two catridges one for color and one for black. Even manually setting to black catridge in printer properties failed to print in black.

---

### Post by Joeb on 2006-07-18
> **vinayasurya said:**
> The printer has two catridges one for color and one for black. Even manually setting to black catridge in printer properties failed to print in black.

I thought the HP 3325 only has one cartridge slot, at least that's what most of the web info says.  Are you sure it is a 3325 or do you mean you have two cartridges but using the black cartridge, the printer still failed to print (as in nothing printed)?

---

### Post by Sef on 2006-07-18
> I thought the HP 3325 only has one cartridge slot

The 3000 series has two cartridge slots.

> have a HP deskjet 3325 printer installed to my ubuntu system. But print color is always set to green even if i print black text.

1) How often do you print?  

2) Did this just start?  

3) Have you had this problem with other cartridges?

---

### Post by vinayasurya on 2006-07-22
I am newbie to ubuntu linux. The printer has no problems working in Windows. I tried with printer property settings but no change. Is this a driver problem?

---

### Post by vinayasurya on 2006-07-28
Someone reply plz.........

---

### Post by danderson3 on 2006-09-07
I have the same problem with an hp 99cse, but printing in red
all of a sudden.

David

---

### Post by danderson3 on 2006-09-09
It turns out I ran out of black ink...

-d

---


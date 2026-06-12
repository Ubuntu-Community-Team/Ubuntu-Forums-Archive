---
title: "Crashing, how do I troubleshoot?"
date: 2009-03-30
forum: General Help
---

### Post by sekinto on 2009-03-30
My computer has been crashing recently, at least once every day... and it seems to be happening more and more often. It does not matter what operating system I use either.

This is what I mean by crashing:
Windows example: Blue Screen of Death
Linux example: X freezes and I can't move cursor, if a sound was playing it gets locked in the same spot and keeps on repeating that same thing, cannot do anything including restarting X or dropping into a virtual console.

Is there any software I can use to find out what piece of hardware is causing this? I've run memtest86+ twice with no positives, so I'm pretty sure it isn't my RAM.

---

### Post by simtaalo on 2009-03-30
does the same thing happen if you boot using the recovery kernel?

---

### Post by sekinto on 2009-03-30
Haven't tried. So you think it is just a coincidence that I've had this problem on 3 different operating systems (and it happens at random times).

---

### Post by simtaalo on 2009-03-30
no idea, its just one of the first things i would try.

---

### Post by sekinto on 2009-03-30
Okay, I'll try it next time I turn on this computer. But I'll need a few days to pass before I can accurately report a positive. I really don't think it will solve the problem, but anything is worth trying I guess.

:-({|=

---

### Post by simtaalo on 2009-03-30
it almost definitely won't solve the problem but it will tick something off the list of causes which is what troubleshooting is all about.

---

### Post by sekinto on 2009-04-05
Recovery did not help, I still had issues. Is there anything else I can try. I really do believe this is a hardware problem, I just don't know of any good ways to test hardware. I'm guessing it might be my hard drive, but I'm really not sure.

---

### Post by markbuntu on 2009-04-05
run the memory test in the grub menu. It sounds like you have some bad ram.

---

### Post by sekinto on 2009-04-05
> **markbuntu said:**
> run the memory test in the grub menu. It sounds like you have some bad ram.

In the OP I mentioned that I had already run memtest86+ twice, but I will run it two more times just to make sure.

---

### Post by markbuntu on 2009-04-06
Sorry, I did not see that. More things that can cause random crashes is an overheating cpu, lose connectors inside or outside the computer, cards not seated properly in their slots, a failing/overloaded power supply, a failing hard drive or motherboard a bad keyboard, mismatched ram (though everyone say this should not happen but it did to me). Since this is effecting all your OSs it is most likely a hardware problem. Check the connections first and then try reseating any cards and take out any mismatched ram so it is all the same.

---


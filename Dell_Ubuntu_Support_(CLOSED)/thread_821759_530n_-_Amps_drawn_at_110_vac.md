---
title: "530n - Amps drawn at 110 vac"
date: 2008-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by javaben on 2008-06-07
My home office is HOT HOT HOT in the summer here in Atlanta GA.

I'm needing to put a window airconditioner in this room, which would be more efficient then making the whole 2nd floor cooler.

This room only has one (1) 15 amp circuit feeding it.  I'm adding up all of the componets' amperages together so I can acertain whether or not I can add the 110vac window unit.  However, I can't find any info on the normal current draw for the 530n, neither on the Dell site, and there aren't any plates on the back of the computer.

Any insight?

JavaBen

---

### Post by niteshifter on 2008-06-07
Hi,

There's usually a rating given in watts on the power supply. For example, I have a Dell PA-10 power unit, it states maximum output as 90W. Power (put simply) is the product of voltage X amperes. So for this unit: 90/120 = 0.75 ampere. This calculation assumes that the power supply is 100% effecient in it's conversion, when actually a typical efficiency is about 95%. So let's crank that in: 0.75 * 0.05 = 0.0375 ampere additional: 0.75 + 0.0375 = 0.79 ampere.

---

### Post by veedub on 2008-06-09
shouldn't be a problem if it is a new air conditioner and you only have one computer.  Even at 550W running maximum output would only draw 5A.  So at absolute peak you would draw approx 4A from the air conditioner, plus 5A(peak) from the PC, plus another 1A from everything else, and maybe another 1A if your lights are on the same circuit would be a total of 11A, providing 4A of breathing room, and that's if everything is running at PEAK power consumption 100% of the time.

It is unlikely that your dell has a 550W power supply.  I just threw that number in for worst case scenario of a PC's power consumption.  Average is about 350W which is 3.18A on a 110V line, and again, that's PEAK, not typical.

---

### Post by gbrainin on 2008-06-10
I would suggest that you get a UPS for the computer before you start up the AC.  While I agree that adding this will probably not overtax your circuit, your computer will appreciate not having the power fluctuations as the AC cycles on and off.

---


---
title: "ubuntu 7.10 installed- ore sound problemsm"
date: 2007-10-16
forum: Dell  Ubuntu Support
---

### Post by igggyc on 2007-10-16
hi all

i'm running an inspiron 1720 notebook with a sigmatel STAC9205 sound card.

i get sound from my laptop speakers, except when i plug in some real speakers using my headphone jack, the laptop speakers continue playing, except i get nothing out of the proper speakers.

many forums have said to change the line in the alsa-base document, which now reads:

options snd-hda-intel model=ref

to

options snd-hda-intel model=stack3

and this has worked for many people, but when in change it, i can't get any sound out of the laptop speakers, but i do get sound when i plug in extneral speakers to my headphone jack.

many sound cards out there have a feature for a headphone sensor which fixes all their problems, mine however does not have that sensor feature.

i've played around with all the settins including those of alsamixer,and i have had no success. please someone give me a solution, i want to end these stupid errors...
__________________

---

### Post by bekirserifoglu on 2007-10-17
I have the same problem with the same soundcard(sigmatel). I have tried everything that is suggested on the forum but no solution. I am planning to switch back to windows till the problem is solved. coz i need to use my headphones all the time. So someone plz help.

---


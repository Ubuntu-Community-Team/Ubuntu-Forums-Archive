---
title: "[Xubuntu] Can't get Beagle to index anything."
date: 2005-11-03
forum: Desktop Environments
---

### Post by norwyn on 2005-11-03
Hi.
I'm using a clean xubuntu-desktop install over the breezy server install.
But I have one problem though. Beagle won't index anything.
Do anyone know why?
I don't know what information you need from me, or how I can obtain it, so please just tell me how, an I'll do it. 

Thank you in advance.

---

### Post by nagilum on 2005-11-03
Last time I tried Beagle it was very slowly with indexing my data, too. This is actually done intentionally by the developers so it will not interfere with your regular work, i.e. slow down your machine too much. But there's a way to force indexing, just set the environment variable BEAGLE_EXERCISE_THE_DOG to 1 and it should start indexing right away.

---

### Post by norwyn on 2005-11-03
Yeah, but I have got it running for a month or so. And it still haven't indexed anything. But anyway how do I set that variable to one?

Thank you for the quick reply!
//norwyn

---

### Post by nagilum on 2005-11-04
Just open a terminal and type:

export BEAGLE_EXERCISE_THE_DOG=1

Afterwards you can start beagle with 'beagled' from the same terminal (the icon launcher from the menu won't work cause the variable is only valid within this terminal). If the deamon is running you can exit the terminal.

---

### Post by norwyn on 2005-11-11
Thank you everyone. 
I had tried the dog exercise, but it didn't work back then, so I had to have something done wrong. But now it works :D !
Thanks again!

---


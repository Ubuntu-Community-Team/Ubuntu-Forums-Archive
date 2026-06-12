---
title: "I can't recover rhythmbox controls"
date: 2012-08-23
forum: Desktop Environments
---

### Post by yardo on 2012-08-23
Hi, I have removed various rhythmbox directorys as superuser to make rhythmbox detect my artbox correctly, but what I have done is not fix the problem but spoil the menu bars of the interface (window menu, play/pause/forward/next controls)

I remember one of the directorys was /usr/share/rhythmbox

How can I recover rhythmbox?

I have tried with apt-get remove --purge rhythmbox

But nothing works, when I reinstall the software I dont have the controls

Any help will be very appreciated

P.D: Sorry for my english, I'm from Spain and not bilingual

---

### Post by Frogs Hair on 2012-08-23
> /usr/share/rhythmbox This directory includes just about everything that makes Rhythmbox function. The only thing I can think of is the following. ```
sudo apt-get install --reinstall rhythmbox
``` 
Be careful when removing items from the root file system and if you are not sure post a question here.

---

### Post by yardo on 2012-08-31
> **Frogs Hair said:**
> This directory includes just about everything that makes Rhythmbox function. The only thing I can think of is the following. ```
sudo apt-get install --reinstall rhythmbox
``` 
Be careful when removing items from the root file system and if you are not sure post a question here.

Thanks Frogs, but the command doesnt work and the problem stills and I dont have the rhythmbox controls, what can I do? I don't want to reinstall ubuntu #-o

---

### Post by Frogs Hair on 2012-08-31
Try this PPA and if it doesn't work I really don't have an answerer other than installing a different media player until you get it figured out. 
[http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html](http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html)

There is VLC, Guayadequ and Banshee to name a few.

---


---
title: "I'm pretty sure I've done something wrong here..."
date: 2007-03-14
forum: Gaming &amp; Leisure
---

### Post by toasterofirony on 2007-03-14
I've just gone through the install and update process for NWN and tried to run it, only to be faced with this error message on typing "./nwn":

mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/absentbabinski/.kde /socket-delphine.
can't create mcop directory

Now, I'm guessing it has something to do with having had KDE installed previously and then removing it (using gnome atm).

Any suggestions?

---

### Post by DoorGunner on 2007-03-14
I think all you have to do is the following. I had similar problem getting kde to start.

sudo chmod 777 ~/.kde
sudo chmod 777 ~/.local

it was just a permission thing when you install K

---

### Post by toasterofirony on 2007-03-14
Thanks for your suggestion, but no dice, it didn't help :(

I'm wondering if just reinstalling KDE might sort it out?

---

### Post by DoorGunner on 2007-03-14
Make sure you check to see that all your hidden files are available in your /home/yourname file

It still be a permission problem. Kde gave me lots of greif that way

---

### Post by toasterofirony on 2007-03-14
Okay, so perhaps I was a little hasty, as it seems to be *working* now.

Hilariously, now the game appears to start, but I can't tell which pass-key it is asking me for in the initial start as no text appears, only the boxes in which to type.

---

### Post by DoorGunner on 2007-03-14
Im not sure what is up with that this but your right..... its a little wonky right now. I have had some what i would classify as minor problems with kde..... if you have multiple partitions ivman doesnt want to work at opening..... however, same system works fine in gnome....

Any ways its still experimental till the official release.... :)

---


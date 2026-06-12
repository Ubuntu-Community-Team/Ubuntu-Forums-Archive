---
title: "[USB &amp; Card-Readers] Problems when copying :\"
date: 2005-10-21
forum: Desktop Environments
---

### Post by victorcete on 2005-10-21
Hello all,

first, sorry about my english, I'll try to explain my problem in the best way :p 

Well, I have installed Ubuntu Breezy some days ago, and I thought everything worked OK, until I tried to copy some mp3 songs to my USB device...

The problem is that, I copy a folder (for example 80MB) and I paste in using Nautilus in my USB folder. It takes around 3 or 4 seconds to copy the entire folder... 

O___O??

I used the command **df -hT** in order to see if the 80MB were ocuppied, and... yes, the space were ocuppied, but I can't access the files, so, that is my problem.

I tried it also with other usb devices (nokia n-gage, pendrive), and I got the same results.

Oh! and also with a card reader, I have the same problem, I tried to copy some data into a MMC Card, and the same as before...

I was thinking it was a problem of the USB's, but now...

Well, I hope someone can give me a solution... I'm really suprised.

Sorry about my ugly english and the long text : P!!

Lot of Thanks !!

---

### Post by victorcete on 2005-10-21
: (

nobody knows how to solve it???

thankssssss

---

### Post by ViGiLnT on 2006-01-15
I'm going to bring this thread back to life, because i'm having this problem too.

When i need to copy something to my pen drive, i always do it within a windows pc im my network, because in ubuntu 5.10 it doesn't really copy anything....

For instance, about a week ago, i copyed a school project to keep working at school to my pen drive, and when i got there, there was nothing on my pendrive...

Anyone has got a clue of what the problem may be ? When copying from the pen to the hd, there's no problem at all...

---

### Post by Eversmann on 2006-02-02
Ok, maybe i'm wront with the explanation, but that's how you have to copy files to pendrive.

When you mount a usb pen, when the files are copied, they are in the cache. Linux doesn't copy anything until you umount the drive (please, correct me if this isn't correct).

The fact is: when you copy files to your usb pen, after that, unmount the drive. You'll see that everything is copied if you remount it.

Hope it helps.

---


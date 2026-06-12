---
title: "&quot;Make&quot; not found!?!"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Michael Steinberg on 2005-11-28
I just upgraded to 5.10 and every time I try to add a program through the Terminal I'm told that the "make" command can't be found. What gives? I didn't have this problem with the earlier releases; am I missing something? I feel like a clone....

Also, I'm unfamiliar with "fakeroot", whoich shows up in the Starter guide for installing Java....

And just when I was feeling like I knew what I was doing....

Michael Steinberg

---

### Post by Hairy_Palms on 2005-11-28
you need to install
sudo apt-get install build-essential
tbh im not entirely sure what fakeroot does either
but its enough to know it works for installing java, never used it anywhere else.

---

### Post by Michael Steinberg on 2005-11-28
Thanks! Works fine now. Of course i had to download fakeroot and install it too to get java up & running. It seems like a mistake to leave these out of 5.10 when make and other basics were installed in 4.10 and 5.04 by default.

Luckily, there are always you people to help me out! I'm grateful, as ever.

Michael Steinberg

---

### Post by Rochvellon on 2005-11-28
[quote=Hairy_Palms]sudo apt-get install build-essential[/quote]Thank you, was getting desperate over here... :mrgreen:

---


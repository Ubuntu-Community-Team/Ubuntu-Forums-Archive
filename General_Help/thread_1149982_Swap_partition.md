---
title: "Swap partition"
date: 2009-05-05
forum: General Help
---

### Post by Manac0re on 2009-05-05
Hi all,

When I installed jaunty, I had a swap partition of 8 gig from Ubuntu 8.10.  I installed Jaunty on ext 4 file system and left my swap partition as swap.  Is there any way of me checking its usage and load from the command line....??

Much obliged and thanks in advance...

-Mana

---

### Post by logos34 on 2009-05-05
command:

> free -m

---

### Post by SentientFluid on 2009-05-05
As a general note, typically you shouldn't need a swap partition larger than the amount of RAM in your ssytem.  And often you may not need that much.  For example, I have 2GB of RAM but my swap is only 1GB.  I find my swap partition is barely touched.

---

### Post by albinootje on 2009-05-05
> **SentientFluid said:**
> For example, I have 2GB of RAM but my swap is only 1GB.  I find my swap partition is barely touched.

For hibernation (or suspend ?) on a laptop you might need more swap space to fit in the things from the used RAM memory I've read somewhere.
The old rule of thumb is to use twice as much swap as you have RAM memory, that isn't always needed, but it's a good start imho.

---

### Post by Keithhed on 2009-05-05
i was using a conky script to monitor swap space, among other things.  i found it to be never used so i reduced the size to 1GB just in case.

---

### Post by logos34 on 2009-05-05
> **albinootje said:**
> For hibernation (or suspend ?) on a laptop you might need more swap space to fit in the things from the used RAM memory I've read somewhere.
The old rule of thumb is to use twice as much swap as you have RAM memory, that isn't always needed, but it's a good start imho.

yeah, 2x ram up to a certain amount, like 768 MB at most. At 1 gb or over 1x is enough, if only to enable hibernation (or maybe a tiny bit over, because sometimes hibernation won't work if it's only 1x, which technically is sufficient).  But at 1 Gb or more, your swap will hardly be touched under average usage.

---

### Post by SentientFluid on 2009-05-05
> **albinootje said:**
> For hibernation (or suspend ?) on a laptop you might need more swap space to fit in the things from the used RAM memory I've read somewhere.
The old rule of thumb is to use twice as much swap as you have RAM memory, that isn't always needed, but it's a good start imho.

Good point about hibernate or suspend.  I never use them so rarely think of them.  You'd need at least as much swap space as you have RAM, and probably a little bit more.

As for doubling the RAM, that was the suggestion when computers didn't have as much RAM as they do now.  I would only suggest that if your RAM is less than 1GB.

---

### Post by Manac0re on 2009-05-05
Thanks guys yeah seems that the swap drive is barely being touched....now i m just curious if u guys have any idea why i m only seeing 3.2 gig ram when i have 4 gig and ubuntu x64 installed... on a dell M2010... i have checked out the bios and it looks like its keeping nearly a gig to it self...

Once again any input would be greatly appreciated..... this was my output from free -m
:P

                                 total           used         free        shared    buffers     cached
Mem:          3232       1   416         1816                 0                 98                720

-/+ buffers/cache:        596       2635

Swap:         7632                0     7632

---

### Post by pastalavista on 2009-05-05
Unless you have dedicated memory on your graphics card, with integrated motherboard graphics, some system memory is reserved exclusively for graphics

---

### Post by HermanAB on 2009-05-05
You could use a swap file instead of a swap partition.  This is *not* slower and it is more efficient space wise.  read 'man swapon' and 'man mkswap' for details.

Example:
swapoff -a

dd if=/dev/zero of=/home/swapfile bs=1024 count=65536
mkswap /home/swapfile

gedit /etc/fstab
Comment out existing swap line and add this:
  # Use a swap file on /home
  /home/swapfile none swap defaults 0 0

mount -a
swapon -a
swapon -s

---

### Post by logos34 on 2009-05-05
> **Manac0re said:**
> i have checked out the bios and it looks like its keeping nearly a gig to it self...

like pastalavista (:P) says, it's the graphics.  (if integrated) Turn down the frame buffer...all you need is like 16-32 mb for average use (Even googleearth runs fine on mine at that level).

> **HermanAB said:**
> You could use a swap file instead of a swap partition.  This is *not* slower and it is more efficient space wise.  read 'man swapon' and 'man mkswap' for details.


there's also a [swap page]("http://www.google.com/url?q=https://help.ubuntu.com/community/SwapFaq&ei=DPEASoylFYrWMNiaseYH&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNG8iLXqP_3bHgWFVVaat2eGU5G4kQ") in the community docs

thinking of converting my own to a swap file...

---

### Post by dcstar on 2009-05-05
> **Manac0re said:**
> Thanks guys yeah seems that the swap drive is barely being touched....now i m just curious if u guys have any idea why i m only seeing 3.2 gig ram when i have 4 gig and ubuntu x64 installed... on a dell M2010


Known issue - search out other posts and see if there is a solution.

---

### Post by logos34 on 2009-05-05
> **dcstar said:**
> Known issue - search out other posts and see if there is a solution.

you mean it's a known issue with that Dell model, or what?  Because the O.P. is using 64-bit ubuntu

---


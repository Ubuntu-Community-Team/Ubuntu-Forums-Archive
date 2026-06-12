---
title: "Do I need a swap partition of 3.2 GB??"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2005-10-17
I've got 1 GB of RAM and a 120 GB hard drive. In my fresh installation of Ubuntu, the installer suggest me a 3.2 GB of swap partition, which I accepted. Isn't it an exaggeration?? Before Breezy Badger I was a happy Fedora Core 4 user and there I've defined to use just 1 GB of swap. And as far as I know, less than 2% of it were used regularly.

Any clue?

---

### Post by wylfing on 2005-10-17
The calculations you see on the net (and used by some installers) for swap size come from an era when RAM was expensive. The user with 512MB of RAM doesn't need a drastically different amount of swap than the user with 1GB of RAM. Something in the 512MB-1GB range is probably going to be plenty.

3.2 GB of swap is too much.

---

### Post by Murgle on 2005-10-17
most of the reccomendations I have seen is that you should have your current amount of ram as swap or possibly twice that if you plan on using alot of memory eating apps.  so you don't need that much swap

---

### Post by Stormy Eyes on 2005-10-17
3.2GB is overkill. The rule of thumb used to be **swap = ram *2**, which you should follow if you have 256MB or less of physical RAM. But if you've got more than 256MB of RAM, then set your swap partition's size to be equal to your amount of RAM.

---

### Post by Marcos.Rufino on 2005-10-17
If 3.2 GB of swap is overkill, I suppose the Ubuntu installer has some issues to solve. Why the heck it suggested that figure?

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=Marcos.Rufino]If 3.2 GB of swap is overkill, I suppose the Ubuntu installer has some issues to solve. Why the heck it suggested that figure?[/QUOTE]

I don't have the installer source handy, but perhaps the installer is programmed to suggest a percentage of available disk, or might still be using outdated rules of thumb from an era when RAM was expensive and the average machine didn't have much of it.

---

### Post by HermanAB on 2005-10-17
The maximum amount of swap that Linux will use is 2GB, so allocating more than that won't help with anything.

---

### Post by Marcos.Rufino on 2005-10-18
Is it safe to rezise this 3.2 GB swap partition to something smaller? I'm thinking about using Gparted to do the job.

---

### Post by Goober on 2005-10-18
Although, apparently, it does work ok if you have a lot of RAM, but don't have a Swap.  I don't have a Swap partition, just never knew about it until after I installed Breezy, alongside Hoary, and things run smooth.  Or maybe it automatically created one . . .

---

### Post by migueljacq on 2005-10-18
[QUOTE=Goober]Although, apparently, it does work ok if you have a lot of RAM, but don't have a Swap.  I don't have a Swap partition, just never knew about it until after I installed Breezy, alongside Hoary, and things run smooth.  Or maybe it automatically created one . . .[/QUOTE]

Your resources in the System Monitor will tell you if it did

---


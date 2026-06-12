---
title: "RAM upgrade causing issues - uncompression error, system halted"
date: 2011-11-22
forum: Desktop Environments
---

### Post by mortuk on 2011-11-22
So first off I have a Gigabyte GA-P35C-DS3R motherboard, with 4gb of Corsair (2 x 2gb) XMS2 DDR2 800MHz RAM

Needed at least 8, so checked the motherboard specs and it allows up to 8gb for DDR2. Brought new RAM, (brought 16gb (8x2gb, this is for 2 machines, then was going to move the current 4gb to another machine).

Anyways long story short I cant get the machine working with anything but 4gb. Either it wont even POST, or I get past GRUB and it tells me 'uncompression error, system halted', or it will just infinitely (left it for 45 minutes) sit and blink with the cursor top left (and in recovery mode it gets up to 'freeing initrd memory').

As I brought RAM for another machine I have lots spare to try, and its all matched. I suspect one set is dud as thats the one when it wont even post. I have tried various sets in various slots, and it all comes down to it works with 4gb (any set, except the suspected dud), but I cant get it working with 8gb (however it does POST)

Any ideas? Pulling my hair out! :P

---

### Post by mortuk on 2011-11-23
anyone? seems very odd that it posts but wont boot into ubuntu and all I have done is added more RAM

I take the extra RAM out and it works again

---

### Post by Jonathan.Dufte on 2011-11-23
This sounds very much like you have a 32-bit Linux installed. Am I right? As far as I remember 32-bit Os only support up to 4 GB. If you want more you need to install a 64-bit OS.

---

### Post by LinuxFan999 on 2011-11-23
> **Jonathan.Dufte said:**
> This sounds very much like you have a 32-bit Linux installed. Am I right? As far as I remember 32-bit Os only support up to 4 GB. If you want more you need to install a 64-bit OS.
Maybe, but 32 bit Linux should be able to boot with more than 4GB of RAM, It just wont see the extra memory. Maybe the user who started this thread is dealing with bad RAM.

---

### Post by mortuk on 2011-11-25
> **Jonathan.Dufte said:**
> This sounds very much like you have a 32-bit Linux installed. Am I right? As far as I remember 32-bit Os only support up to 4 GB. If you want more you need to install a 64-bit OS.

Nope, definitely x86_64

> **LinuxFan999 said:**
> Maybe, but 32 bit Linux should be able to boot with more than 4GB of RAM, It just wont see the extra memory. Maybe the user who started this thread is dealing with bad RAM.

And I have 8 identical 2gb sticks, plus the 2 x 2gb sticks I had previously. I have one set that is definitely bad as wont post at all, the rest should be fine. Also tried all combinations of various sets in various slots / on their own, etc

The fact that it posts but wont boot past GRUB is very strange. I 
have the same problem booting from a new live cd as well. Properly stuck :(

---


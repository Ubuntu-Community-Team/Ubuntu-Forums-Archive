---
title: "[SOLVED] I need help my.. X current intrepid failed, and I messed up Formating Need H"
date: 2009-01-07
forum: General Help
---

### Post by madmilk on 2009-01-07
Well I had installed earlier today Ubuntu 8.10 (Dual boot, with my Windows XP), but all the sudden in a couple of Commands I messed up a couple of things of the Ubuntu, non of my themes were working, I also lost allot applications (folders appeared moved around) .. lets just say I messed it up big time  

*Dumb Noob Things*

Okay well decided to Re-install Ubuntu 8.10

I used the same CD I used to install it...  Ran the Live CD, at Live Desktop.. chose Install

At partitioning area I chose *manual*

Here is  where i know I skrewed up big time

I decided to Format First the SWAP :/  (then chose on it to be Swap) ...  then Formatted the *partition on where i had the old Ubuntu on... (chose ext3  / )

And well continued for it. to make the Installation ...  did my member name and etc...    

When it started running the installation ... for some reason, errors ocurred (files not being the same as the source from Cd)  I kept trying clicking to Retry ...  but well ..  it simply it could not continue.. as faulty CD

That is totally messed up... when its NEW and it was teh same CD I used a few hours earlier.

Well   RESTARTED ... (decided to take out CD)
buuuu   GRUB  won't start  (Duhh i forgot *I marked to format it .. crap)


Any Way for me to Repair my old GRUB (from earlier today) ..  so that I can be able again to access my Dual Boot.. BACK into my Windows XP?? 

I need to  Burn again a new CD (Ubuntu 8.10) so that i can re fix my HD ubuntu install


WTE ..  I'm so lost here.. I need HELP URGENT!

***I'm currently running through Live CD to ask for help on the Forum***

---

### Post by madmilk on 2009-01-07
help....

---

### Post by nothingspecial on 2009-01-07
I`m not quite sure I understand entirely what you`ve done.

Do you still have xp or have you nuked it?

If you have formatted your entire drive it should just be a matter of installing and using the option "guided use entire disk". 

If you still have windows and or important data use the live disk to back them up to an external device. Then use gparted (it`s in the menus on the live disk somewhere, it`s called partition editor or something like that) to identify where windows is (make sure you do this right)and install ubuntu on the other part of your disk.

---

### Post by madmilk on 2009-01-07
I Got back WINDOWS!!!  =)

This Command..  Erases the old GRUB in BOOT..  and   Re installs your Original  Windows  Boot


sudo lilo -M /dev/sda mbr


Now I hope...  the New Copy .. gets me to Re-Fix... my  Ubuntu & Swap partition .. to  Put back up Ubuntu 8.10

CROSSING MY FINGER lol

---

### Post by madmilk on 2009-01-07
I messed up my Old's Ubuntu *GRUB*

I mistakenly  Formatted the **SWAP**  partition (in other words killed GRUB)

Anyways ...  now  I'm gonna re burn a new  Ubuntu 8.10 Live CD.. since  it appears the one i used earlier today.. Currupted or something (Really weird its entirely new, and did install it perfectly before)

Well alleluya I found this command: sudo lilo -M /dev/sda mbr

It got me back into.. Booting my Original Windows *Boot* ...

I hope now I could be abel to Fix my *Old Ubutnu partition & Swap ...  for Re-installing of ubuntu 8.10

> **nothingspecial said:**
> I`m not quite sure I understand entirely what you`ve done.

Do you still have xp or have you nuked it?

If you have formatted your entire drive it should just be a matter of installing and using the option "guided use entire disk". 

If you still have windows and or important data use the live disk to back them up to an external device. Then use gparted (it`s in the menus on the live disk somewhere, it`s called partition editor or something like that) to identify where windows is (make sure you do this right)and install ubuntu on the other part of your disk.

---

### Post by nothingspecial on 2009-01-07
I would still suggest backing everything up before you make major changes to your system. I learnt the hard way (see my sig).

When you install, if your not sure what youre doing use the "guided - use largest available free space" option. Make sure you`ve got this right before going ahead. I believe it is advised to defrag windows before you install.

I`ll never forget a post about a year ago that went something along the lines of -

"Help, I think I`ve just removed windows from my dad`s pc, it had all his work on it"

---

### Post by madmilk on 2009-01-07
Thanx  ..  anyways  I do know how to work with partitions inside Windows   .. it was simply  *Format all the Partitions (You used with Ubuntu & Swap) and set them as Un-allocated*

Afterwards Restart the Computer, with the LiveCD ...  choose  Gparted  ...   and then in that area  *EXPAND* your Current Windows Partition .. Completely  .. and choose to Apply

After that ...  you normal  choose  Install in the LiveCD, and Re Install like the Normal Process of First Time Installing Ubuntu.

*That thing i did in Gparted puts your Hard Drive exactly how it was originally, before ever installing or making any Partitions Before Adding Ubuntu or any other OS*


=)  thanx Anyways


> **nothingspecial said:**
> I would still suggest backing everything up before you make major changes to your system. I learnt the hard way (see my sig).

When you install, if your not sure what youre doing use the "guided - use largest available free space" option. Make sure you`ve got this right before going ahead. I believe it is advised to defrag windows before you install.

I`ll never forget a post about a year ago that went something along the lines of -

"Help, I think I`ve just removed windows from my dad`s pc, it had all his work on it"

---


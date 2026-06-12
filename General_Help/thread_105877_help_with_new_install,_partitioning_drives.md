---
title: "help with new install, partitioning drives"
date: 2005-12-19
forum: General Help
---

### Post by Age One on 2005-12-19
Hi.

I'm getting ready to install Ubuntu onto my computer (waiting for my Shipit disk). I have installed and run linux before (SuSE 9.1/FC3/SuSE 9.3) this will be my first time with ubuntu, and also my first time installing on a diffrent HDD then XP. in the past I have installed xp and suse on the same HDD (200 GB) with no problems. I am going to do something diffrent this time..

what I have, a 80gb HDD as master with XP installed on it, it is imperative I not lose the info on this drive. what I want to do is add my 200GB as a slave drive with ubuntu installed here.

my question. where do I install the boot loader? on hda or hdb, will the install program for ubuntu specify a location or do it automaticly? is there anything else I should be aware of when doing this? 

thanks.
-Adrian

---

### Post by tlc on 2005-12-19
Ubuntu will install the boot loader for you. Your XP installation should be automagically picked up.

edit: obviously, tell Ubuntu to install itself on the 200GB drive... :p

---

### Post by maglis on 2005-12-19
> **Age One] what I want to do is add my 200GB as a slave drive with ubuntu installed here.
[/quote] Just make sure it is really connected to your motherboard as a "slave drive" said:**
> 
my question. where do I install the boot loader? on hda or hdb, will the install program for ubuntu specify a location or do it automaticly? is there anything else I should be aware of when doing this? 
 
Install boot loader in Master Boot Record (MBR, default choice in Ubuntu), unless you choose an "expert" installation mode, which you don't need to. Simply, when the question pops up on where do you want ubuntu to be installed choose the correct disk ;)

---

### Post by Age One on 2005-12-19
I have the jumpers on cable select, should I have them specify there location?

---

### Post by maglis on 2005-12-19
No, not necessarily. So long as it is at the correct end of the cable...

If not sure, better pick slave jumper position.

---


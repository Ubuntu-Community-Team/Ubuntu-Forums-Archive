---
title: "will reparing xp mess up my dual boot?"
date: 2009-06-06
forum: General Help
---

### Post by Bigneil on 2009-06-06
I'm having trouble with my XP, i think i need to do a repair on it. But will this destroy my grub loader?   .... last time i tried to fix grub i gave up and did a clean install, i am keen to avoid this.

---

### Post by iponeverything on 2009-06-06
Yes, more than likely the "repair" will nuke grub from the boot sector.

Reinstalling grub in the boot sector -- it is a pain - but is doable by about anyone with moderate skill level.

google around for "reinstall grub"

I would boot from original install disk, choosing the option that looks something like "boot primary linux partition" and then run the "grub-install" program.. 

I have not tried this, but I seems like it should work. Last time I had to do this for someone, it took me about 15 minutes to figure it out..

---

### Post by Bigneil on 2009-06-06
> **iponeverything said:**
> Yes, more than likely the "repair" will nuke grub from the boot sector.

Reinstalling grub in the boot sector -- it is a pain - but is doable by about anyone with moderate skill level.

google around for "reinstall grub"

I would boot from original install disk, choosing the option that looks something like "boot primary linux partition" and then run the "grub-install" program.. 

I have not tried this, but I seems like it should work. Last time I had to do this for someone, it took me about 15 minutes to figure it out..

So, if i have to fix grub, i can do this from the Ubuntu live cd.  does it work with all versions of ubuntu and all versions of the live cd?

---

### Post by iponeverything on 2009-06-06
> So, if i have to fix grub, i can do this from the Ubuntu live cd. does it work with all versions of ubuntu and all versions of the live cd?


My guess would be yes. Though I can only vouch for Desktop and Server CD's  -- I would avoid going as far back as feisty, there may have some changes in grub since then.

---

### Post by Bigneil on 2009-06-06
> **iponeverything said:**
> My guess would be yes. Though I can only vouch for Desktop and Server CD's  -- I would avoid going as far back as feisty, there may have some changes in grub since then.

thanks for your help. i have hardy disk i can use. :)

---


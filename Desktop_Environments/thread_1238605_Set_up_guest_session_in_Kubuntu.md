---
title: "Set up guest session in Kubuntu?"
date: 2009-08-12
forum: Desktop Environments
---

### Post by Raboch on 2009-08-12
Hey all, is there any way to set up Kubuntu to have a guest session like in Ubuntu? That's the one feature in Ubuntu that I really miss. I know that this is listed in [KubuntuUbuntuFeatureParity]("https://wiki.kubuntu.org/Kubuntu/UbuntuFeatureParity") on the Kubuntu wiki, but can't there be a workaround to get this functionality earlier?

Any thoughts?

---

### Post by krazyd on 2009-08-12
You can use the KUser program to administer users/groups.

I haven't set up a guest account myself, but you can create a new user called 'guest' and then go to System Settings > Advanced tab > Login Manager > Convenience tab and enable passwordless login for 'guest'.

Is that the effect you were after?

---

### Post by Raboch on 2009-08-13
Yeah, it gets the job done, thanks.

---

### Post by Mad_Dud on 2009-08-30
Doesn't the guest account have some special (restrict) permission settings?

---

### Post by krazyd on 2009-08-31
Well, unless the guest knows the root password, they can only edit /home/guest/*

---


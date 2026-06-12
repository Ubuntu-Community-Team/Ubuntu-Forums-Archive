---
title: "Single-sign-on how-to?"
date: 2007-06-06
forum: Desktop Environments
---

### Post by noevilclowns on 2007-06-06
Hi all,

I have done a bit of searching, but I cannot find if it is possible to get single-sign-on (SSO) or some form of SSO working in 7.04.  Afaict, Evolution and Gaim do not use gnome-keyring to store passwords.  Is this correct?  If so, is there some package I need to enable this?  Or is this a compile-time option?  Also, is there a way to get gdm to unlock gnome-keyring?

Any assistance would be much appreciated.

---

### Post by hillbilly on 2007-06-06
I don't use Evolution, but for Gaim, there is an option in the Account Information to remember passwords. That should do for you I believe

---

### Post by noevilclowns on 2007-06-13
> **hillbilly said:**
> I don't use Evolution, but for Gaim, there is an option in the Account Information to remember passwords. That should do for you I believe

Thanks for the reply, Hillbilly.  I know I can save passwords with both Gaim and Evolution, but I also know that both these programs used to use their own method of storing passwords.  Neither of them was particularly secure.  

When I look in gnome-keyring-manager there are no saved passwords, and I have checked the "Save this password" box in both Gaim and Evolution.  Therefore, I have to conclude that they are not using GNOME Keyring.  I haven't found any packages that enable this either, but maybe I'm not looking in the right place (or with the right name).

Anyway, thanks again for the reply.  Anyone else have any ideas?

---


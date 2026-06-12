---
title: "Is it possible to have 2 versions of wine?"
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by blazercist on 2007-05-29
I'd like to know if its possible to have 2 different versions of wine each with its own winecfg and fake "c drive" totally seperate from one another... I would change the name of the wine binaries to reflect the versions...  thanks.

---

### Post by AndrewRiedi on 2007-05-29
If you compile Wine from source you can run it like so:  **~/wine-git/wine** without the need to install it.  Also look into **WINEPREFIX**.  (Maybe **man wine** ?)

---

### Post by blazercist on 2007-05-30
I'm not understanding the git-wine thing?  I can run the new binary without installing, but that doesn't solve my problem of having two different winecfg's and two fake c drives.

---

### Post by derouge on 2007-06-07
I'm also interested in this. Figured I'd bump it as opposed to posting a new topic. Reason being, I have one program that only works with an older version of WINE. However, I'd also like to have the newer version on hand since, I'm assuming, it's more up to date and will work better in most cases.

---

### Post by AndrewRiedi on 2007-06-08
> **blazercist said:**
> I'm not understanding the git-wine thing?  I can run the new binary without installing, but that doesn't solve my problem of having two different winecfg's and two fake c drives.

You read about WINEPREFIX?  It will create another fake windows for you.  A new config and everything.

---

### Post by AndrewRiedi on 2007-06-08
> **derouge said:**
> I'm also interested in this. Figured I'd bump it as opposed to posting a new topic. Reason being, I have one program that only works with an older version of WINE. However, I'd also like to have the newer version on hand since, I'm assuming, it's more up to date and will work better in most cases.

Do you know how to compile Wine?

---

### Post by derouge on 2007-06-08
Yes. I'll take a look at WINEPREFIX. Thanks. :)

---


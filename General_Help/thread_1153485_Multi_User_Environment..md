---
title: "Multi_User Environment."
date: 2009-05-08
forum: General Help
---

### Post by Wiebelhaus on 2009-05-08
I'm about to set up Ubuntu for a family in a multi user environment , I've never used nor setup any Desktop Linux Distribution in such a way , Is there anything from your experience that I need to prepare for? Or any special setup? Does Ubuntu fair well in a Multi user desktop environment?

Thanks for any suggestions or help or advice you may offer.

Cheers!

---

### Post by CatKiller on 2009-05-08
> **sx66gns said:**
> Does Ubuntu fair well in a Multi user desktop environment?

Yes. It's what it was designed for.

Create an account for each user, and each user gets his or her own individual settings & storage and doesn't need to affect any other user in any way. Things that affect other users require root access, which is done through sudo and is available to users who are in the admin group. This is the user that was created when Ubuntu was installed and any others that you've decided should have administrative privileges.

The only thing to watch out for is that, unless it's been changed in recent versions, Home folders are readable by everyone by default when they are created. It's easy enough to change, though.

---

### Post by Wiebelhaus on 2009-05-08
> **CatKiller said:**
> Yes. It's what it was designed for.

Create an account for each user, and each user gets his or her own individual settings & storage and doesn't need to affect any other user in any way. Things that affect other users require root access, which is done through sudo and is available to users who are in the admin group. This is the user that was created when Ubuntu was installed and any others that you've decided should have administrative privileges.

The only thing to watch out for is that, unless it's been changed in recent versions, Home folders are readable by everyone by default when they are created. It's easy enough to change, though.

Thanks mate , that's the information I was looking for.

---


---
title: "how to check all packages in time?"
date: 2009-05-16
forum: General Help
---

### Post by nikolko on 2009-05-16
Hi,

just made an error and suddenly executed 

sudo rm -rf /usr/lib/

and noticed it couple seconds after... so, some libraries were deleted. How can I force APT to check the existence of all the files from installed packages and to fix them???

---

### Post by kpkeerthi on 2009-05-16
Do you have a backup?

---

### Post by nikolko on 2009-05-16
> **kpkeerthi said:**
> Do you have a backup?

I'm afraid I never did a backup of /usr/lib/ directory, as it is not very important data...

---

### Post by nikolko on 2009-05-16
hmm... I decided to re-install ubuntu on top of previous version, now it looks fine, but some soft was removed...

---

### Post by kpkeerthi on 2009-05-17
> **nikolko said:**
> hmm... I decided to re-install ubuntu on top of previous version, now it looks fine, but some soft was removed...

If you reinstall on top of previous version it does not do an upgrade.

---

### Post by dcstar on 2009-05-17
> **nikolko said:**
> I'm afraid I never did a backup of /usr/lib/ directory, as it is not very important data...

You should **never** touch any system folder, /usr is a system folder **not** a user folder.

---


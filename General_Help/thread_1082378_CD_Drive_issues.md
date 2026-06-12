---
title: "CD Drive issues"
date: 2009-02-27
forum: General Help
---

### Post by fluffybacon on 2009-02-27
Hi Guys,

Not sure how to go about fixing this, but changing CDs in the drive isn't being updated in gnome.  I can still mount new CDs manually.  I suspect that it may be an issue with hal, but I'm not sure where I should be checking, any ideas?

Thanks.

---

### Post by Tamlynmac on 2009-02-27
You might check your Gnome Configuration Editor to sure your automounting your media..

apps/nautilus/preferences

Make sure the "media_automount" & "media_automount open"
Are both checked.

---

### Post by fluffybacon on 2009-02-27
> 
Make sure the "media_automount" & "media_automount open"
Are both checked.


Hi Tamlynmac, yes on both counts I'm afraid.

---

### Post by dcstar on 2009-02-28
> **fluffybacon said:**
> Hi Guys,

Not sure how to go about fixing this, but changing CDs in the drive isn't being updated in gnome.  I can still mount new CDs manually.  I suspect that it may be an issue with hal, but I'm not sure where I should be checking, any ideas?

Thanks.

Nautilus-Edit-Preferences-Media

Also post contents of /etc/fstab.

---


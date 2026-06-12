---
title: "Hibernate works for one user but not for the other..."
date: 2009-04-10
forum: General Help
---

### Post by wookie81179 on 2009-04-10
Hello and good Morning,

I guess I've run into something of a dead end here.

When I log in with my standard username and password the gnome-power-manager only offers me "standby" as a power saving feature. But as soon as I log in with an alternate username it also offers me hibernate.

Any suggestions what i might have screwed up in my own settings? And how to reset it to standard?

Thanks everyone.
Bye.

---

### Post by PurposeOfReason on 2009-04-10
Are both users in the 'power' group?

---

### Post by wookie81179 on 2009-04-10
Nevermind. I found it.
Somehow for my main user the "can hibernate" has been unflaged in gnome-power-manager/general.
I only had to re-set this flag with gconf-editor and now it works fine again... NARF.

I love LINUX. It drives me crazy, but I love it.

---


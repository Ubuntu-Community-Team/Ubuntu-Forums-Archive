---
title: "Permissions Problems"
date: 2009-06-13
forum: General Help
---

### Post by regnumimbrium on 2009-06-13
Hey Everyone,

I really screwed up my installation (especially MySQL) by running the following command:

sudo chown -R main:root /var

Is there anyway to undo this mistake, short of reinstalling the whole distro or each affected program?

Any help would be tremendously appreciated.

---

### Post by jonobr on 2009-06-13
Hello


Im thinking the only thing you could possibly do is to reinstall packages/application that are messed up, for example 
/var/www <- all your web apache stuff..
This will loose config files though.......

However Im the type of person that thinks if I dont restore things to the way they were, If I run into an issue, I will always think that this was cuased by this problem, even though it may not...

---


---
title: "Purge and Purge*"
date: 2009-02-22
forum: General Help
---

### Post by RedSingularity on 2009-02-22
What is the difference between "apt-get purge application" and "apt-get purge application*"

---

### Post by mcduck on 2009-02-22
the "*" is a wildcard, meaning that it can be replaced with any number of any characters.

So, "apt-get purge application" would purge a package called "application".

"apt-get purge application*" would purge all packages that have a name starting with "application".

---

### Post by RedSingularity on 2009-02-22
Perfect thats exactly what i wanted.  THANKS!!!  :)

---


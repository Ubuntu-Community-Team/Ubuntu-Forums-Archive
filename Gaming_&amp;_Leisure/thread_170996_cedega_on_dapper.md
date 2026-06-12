---
title: "cedega on dapper"
date: 2006-05-05
forum: Gaming &amp; Leisure
---

### Post by bunnieofdoom on 2006-05-05
im haveing an install problem with cedega on dapper :(

 Package xlibs is not installed.

but its not in the repositories i also have xlibs-dev install to latest version

---

### Post by Sef on 2006-05-05
Try this: 

Applications > Accessories > Terminal

sudo apt-get update

sudo apt-get install xlibs-dev

See if that works for you.

---

### Post by bunnieofdoom on 2006-05-05
it didn't work but i got it fixed i pulled xlibs from breazy repos

---


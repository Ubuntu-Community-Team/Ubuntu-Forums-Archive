---
title: "trying to preform setenv, no command ?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by zeltak on 2006-02-16
hi 

im trying to install the new mythTV with hyams amazing guide. in the middle it says to input:

setenv QTDIR /usr/lib/qt3

but i get an error message saying there is no such command... can anyone tell me what im doing wrong?

thx alot

Zeltak

---

### Post by wrtrdood on 2006-02-16
Different shell.  For Bash, try:

*export QTDIR=/usr/lib/qt3*

---


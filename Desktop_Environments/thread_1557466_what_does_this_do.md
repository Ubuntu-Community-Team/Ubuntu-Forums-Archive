---
title: "what does this do"
date: 2010-08-20
forum: Desktop Environments
---

### Post by hungerformore on 2010-08-20
what does the following bash script do? ls -R | grep ": $" | sed -e 's/:$//' -e 's[^-][^\/]*\/ / --/ g ' -e ' s /^/ /'-e's/-/|/'

---

### Post by stoimeno on 2010-08-23
ls -R | grep ':$' | sed -e 's/:$//' -e 's/[^-][^\/]*\/ /--/g' -e 's/^/ /' -e 's/-/|/'
lists all non-hidden subdirectories (except that it replaces the 1st - by |)
a better way:
find . -type d -name '[^.]*' -print | grep -v '[\/][.]'

---


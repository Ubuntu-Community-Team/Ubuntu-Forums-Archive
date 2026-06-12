---
title: "search a directory and all sub directories and"
date: 2009-05-03
forum: General Help
---

### Post by Primefalcon on 2009-05-03
This is what I need to do

I need to search a directory (specifically my /var/www directory) and all sub directories for matching text (base64_decode) and delete the first line in said files

the command I'm thinking of using is
sed '1d' $(grep -liR base64_decode /var/www/)

however I'm not sure if this would work and am asking for input from this great community before I possibly make a big mistake (I'm not familiar with the sed command)

---

### Post by Primefalcon on 2009-05-03
I figure someone here has to be familiar with sed

---

### Post by unutbu on 2009-05-03
It would be wise to test this on a copy of /var/www before putting it to work:

```
find . -type f -exec grep -l base64_decode {} \; | while read file; do  echo "$file"; sed -i '1d' "$file"; done
```

---

### Post by Primefalcon on 2009-05-03
Will do and thank you very much

---

### Post by mysoogal on 2009-05-03
> **Primefalcon said:**
> Will do and thank you very much

it all looks so confusing why don't you use a simple method the search function has the same things you after

[IMG]http://i44.tinypic.com/ok73gw.png[/IMG]

---

### Post by Primefalcon on 2009-05-03
simple, because I have a few hundred thousound files... and I'd prefer not to have to edit them manually

---

### Post by Primefalcon on 2009-05-03
Btw unutbu that worked a treat, Thx :-D

---

### Post by unutbu on 2009-05-03
Glad I could help.

---


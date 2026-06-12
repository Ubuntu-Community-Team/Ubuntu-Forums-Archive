---
title: "symbolic link   ln -s"
date: 2009-03-04
forum: General Help
---

### Post by lex1 on 2009-03-04
I have a package elforn in /var/lib/elforn

I need to create a syslink to [www.mydomain/modified/elforn](www.mydomain/modified/elforn)

IN var/lib/elforn i did a ln -s elforn.html index.html as user
elforn

in /var/www i did as root ln -s /var/lib/elforn/results elforn

my question

since the eflorn.html file is in a directory called 'modified'(web page is [www.mydomain/modified/eforn)is](www.mydomain/modified/eforn)is)
in /var/www and the index.html is in /var/www but not in the 'modified'directory are the above syslinks correct?

lex1:popcorn:

---


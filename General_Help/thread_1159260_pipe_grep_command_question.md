---
title: "pipe grep command question"
date: 2009-05-14
forum: General Help
---

### Post by epro66 on 2009-05-14
Hi all,
I applogise if I am not using a corect forum for this, but I couldn't find any that would
fit more.
Can someone help me with the following problem.
I am executing the following command:
(search for occurences of 'error' in files that match cl-*.log expression)
> grep -cw -i --max-count=1 'error' cl-*.log  
this command outputs:
cl-apache.log:1
cl-apache_error.log:1
cl-apache_warn.log:1
cl-apache_2009_05_13.log:1

Than I want to filter the results from this command and exclude lines
that are matching some user entered wildcard (lets say: exclude files
from the result that match 'cf-*err*'). So I tried the following command:
> grep -cw -i --max-count=1 'error' cl-*.log  |  grep -v 'cf-*err*'

I was expecting that the second command (grep -v 'cf-*err*') will 
filter the first command OUTPUT, but instead, it saerch 'cf-*err*' 
WITHIN each file Content, instead of fcommand output.

Any help is appretiated,
Thx

---

### Post by Locutus_of_Borg on 2009-05-14
maybe there's a better way, but you could do this:

grep -cw -i --max-count=1 'error' cl-*.log >> /tmp/temp.file && grep -v 'cf-*err* /tmp/temp.file && rm /tmp/temp.file

---

### Post by epro66 on 2009-05-14
Thank for the quick reply. 
I am still searching for more "elegant" solution(dont know if ther is one),  but If I 
dont find any soon, I will need to use what you suggested

---


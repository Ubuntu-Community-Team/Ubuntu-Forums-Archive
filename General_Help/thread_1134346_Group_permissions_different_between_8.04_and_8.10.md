---
title: "Group permissions different between 8.04 and 8.10?"
date: 2009-04-23
forum: General Help
---

### Post by qwertybyrd on 2009-04-23
There seems to be a difference in the way 8.10 handles group permissions with respect to 8.04.

In 8.04, user foo is member of foo and bar. Group foo is the primary group. if a directory is owned by root:bar, with permissions of 770, foo can cd into the directory and create a file.

In 8.10, trying to cd into the directory results in 'access denied'. If he does a newgrp bar, he is then able to cd and create the file.

Is this new behaviour, a new configuration setting, or a bug? Is there any way to return to the original behaviour?

Thanks in advance

markus

---


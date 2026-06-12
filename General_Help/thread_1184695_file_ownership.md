---
title: "file ownership"
date: 2009-06-11
forum: General Help
---

### Post by lex1 on 2009-06-11
at the moment I have a file with this ownership
www-data www-data

it needs to be
www-data root

what is the command to change this?

lwx11;)

---

### Post by indytim on 2009-06-11
```

$ man chown

```

---

### Post by ibuclaw on 2009-06-11
Two commands you could use are **chown** or **chgrp**

chown lets you able to change both owner and group permissions
```
sudo chown www-data:root filename.txt
```

chgrp just allows you to change the group.
```
sudo chgrp root filename.txt
```

Since you are changing the group to a user that is not yourself, you are required to use **sudo** in order to acquire the right privileges to change the group permission of the file.

Regards
Iain

---


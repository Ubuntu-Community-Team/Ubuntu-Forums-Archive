---
title: "Change user name"
date: 2009-02-01
forum: General Help
---

### Post by charleykay on 2009-02-01
I have a Wubi installation of 8.10 and I would like to change the user name I chose during installation. I have tried System => Adiministration => Users and Groups and selecting my Account then clicking Unlock. This allows me to change Real name and Home directory but Username is greyed out so I can not change it. Any help would be appreciated thanks.

---

### Post by brandon88tube on 2009-02-01
You could create a new account with the same privileges then sign onto that account and delete the old one.

---

### Post by charleykay on 2009-02-02
Thanks for the suggestion sounds like a good idea. I'd still like to know how to change the user name if anyone can help please.

---

### Post by gettinoriginal on 2009-02-02
Don't know about wubi, and I don't know if this is editable, but you can try this.  But when my grub splash comes up, I hit escape, select root prompt, and enter this:

```
grep 1000 /etc/passwd
```
should give you the username -eg
**username**:x:1000:1000:**username**,,,:/home/**username**:/bin/bash

---

### Post by brandon88tube on 2009-02-02
I've found your answer. Go here [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235) and scroll down to the 2nd and 3rd posts.

---

### Post by charleykay on 2009-02-02
> **brandon88tube said:**
> I've found your answer. Go here [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235) and scroll down to the 2nd and 3rd posts.

Thanks, looks like that has done the trick.

---


---
title: "cannot change default program to open file [Resolved]"
date: 2006-12-06
forum: Desktop Environments
---

### Post by cyber_bushi on 2006-12-06
Hi all,

since I'm using Edgy I cannot change the default program to use to open a file type like I used to in nautilus. I used Properties\open with and chose the program. But now I cannot activate another option box. As root I can but doesn't change anything for me then. Did anyone experience this? Is there maybe a file where I can change this manually? I can btw give and remove permissions on the file, since I'm the owner of the dir and files...

Please help,

regards,

cb

---

### Post by aysiu on 2006-12-06
Sounds as if you lost control over parts of your home directory. Type this command into the terminal (substituting in your actual username for *username*) and see if it makes a difference: ```
sudo chown -R *username:username* /home/*username*
```

---

### Post by cyber_bushi on 2006-12-06
Yep, that's what it was! Thank you so much! Struggled around with this for quite some times and noone could/would help me in some other forums.
Thanks a lot!
cb

---


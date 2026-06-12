---
title: "Boot Error"
date: 2005-12-18
forum: Desktop Environments
---

### Post by gman2004 on 2005-12-18
When I log to my computer I get this message:
"Your $home/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."
Can you explain this to me? It seems that everything works fine to me!

---

### Post by Koybe on 2005-12-18
Try to do :
```
ls -l ~/.dmrc
```
The permission should be "rw- r-- r--"
and owned by you "user user"

> ls -l ~/.dmrc
> -rw-r--r--  1 jerome jerome 45 d&#233;c 18 10:17 .dmrc

If not juste change it too :
```
chmod 644 ~/.dmrc
chown user. ~/.dmrc
```

---

### Post by gman2004 on 2005-12-18
I did check and made the changes but I get the same error!

---

### Post by doitashimashite on 2005-12-18
But what do you see when you enter:

ls -l ~/.dmrc

---

### Post by gman2004 on 2005-12-18
This is what I see:
-rw-r--r--  1 user user 26 2005-10-12 00:10 /home/user/.dmrc

---

### Post by Koybe on 2005-12-18
[QUOTE=gman2004]This is what I see:
-rw-r--r--  1 user user 26 2005-10-12 00:10 /home/user/.dmrc[/QUOTE]


I told you *user* as an exemple you should put your login. ;)

So restart this command :

```
chown *yourlogin*. ~/.dmrc
```

---

### Post by gman2004 on 2005-12-18
I used "user" as an example, I did use my userID

---

### Post by Koybe on 2005-12-19
Sorry... misunderstood ;)

Anyway if you have write access to the file it should be ok. If you want you can try removing (or moving) it and restart gdm to see what happend. It should reconstruct the file.

No more idea ;)

---

### Post by bszmyd on 2005-12-19
I also am having the same problem error, though it only seems to prevent me from saving my desktop configuration. I saw on another forum that the .dmrc file will also be rejected if other users have write permissions to your user directory...this doesn't seem to be the case with my setup either, but could be with yours.

I'll keep you posted...

---

### Post by gman2004 on 2006-02-19
[QUOTE=Koybe]Sorry... misunderstood ;)

Anyway if you have write access to the file it should be ok. If you want you can try removing (or moving) it and restart gdm to see what happend. It should reconstruct the file.

No more idea ;)[/QUOTE]
Sorry for not responding to you reply earlier but I was ignoring the problem, I was so busy!
Any how, the error is not gone, it is still there but I don't understand what do you mean by "try removing (or moving) it and restart gdm". Can you please make it more clear.

Thank you.

---


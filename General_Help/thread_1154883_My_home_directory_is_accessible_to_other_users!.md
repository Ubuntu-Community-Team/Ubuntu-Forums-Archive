---
title: "My home directory is accessible to other users?!"
date: 2009-05-10
forum: General Help
---

### Post by doncristobal on 2009-05-10
It's probably a stupid question, but why the hell is my home directory (/home/[username]) read/execute-accessible for all users?! (drwxr-xr-x)
This means concretely that the guest account can open everything there - is this the normal behaviour? Or have I messed up something without realising? Some sub-directories are only readable for myself (drwx------), but it's rather the exception than the rule. 

Is it a good idea to "chmod 700" my home directory? With or without the --recursive option?

---

### Post by spiderbatdad on 2009-05-10
yes you can change the permissions to 700, by default they are 755. I wouldn't use -R as first choice but rather chmod 700 /home/username

---

### Post by doncristobal on 2009-05-10
I did "chmod 700 /home/[username]". Now it seems to behave as I expected. I'll post again if trouble arises :-)
By the way: Much better data protection can be obtained by encryption: [https://help.ubuntu.com/community/EncryptedPrivateDirectory/](https://help.ubuntu.com/community/EncryptedPrivateDirectory/)

---

### Post by glotz on 2009-05-10
I'm afraid it's the default setting. Why it is so beats me.

---

### Post by spiderbatdad on 2009-05-10
> **glotz said:**
> I'm afraid it's the default setting. Why it is so beats me.

Probably so as not to dupe users into a false sense of security...believing anything regarding multi-user computers is inherently private unless user responsibility for privacy is taken.

---


---
title: "Root to User"
date: 2008-12-27
forum: Desktop Environments
---

### Post by Ghostknyght on 2008-12-27
Ive been using the root user since Ive started using ubuntu, which I unfortunately just learned my lesson about. In an effort to change I want to use my other user, but I don't want to go through the hassle of fighting with all of my visual settings and whatnot again. Is there any way to switch them ALL over? I mean every single setting.

---

### Post by haldean on 2008-12-30
As the root user, and in the root user's home directory, use:

```
cp -r .* /path/to/non-root/user/home
chown -R non-root-username /path/to/non-root/user/home
```

The first command will copy all of the hidden files in the root home (files that start with a period - which is where most configuration is stored) to the nonroot home. The second command will make it so that those files are accessible to the nonroot user. 

Note that some programs may still not like that their configuration now belongs to a different user, so you may end up having to reconfigure some of them, but this will transfer visual settings definitely (themes, icons, fonts, etc), and many settings for other programs as well.

---


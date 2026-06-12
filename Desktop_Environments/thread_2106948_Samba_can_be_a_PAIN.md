---
title: "Samba can be a PAIN"
date: 2013-01-20
forum: Desktop Environments
---

### Post by Geffers on 2013-01-20
Why can samab be such a pain.

I want to share some of my laptop files over my local network with my Nexus.

I have allowed guest, read'write to anybody but it fails telling me there are permission problems.

An old desktop has been sharing files across my network with anyone for ages, grrr!!!

geffers

---

### Post by circa on 2013-01-20
LOL. I had the same issues with it too. I just used SSH. It's a primitive approach, but It worked when Samba wouldn't.

---

### Post by Morbius1 on 2013-01-20
>  I have allowed guest, read'write to anybody but it fails telling me there are permission problems.Two sets of permissions. Telling Samba that any remote user has read / write permissions tells it what that user [COLOR=Blue]**may**[/COLOR] do. But it has no authority over Linux permissions that dictates what that user [COLOR=Blue]**can**[/COLOR] do.

What are the linux permissions of the folder that you shared:
```
ls -dl /path/to/shared/folder
```It has to come back with: drwxrwxrwx in order for this to work  ... unless you did something exotic in your smb.conf.

BTW, Providing additional details is always helpful in these cases so you might want to post the output of the following commands when you get a sec:
```
testparm -s
net usershare info --long
```

---

### Post by martinvincent on 2013-01-21
post ur smb.conf file...

---


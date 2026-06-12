---
title: "Default Permissions on Files copied to Samba share from Windows Machine"
date: 2005-12-21
forum: Desktop Environments
---

### Post by jabber on 2005-12-21
Hi,

I am a complete newb to Linux - but am getting there. I have set up my linux machine as a samba server, which I store all my movies etc on, which I then stream to my xbox when I want to play/listen.

The problem I have is that when I copy a file to s samba share from my windows machine, the default permission assigned to it doesnt only allows read/write/execute for the owner.

This means I cannot play the movies etc on the xbox unless I manually change the permissions on the file.

My question is how can I change the default permissions assigned to a file when it is copied to the samba share from the Windows machine.

Hope this makes sense. Thanks in Advance.

James

---

### Post by zoiks on 2005-12-21
Sounds like you should be setting

```
create mask = 744
directory mask = 755
```

in smb.conf, a la [http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_03.html)

---

### Post by jabber on 2005-12-21
I knew it would be something simple - thanks for your help.

---


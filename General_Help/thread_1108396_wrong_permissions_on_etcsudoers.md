---
title: "wrong permissions on /etc/sudoers"
date: 2009-03-27
forum: General Help
---

### Post by JohanSamyn on 2009-03-27
Hi, I tampered with the /etc/sudoers file. I changed the permissions so I could edit it. But now I cannot reset the permissions back to 440. I think those wrong permissions are also the reason I cannot install any updates anymore. Can someone please tell me how to set the permissions for /etc/sudoers back to 440 ? Or how to install a root user, so I can use that to change those permissions ? I am using an Ubuntu 8.10 installed with Wubi.

---

### Post by snova on 2009-03-27
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

You might need to run this as well:

```
chown root:root /etc/sudoers
```

Before you type 'exit'.

---

### Post by JohanSamyn on 2009-03-29
@snova:
Your reply somehow helped me to find how to install a root user.
Once that was available, su root and chmod were a breeze.
I'll keep the links, just in case ...
Thanks for the help.

---


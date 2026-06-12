---
title: "Set up a fully qualified domain name"
date: 2006-06-26
forum: Desktop Environments
---

### Post by mssever on 2006-06-26
I've noticed that Apache complains about being unable to determine the fully qualified domain name (FQDN) for my machine. I know that I could edit Apache's conf to fix that, but can I set a system-wide FQDN?

Here are some details about my setup: I'm behind a router, so does that mean that I can pretty much make up a domain name as long as it's something that won't conflict with anything in the outside world?

System > Administration > Networking > General tab: I set the domain part to "local," but [FONT=Courier New]hostname -f[FONT=Verdana] only returns "scott-desktop," not "scott-desktop.local," as I would expect. I've restarted networking to no avail.

What should I do to set up a FQDN?
[/FONT][/FONT]

---

### Post by mlind on 2006-06-26
/etc/hosts
```

127.0.0.1 localhost
**192.168.1.1 server.domain server**

```

I haven't registered fqdn, so I use just
```

127.0.0.1       localhost       *alias*

```


Is this what you're looking for?

---

### Post by Abhi Kalyan on 2006-11-13
Could you please explain what is to be done to give a domain name for my box.
My systems name is viki
i dont have anything in the domain name box.
How to fill it?

---

### Post by mssever on 2006-11-29
> **Abhi Kalyan said:**
> Could you please explain what is to be done to give a domain name for my box.
My systems name is viki
i dont have anything in the domain name box.
How to fill it?

Include something like the following in /etc/hosts:
```
127.0.0.1       viki.your.domain viki localhost
::1             viki.your.domain viki localhost
```

---

### Post by drndrw on 2007-11-12
Hi. I am having this same problem but I cannot edit /etc/hosts because I cannot get permission to the file. I've tried sudo chown but it says it is not the correct path. What must I type in?

---

### Post by mssever on 2007-11-13
> **drndrw said:**
> Hi. I am having this same problem but I cannot edit /etc/hosts because I cannot get permission to the file. I've tried sudo chown but it says it is not the correct path. What must I type in?

Don't chown files unless you know what you're doing. chowning stuff willy nilly could break your system. Try ```
gksudo gedit /etc/hosts
```

---


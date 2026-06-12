---
title: "Problems with the Administration tools"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Hellaxe on 2006-03-30
Hi peopple:

My wife made a total mess trying to connect to the a wireless net on her college.
She misconfigured the hostname, the domain name the dns and all that stuff:evil: .
i've changed to the right names everything except the hostname. Now when Gnome is booting up i get the following message:

```
Could not look up internet address for <meu host>.
This will prevent GNOME from operating correctly. 
It may be possible to correct the problem by adding <meu host> to the file /etc/hosts.

Log in anyway       try again
```

After logging in a cannot enter the Networkig tools, the User tools and so on.
Please Help me.

PS: I've correct the hostname, host.conf and the resolve.conf files.

---

### Post by meborc on 2006-03-30
did you also made changes to /etc/hosts file like it suggests?

**sudo gedit /etc/hosts**
and add your host there

---

### Post by Hellaxe on 2006-03-30
I though that i made the change but i missed the hostname at the end of the first line.

Thank You. :D

---


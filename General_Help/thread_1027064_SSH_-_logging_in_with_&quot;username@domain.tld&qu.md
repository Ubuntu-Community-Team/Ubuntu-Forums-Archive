---
title: "SSH - logging in with &quot;username@domain.tld&quot; format username"
date: 2008-12-31
forum: General Help
---

### Post by TheFuzzy0ne on 2008-12-31
Hello, and happy new year!

I was wondering how to login via SSH for servers that require a username that is formatted "username@domain.tld". The issue I have here is that (to my knowledge), the CLI SSH client, and fish protocol do not understand logins like this:

[email]daz@mydomain.com@someserver.com[/email]

I'm guessing that perhaps I need quotes of some kind, but I can't be sure. I'd appreciate any input anyone can offer, that doesn't involve a reinstall ;)

---

### Post by spiderbatdad on 2008-12-31
```
ssh user:domain@server.com
```

---

### Post by TheFuzzy0ne on 2008-12-31
Problem solved!

ssh -l [email]daz@mydomain.com[/email] someserver.com

Thanks for the reply, spiderbatdad.

---


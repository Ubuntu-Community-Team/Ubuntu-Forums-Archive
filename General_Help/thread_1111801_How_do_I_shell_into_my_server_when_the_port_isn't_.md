---
title: "How do I shell into my server when the port isn't 22?"
date: 2009-03-31
forum: General Help
---

### Post by XGhozt on 2009-03-31
I change the ports for SSH access on my servers for security. Now, I could use Putty, or Kitty in wine to get to my servers. But I know there is a way to login to another server using terminal.

> Here's what I tried: **ssh xghozt.com**
But when I do that I get: **ssh: connect to host xghozt.com port 22: Connection refused**

I tried doing: **ssh xghozt.com:####**
But then I got: **ssh: Could not resolve hostname**

---

### Post by HermanAB on 2009-03-31
$ ssh user@server -p 2222

---

### Post by surfed on 2009-03-31
```
ssh -p xxxx www.host.com
```

---

### Post by XGhozt on 2009-03-31
Thanks! I got it now. :)

---


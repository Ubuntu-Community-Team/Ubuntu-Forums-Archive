---
title: "passwordless ssh login"
date: 2021-08-25
forum: Desktop Environments
---

### Post by hstoellinger on 2021-08-25
Hello,
I have been using passwordless login from my Kubuntu 21.04 laptop to my Debian 10 LAN-connected server for a long time now. All of a sudden I keep having to enter a password when doing ssh user@server. I have followed all the setup steps (ssh-keygen, copy public key to server...). What might I be missing?
Thanks for your help
Regards
H. Stoellinger

---

### Post by ActionParsnip on 2021-08-25
when you connect. Use
```

ssh -vvvvvvvvv username@servername

```
What is the output please?

---


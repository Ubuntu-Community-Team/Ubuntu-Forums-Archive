---
title: "Yubikey Login"
date: 2020-11-24
forum: Desktop Environments
---

### Post by aramane7000 on 2020-11-24
[COLOR=#D7DADC][COLOR=#000000]Hello all,
[/COLOR]
[COLOR=#000000]I'm using the guide @ [/COLOR][[COLOR=#000000]https://support.yubico.com/hc/en-us/articles/360016649099-Ubuntu-Linux-Login-Guide-U2F[/COLOR]]("https://support.yubico.com/hc/en-us/articles/360016649099-Ubuntu-Linux-Login-Guide-U2F")[COLOR=#000000].   After downgrading my Ubuntu to Bionic Beaver I've had to reapply my  Yubikey for my Ubuntu login. I've done this before with Focal Fossa and  had no issues and my Yubikey worked flawlessly. I'm just not on my game  as I was before so I could use a some assistance.
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I'm  having an issue pointing Pam to the correct file. I have /etc/Pam.d so  from what I've read from /etc/pam.conf is that /etc/pam.conf gets  ignored completely if the directory /etc/Pam.d is present. Which  configuration file do I add  "authfile=/etc/Yubico/u2f_keys" too?
[/COLOR]
[/COLOR]

---

### Post by skipbarker on 2020-12-08
I believe the file you are looking for is ```
/etc/pam.d/gdm-password
```

---


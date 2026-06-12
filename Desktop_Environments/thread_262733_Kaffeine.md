---
title: "Kaffeine"
date: 2006-09-22
forum: Desktop Environments
---

### Post by ART_Adventures on 2006-09-22
Hello People,

I have the Kaffeine media player and it doesn't seem to play any sound; if I use the DVB tuner, I can see different channels but I cannot hear them.

If I also try to play a DVD using this player, it says:

"The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Encrypted or faulty DVD)"

Can anybody help me.

Thanks.

---

### Post by ART_Adventures on 2006-09-22
Does anybody know? I'm sure I'm just doing something silly...

Thanks.

---

### Post by X.Cyclop on 2006-09-22
Did you install all the codecs?

[Add extra repos]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") and type:
```
sudo apt-get install w32codecs libxine-extracodecs libxine1c2 libdvdcss2 libdvdread3 libdvdnav4
```

;)

---

### Post by ART_Adventures on 2006-09-22
If I type sudo apt-get install w32codecs it says:

E: Couldn't find package w32codecs

Can anybody help. Thanks.

Incase it helps. If I type sudo apt-get update
 it says:

```

Get: 1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get: 2 http://gb.archive.ubuntu.com dapper-security Release.gpg [189B]
Get: 3 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get: 5 http://gb.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://gb.archive.ubuntu.com dapper-security Release
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports Release
Hit http://gb.archive.ubuntu.com dapper-security/main Packages
Hit http://gb.archive.ubuntu.com dapper-security/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://gb.archive.ubuntu.com dapper-security/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/universe Packages
Hit http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/main Packages
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-backports/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-backports/main Sources
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/universe Sources
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Sources

```

---

### Post by X.Cyclop on 2006-09-24
[Add extra repos]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") ;)

---


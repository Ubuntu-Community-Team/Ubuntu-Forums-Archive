---
title: "Quake 4 installation problem"
date: 2008-04-30
forum: Gaming &amp; Leisure
---

### Post by jdix123 on 2008-04-30
Hi.

I followed the zerowing/idgames howto to install Quake 4.  That is, i copied the pk4 files to /usr/local/games/quake4/q4base and then downloaded the 1.4.2 (latest) installer script from the website, but when I run it I get 

```

:/usr/local/games/quake4$ sudo sh quake4-linux-1.4.2.x86.run
Verifying archive integrity...Error in MD5 checksums: d7e664bd1f0d892ca59d33e27218dbe0 is different from 3838acf174131d21b16045efa2b599fd

```

However when I checked the checksums on the howto page, I didn't see either of those two entries.  Amy I just missing something obvious?

Kubuntu 8.04
AMD Sempron 2800+
1024 MB RAM
nVidia GeForce 8600

---

### Post by Bölvaður on 2008-04-30
I know Im not really helping, but try older version of the linux installer.
it worked brilliantly for me.

---

### Post by DoktorSeven on 2008-04-30
Check the actual installer's checksum with the ones on the page using md5sum:

```
md5sum quake4-linux-1.4.2.x86.run
```

If it's wrong, then you'll need to re-download.

Also, try running it with **bash** instead of **sh**:

```
sudo bash quake4-linux-1.4.2.x86.run
```

In Ubuntu, sh is linked to a bash workalike called "dash" which sometimes gives problems.  Calling bash directly gets around that.

---


---
title: "Alien package problem"
date: 2006-07-22
forum: Desktop Environments
---

### Post by leb3000 on 2006-07-22
Is anyone having problems using Alien?

And whats the --script option for? Should I include it?

I convert rpms to .deb but when I install the rpm I get errors!

Hehe WHY doesn't everyone use .deb????? (I  say that because it is the opinion of the majority of people that .deb is superior to .rpm!)

The installation in question is realplayer! I used mandrake before and its so obvious .deb format is betterr even after using .deb for a day! It's a shame some people don't release software in that format alongside rpm

---

### Post by taurus on 2006-07-22
Once you have converted .rpm to .deb, you install the .deb, NOT the .rpm!!!

```

alien <package name>.rpm
sudo dpkg -i <package name>.deb

```
Why don't you download the .bin for realplay and install it from it?  Make sure you change the permission first as

```

chmod 755 RealPlayerGOLD10.bin
sudo ./RealPlayerGOLD10.bin

```

---

### Post by leb3000 on 2006-07-22
lol yeh, sorry I meant install the .deb file.

I know about the binary installation but that makes realplayer difficult to uninstall :(

---

### Post by mlind on 2006-07-22
You can get realplayer from "commercial" Ubuntu repository.
```

deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---


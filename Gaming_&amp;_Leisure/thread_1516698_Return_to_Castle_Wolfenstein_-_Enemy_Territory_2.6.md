---
title: "Return to Castle Wolfenstein - Enemy Territory 2.60"
date: 2010-06-24
forum: Gaming &amp; Leisure
---

### Post by Vexiphne on 2010-06-24
Hi.

I've just downloaded et-linux-2.60.x86.run, but I have no idea how to install the game. I've found a lot of "how to's" but they didn't work for me because they were really old.

Could someone be so kind to explain to me how I can install RTCW-ET using et-linux-2.60.x86.run and NOT Wine. I want to use the linux version and not windows :)

I have the latest Ubuntu (10.04 desktop)

---

### Post by Perfect Storm on 2010-06-24
```
chmod +x et-linux-2.60.x86.run
sudo sh et-linux-2.60.x86.run
```


2.60b patching;
[http://www.planetwolfenstein.com/files/files.shtml](http://www.planetwolfenstein.com/files/files.shtml)

```
cd ~/Desktop
unzip et-2.60b.zip
cd "Enemy Territory 2.60b/linux"
sudo cp -r * /usr/local/games/enemy-territory
```

It may require that you install libgtk1.2.

For 64-bit: [http://gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gwos.org/doku.php/guides:64bit:et_wolfenstein)

---

### Post by Vexiphne on 2010-06-25
Thanx AI :)

You shouldn't know how I un-install it to? :)

---


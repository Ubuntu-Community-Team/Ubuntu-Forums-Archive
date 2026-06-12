---
title: "Upgrade gone wrong"
date: 2007-05-05
forum: Desktop Environments
---

### Post by Cat in a tree on 2007-05-05
I messed my upgrade from 6.10 to 7.4  up. I closed the terminal before it finished. the error i got was about lsb-base
and also mdadm. I don't remember the exact message. My desktop fonts are corrupt, everything
has a small box for a character, there are no readable characters. I am lost as to what to remove and what to reinstall.

---

### Post by webdr on 2007-05-08
same here on another machine

---

### Post by mlind on 2007-05-08
Download a ubuntu live cd, boot using it and chroot into your broken Feisty. Continue upgrade process.

```

sudo mount /dev/xxx /mnt
sudo mount -t proc proc /mnt/proc
sudo chroot /mnt
sudo aptitude update
sudo aptitude dist-upgrade

```

/dev/xxx is your Feisty root partition, which you can find out from the output of
```

sudo fdisk -l

```

You can try to do this without livdcd too, even if characters are messed up. Log in to a terminal and type
```

sudo aptitude dist-upgrade -y

```
You'll be prompted your password. Then upgrade process should continue.

---

### Post by webdr on 2007-05-08
Did this, [https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)
It worked for me.
Hope it helps others...

[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

---


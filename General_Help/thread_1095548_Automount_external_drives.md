---
title: "Automount external drives?"
date: 2009-03-13
forum: General Help
---

### Post by kahlil88 on 2009-03-13
I made the switch to Gentoo recently, and I want to configure external hard drives to automatically mount and be writable for users, like in Ubuntu.

---

### Post by circa82 on 2009-03-13
Did you setup hal (hald / hal daemon)? If you installed KDE or GNOME, you should already have it installed. You'll need to start it with:
```
/etc/init.d/hald start
```
and then set it to run at boot:
```
rc-update add hald default
```

It will automatically mount external and optical drives for you. You really won't need to configure it all that much unless you're working with NTFS file system. For that, you'll need to write a new policy to allow users besides root to have access. If it is NTFS, just post back.

---

### Post by dcstar on 2009-03-13
> **kahlil88 said:**
> I made the switch to Gentoo recently, and I want to configure external hard drives to automatically mount and be writable for users, like in Ubuntu.

Then go to a Gentoo forum and ask there - this is an **Ubuntu** help forum.

---

### Post by kahlil88 on 2009-03-13
> **circa82 said:**
> Did you setup hal (hald / hal daemon)? If you installed KDE or GNOME, you should already have it installed. You'll need to start it with:
```
/etc/init.d/hald start
```
and then set it to run at boot:
```
rc-update add hald default
```

It will automatically mount external and optical drives for you. You really won't need to configure it all that much unless you're working with NTFS file system. For that, you'll need to write a new policy to allow users besides root to have access. If it is NTFS, just post back.
Worked like a charm! I will need to access NTFS eventually, so your help would be much appreciated,

> **dcstar said:**
> Then go to a Gentoo forum and ask there - this is an **Ubuntu** help forum.
The Gentoo Forum seems kind of empty. I usually wait DAYS for responses instead of minutes. I don't think it should matter that much since Ubuntu and Gentoo are both GNU/Linux operating systems -- plus the goal I'm trying to achieve is to make Gentoo mimic Ubuntu behaviors.

---


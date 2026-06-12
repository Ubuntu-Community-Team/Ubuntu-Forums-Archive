---
title: "!IM A NOOB!  What do I do with a tar.bz2 file?"
date: 2009-04-25
forum: General Help
---

### Post by baz8771 on 2009-04-25
Hey guys, I'm a huge noob with ubuntu, and I'm trying to install yakuke, but the only way that I can find to download it is in tar.bz2 format.  What Do I even do with that? any help would be great.

---

### Post by ibuclaw on 2009-04-25
Go into:

**Applications->Add/Remove Programs**

then search for
```
yakuake
```
Then mark it for installation, and apply changes. ;)

Regards
Iain

---

### Post by linuxvacuum on 2009-04-25
```
tar -jxvf filename.tar.bz2
```

---

### Post by albinootje on 2009-04-25
> **baz8771 said:**
> I'm trying to install yakuke

For Ubuntu beginners it is really recommended to use packages, instead of starting to compile source code.

```

apt-cache search yakuake
yakuake - a Quake-style terminal emulator based on KDE Konsole technology
yakuake-kde4 - a Quake-style terminal emulator based on KDE 4 Konsole technology

```

Read also the following carefully :
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

And download the pocket guide, and read it :
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

Enjoy Ubuntu! :)

---

### Post by linuxvacuum on 2009-04-25
You can also install a graphical archive manager such as xarchiver.

---

### Post by Mike_IronFist on 2009-04-25
> **baz8771 said:**
> Hey guys, I'm a huge noob with ubuntu, and I'm trying to install yakuke, but the only way that I can find to download it is in tar.bz2 format.  What Do I even do with that? any help would be great.

Also you don't have to call yourself a noob around these parts. I think you'll find the Ubuntu community is friendly enough that we don't chastise someone for not knowing things when they're new to the system.

---


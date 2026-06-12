---
title: "Partitions can be unmounted ( permission issues, etc. ) - any workarounds ?"
date: 2009-06-11
forum: General Help
---

### Post by ActiveFrost on 2009-06-11
```
**/** [primary]
**/home** [primary]
**swap** [logical]
**/data** [logical]
```

This layout seems to be problematic - I can unmount /data partition and after doing that, I'll need to chown it ( permissions will be set to root only ).
How to make this partition so I could use it as a partition, not as a media disk ( like /home - it can't be unmounted and it's a "permanent" one ) ?

---

### Post by TeoBigusGeekus on 2009-06-11
If I understand correctly you want the partition to be mounted every time you reboot, right?
If that is the case, then you have to fiddle with your fstab file.

---

### Post by ActiveFrost on 2009-06-11
> **TeoBigusGeekus said:**
> If I understand correctly you want the partition to be mounted every time you reboot, right?
If that is the case, then you have to fiddle with your fstab file.

Well, it's always mounted on startup, but .. ehh, hard to explain !
Ok, let's say, I've 1 ext3 partition - /data. Is it possible to use it as a part of my OS, not as an extended partition ( Ubuntu shows it as "media" partition, like USB, etc. ) ?

---

### Post by merlinus on 2009-06-11
Please explain what you mean by use as part of the os?

Also, you might post results of:

```

cat /etc/fstab

```

---

### Post by ActiveFrost on 2009-06-11
> **merlinus said:**
> Please explain what you mean by use as part of the os?

Also, you might post results of:

```

cat /etc/fstab

```

I already gave an example - /home can't be unmounted and it's being used as a "folder" ( but actually it's a partition ). What I want to do is to have another "partition" used as a "folder", not as an extended "media" partition ..
About fstab - will post it a bit later on today ( can't access it at the moment ).

---

### Post by merlinus on 2009-06-11
/etc/fstab needs an entry for it.

I have a partition called /art, and here is the fstab entry for it:

# /art was on /dev/sda8 during installation
UUID=645de342-f83a-40aa-8e22-84f7bcf96332 /art  ext3  relatime  0  2

It appears as a folder in filesystem.

hth....

---


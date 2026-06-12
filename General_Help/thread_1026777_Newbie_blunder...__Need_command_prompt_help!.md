---
title: "Newbie blunder...  Need command prompt help!"
date: 2008-12-31
forum: General Help
---

### Post by ratdog on 2008-12-31
Hello,
I've been trying to get some video output to my old TV and messed something up with the nvidia-settings program.

I backed up my xorg.conf file using this command before I started changing things:
```

sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf.backup1
```

Now my computer wont boot into X.

How do I restore my xorg.conf from the command prompt?

Thank You!

---

### Post by Ahadiel on 2008-12-31
```
sudo cp /etc/X11/xorg.conf.backup1 /etc/X11/xorg.conf
```
Just the reverse of what you did to back it up...

---

### Post by donkyhotay on 2008-12-31
```
sudo cp /etc/X11/xorg.conf.backup1 etc/X11/xorg.conf
```
will copy the backup back to the original. You can then reboot by just using
```
sudo telinit 6
```

---

### Post by Slim Odds on 2008-12-31
> **donkyhotay said:**
> ```
sudo cp /etc/X11/xorg.conf.backup1 etc/X11/xorg.conf
```will copy the backup back to the original. You can then **reboot** by just using
```
sudo telinit 6
```

**restart **would be a far more appropriate word.

---

### Post by donkyhotay on 2008-12-31
> **Slim Odds said:**
> **restart **would be a far more appropriate word.

potayto/potahto, personally though I've found for a quick simple reboot/shutdown (especially when having computer problems) that it's easier to use telinit # then reboot/shutdown.

---

### Post by ratdog on 2008-12-31
Thanks so much!
I'll get a handle on this stuff someday.

---


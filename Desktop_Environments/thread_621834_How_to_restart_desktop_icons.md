---
title: "How to restart desktop icons"
date: 2007-11-24
forum: Desktop Environments
---

### Post by satbunny on 2007-11-24
Here's one that always has bugged me.

Sometimes all the desktop icons in Gnome (7.10_Gutsy but previous as well) disappear.

How can I restart the app that manages them without having to stop X and lose all running apps?

There must be a way, mustn't there?

This has bugged me since 6.06 and I've never asked before.. :confused:

---

### Post by bingoUV on 2007-11-24
Does this help?
```

nautilus -q
nautilus &

```

---

### Post by websnail on 2007-11-24
Alt+ F2 type "gnome-system-monitor"
find nautilus and kill it .
nautilus should restart , and bring your desktop icon back .

---

### Post by tibistibi on 2008-06-09
i have 8.04 and had this problem to

nautilus -q
nautilus &

worked to restore it. mayby there should be a process wich checks if other processes still work.

i had a problem with menu items to (not starting at all)

---

### Post by satbunny on 2008-06-10
An update.

Although the command line text above often worked, or using the System Monitor directly, I had problems with nautilus and desktop icons all the way through to 7.10


At which point I did 2 apparently unrelated things, I changed to mounting my Samba shares using CIFS not SMBFS and also I properly setup a WINS server on my home network (as simple as turning it on the smb.conf on my fileserver).

Not only did my network access improve but my desktop icons, most of which were mounted shares, started to behave.

I am in the process of upgrading to 8.04 (I am stuck in a partial upgrade until my home internet is fixed) and I suspect that the new ways that Nautilus talks to samba will also help.

In addition I also access a DAVFS share at my University over internet and I take care to only have that mounted as and when required and always unmount before logging off.

---


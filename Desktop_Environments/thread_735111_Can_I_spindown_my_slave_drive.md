---
title: "Can I spindown my slave drive?"
date: 2008-03-25
forum: Desktop Environments
---

### Post by mister_p_1998 on 2008-03-25
Im dual-booting Hardy & XP, with ubuntu on hda & XP on Hdb. Can I get the Windows drive to spindown as Im not using it?

---

### Post by bittdude on 2008-03-25
You should be able to spin down your drive with this command:

```
sudo hdparm -y /dev/hdb
```

---

### Post by mister_p_1998 on 2008-03-26
Great,
Thanks
and how do I make this permanant?
Steve

---

### Post by logos34 on 2008-03-26
> **mister_p_1998 said:**
> Great,
Thanks
and how do I make this permanant?
Steve

I believe you want the[ -S option]("http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#Spindown_-S"), which will spindown the drive automatically after x seconds

see **man hdparm** for more info

---


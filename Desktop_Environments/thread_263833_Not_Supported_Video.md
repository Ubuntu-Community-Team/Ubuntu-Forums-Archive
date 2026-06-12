---
title: "Not Supported Video"
date: 2006-09-23
forum: Desktop Environments
---

### Post by cccc on 2006-09-23
hi

during the dapper drake start, I get only a black screen with this message:```

NOT SUPPORTED VIDEO
```

I've tried to add in **/boot/grub/menu.lst** the following entry:```

defoptions=quiet splash vga=0x0318
```
but after:```
sudo update-grub
```this entry disappears.

howto get the startup screen during the start ?

---

### Post by cccc on 2006-09-23
```

# defoptions=quiet splash vga=0x0318

```
solved my problem !

---


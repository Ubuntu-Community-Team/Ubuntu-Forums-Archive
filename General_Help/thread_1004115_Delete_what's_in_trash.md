---
title: "Delete what's in trash:///"
date: 2008-12-06
forum: General Help
---

### Post by pan69 on 2008-12-06
I deleted some files that came from a CD and now they are stuck in my garbage bin and I can't delete them. When I request the properties is syas the location on the files is *trash:///*.

How do I delete these files?

Thanks

---

### Post by 2hot6ft2 on 2008-12-06
I'm sure there's a simple way but this is a great way to cleanup your system [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) 
And it does lots more give it a shot.

I bypass the trash myself.

---

### Post by fooman on 2008-12-06
open a terminal and type or copy/paste the following command:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by pan69 on 2008-12-07
Ah. .local/share/Trash is where they hide it.

Thanks mate!

---


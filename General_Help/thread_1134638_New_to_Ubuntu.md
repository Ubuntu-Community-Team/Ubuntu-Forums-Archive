---
title: "New to Ubuntu"
date: 2009-04-23
forum: General Help
---

### Post by Nezidig on 2009-04-23
Hey, I was just editing some values in /boot/grub/menu.lst, and I went to save it, I get no save button.

Nothing under any tabs gives me a save button, and I haven't found a shortcut to save yet.

Any help?

---

### Post by Tim Sharitt on 2009-04-23
You likely don't have permission to edit it. You will need to edit it as root. 

To do this, hit Alt-F2 and enter:

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by Nezidig on 2009-04-23
Thanks, It worked.
Can I do this to any file that I can't save on?
Like I said, I'm new to this whole Ubuntu thing.

---

### Post by LoneWolfJack on 2009-04-23
yes you can; what this command does is open the editor with root privileges. the root user may write to any file. 

be careful though as linux will assume you know what you are doing when using that command. if you break an important file you may break your installation.

---


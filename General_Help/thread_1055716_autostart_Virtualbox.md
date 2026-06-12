---
title: "autostart Virtualbox"
date: 2009-01-31
forum: General Help
---

### Post by Sid1980 on 2009-01-31
is it possible as soon as i logon ubuntu the image present inside virtualbox also starts itself ?? the whole idea is to start xp automatically as soon as ubuntu finishes logging in.

---

### Post by lykwydchykyn on 2009-01-31
You can put this as a startup command:
```

VBoxManage startvm name_of_vm

```

I don't know where GNOME configures startup commands, but that's the command to use!

---

### Post by Sid1980 on 2009-01-31
> **lykwydchykyn said:**
> You can put this as a startup command:
```

VBoxManage startvm name_of_vm

```

I don't know where GNOME configures startup commands, but that's the command to use!

thx

---

### Post by Sid1980 on 2009-01-31
and if i want to start in fullscreen mode then what will be command ??

---

### Post by lykwydchykyn on 2009-02-01
I can't remember.  Try putting VBoxManage --help into a terminal.

---


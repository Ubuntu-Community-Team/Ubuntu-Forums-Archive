---
title: "kubuntu startup"
date: 2007-10-31
forum: Desktop Environments
---

### Post by kwagster on 2007-10-31
during kubuntu startup (and xubunt and ubuntu for that matter), it hangs after the grub countdown on a blank screen until you open verbose mode (alt-f1).  i COULD open verbose mode every time but that could get real annoying.

is this a know bug or is it specific to me.

---

### Post by benerivo on 2007-11-01
I haven't seen this problem before, but you could try altering your /boot/gub/menu.lst file so that it automatically boots in to verbose mode. I haven't done this myself, but i think it could be done by changing the end of

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8fgf4d56dg74f-8426-4a9c-8e1a-565c6rj254685 ro quiet splash
```

to

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8fgf4d56dg74f-8426-4a9c-8e1a-565c6rj254685 ro noquiet splash=verbose
```

---

### Post by kwagster on 2007-11-01
thanks i'll go ahead and try that but i would also like a way to "solve" this problem, not just hide it

---


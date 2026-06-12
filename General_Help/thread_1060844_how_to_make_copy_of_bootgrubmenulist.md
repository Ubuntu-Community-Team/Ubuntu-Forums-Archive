---
title: "how to make copy of /boot/grub/menulist?"
date: 2009-02-05
forum: General Help
---

### Post by jesse c on 2009-02-05
A forum help input has recommended i make a copy of my /boot/grub/menu/list to make a back up of the file because a 'wifi-radar' install wants to change my grub list,and cautions me that my current grub list has been 'locally modified'.The problem i have is that i dont know the proper way to do this.What do i type in terminal to bring this up? The way i tried informs me "no such file exists"

---

### Post by spongypants23 on 2009-02-05
Try this:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by spiderbatdad on 2009-02-05
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst~
```
Edit: sorry too slow

---

### Post by jesse c on 2009-02-05
thanks for replies.Cant find 'solved'tool,sorry
Wait to quick to think 'solved' I replied before actually trying posted solutions.Copy/paste either solution brought up nothing.I must be missing something here.

---

### Post by oldos2er on 2009-02-05
Bash only gives feedback if there was an error. If you entered the command and saw the bash prompt again, the command completed successfully. Run 'ls' to check that the backup exists.

---

### Post by jerome1232 on 2009-02-05
> **jesse c said:**
> thanks for replies.Cant find 'solved'tool,sorry
Wait to quick to think 'solved' I replied before actually trying posted solutions.Copy/paste either solution brought up nothing.I must be missing something here.

If you want to see what is going on when commands run, -v or -V is a pretty universal flag for verbosity, it tells you exactly what the command is actually doing

for example
```
sudo cp -v /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by gjoellee on 2009-02-05
You can actually make the backup to stay anywhere on your system...

---


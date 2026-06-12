---
title: "thunar from terminal"
date: 2006-07-13
forum: Desktop Environments
---

### Post by juanjojo73 on 2006-07-13
Hallo, 

i'm sorry, my english is so bad, but i have a problem.


I'd install Xubuntu in 20 computer for a school, and they need floppy support.

Since Thunar doesn't mount floppys, i tried a script, it was basicly like:

mount /media/floppy; thunar /media/floppy; umount /media/floppy

I wanted that with a clic on a icon, it mounts the floppy, open thunar and umount the flopy when thunar's window is closed. 

In Xfce and with a normal user it didn't work because thunar is executed in background and the script doesn't wait that thunar ended to umount. But as root, or with gnome it works because the script waits until thunar is closed.

You can prove it in a terminal. just writing :

$thunar

inmediatly appears the promt $ for the next command.

How can i run thunar als user from a terminal in xfce so that terminal waits? or how do i make it that the script waits for the next command?

I wish my english wasn't so terrible.

Thank you
Juan

---

### Post by Paerez on 2006-07-13
I can offer another solution. Put a link on the desktop that says "Open Floppy" that runs the mount and thunar. Then put a link that says "Eject Floppy (Important!)" that does the unmount. Then tell people they must eject, not just take it out.

---

### Post by Ramses de Norre on 2006-07-13
Does it work when you execute ```
thunar /media/floppy && umount /media/floppy
```
instead of ```
thunar /media/floppy; umount /media/floppy
```

---

### Post by juanjojo73 on 2006-07-14
@Paerez, thank you, that will be the plan B. The easier and maybe the only thing.

@Ramses de Norre, i found no difference, thunar is executed in background and almost at the same time is the floppy unmounted, so i can't work it. Thank you very much anyway

Juan

---


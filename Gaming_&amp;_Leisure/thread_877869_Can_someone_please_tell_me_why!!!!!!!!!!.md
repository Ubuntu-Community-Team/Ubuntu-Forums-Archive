---
title: "Can someone please tell me why!!!!!!!!!!"
date: 2008-08-02
forum: Gaming &amp; Leisure
---

### Post by Repent on 2008-08-02
Can someone please tell me why after I installed Hardy my ThinkTanks game stopped working?

 [IMG][[IMG]http://img411.imageshack.us/img411/5527/screenshotwg6.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshotwg6.png)[/IMG]


Thanks a ton.

---

### Post by eragon100 on 2008-08-02
Run it from a terminal.

Commands:

cd ThinkTanks

chmod +x ThinkTanks.bin

./ThinkTanks.bin


That should work, and you can copy and paste from here :)

---

### Post by Vadi on 2008-08-02
Yeah, a bug unforunately... but you can use chmod graphically - right-click on thinktanks.bin, select properties, permissions and enable "allow execution of file as program".

---

### Post by Sockerdrickan on 2008-08-02
a bug?

---

### Post by Vadi on 2008-08-02
Some .bin files don't execute when clicked on but say no app found to run with.

---

### Post by Sockerdrickan on 2008-08-02
That's not a bug, the file doesn't have the permission to be an executable. It happens when you use an archive format that doesn't support UNIX file permissions.
Also binaries in UNIX doesn't have a binary.foo you can name them whatever.

---

### Post by Repent on 2008-08-05
OK so how do I fix it?

---

### Post by Vadi on 2008-08-05
I don't remember how did it fix here. But as a workaround, you just open the terminal, drag the application icon into it, and press enter.

---


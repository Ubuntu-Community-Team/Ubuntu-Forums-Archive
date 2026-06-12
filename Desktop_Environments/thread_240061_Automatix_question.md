---
title: "Automatix question"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Russty of Oz on 2006-08-20
Everytime I run Automatix to install something, I get the following at the end.  What does this mean?  Is there a problem? If so, how do I fix it?

[B]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open bad device
[/B]

Russty

---

### Post by Iarwain ben-adar on 2006-08-20
Hi,
just edit your xorg.conf

(comment out the "wacom" devices :D )


Iarwain

---

### Post by arnieboy on 2006-08-20
> **Russty of Oz said:**
> Everytime I run Automatix to install something, I get the following at the end.  What does this mean?  Is there a problem? If so, how do I fix it?

[B]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode: 147
  Minor opcode: 3
  Resource id: 0x0
Failed to open bad device
[/B]

Russty

[http://ubuntuforums.org/showpost.php?p=1264009&postcount=3](http://ubuntuforums.org/showpost.php?p=1264009&postcount=3)

---

### Post by Russty of Oz on 2006-08-21
Thanks for the advice, but I still don't quite understand **HOW** to edit the xorg.conf!  I tried typing in the terminal   kate xorg.conf   but it came up with the same error.  I also tried typing xorg.conf in the run command but that doesn't work either. 

I guess you guys must get tired of us novices asking what must be "simple" questions!

Russty

---

### Post by -deadcats on 2006-08-21
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Russty of Oz on 2006-08-21
Thanks, that fixed it!!:D 

Now for my next problem, I am sure there will be one!;) 

Russty

---


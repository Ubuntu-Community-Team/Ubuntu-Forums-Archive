---
title: "Major oops with permissions in /media"
date: 2009-04-16
forum: General Help
---

### Post by mithbuntu on 2009-04-16
Need help, I can't ls my /media directory anymore...
I accidentally issued a chmod incorrectly:
```

.945.[22:01 drew@mithbuntu:/media 0Mb]$ sudo chmod 777 -r .
chmod: cannot access `777': No such file or directory
ls: cannot open directory .: Permission denied
.947.[22:01 drew@mithbuntu:/media 0Mb]$ l
ls: cannot open directory .: Permission denied
.947.[22:02 drew@mithbuntu:/media 0Mb]$ ls
ls: cannot open directory .: Permission denied

```

How do I fix?

ps(it works as root)
```

.947.[22:03 drew@mithbuntu:/media 0Mb]$ sudo su
root@mithbuntu:/media# ls
cdrom  cdrom0  Clouds  Datalink  DREW'S IPOD  ISO0  ISO1  ISO2  ISO3  ISO4  ISO5  ISO6  ISO7  ISO8  ISO9  Mojo  Raptor  Terra

```

---

### Post by mithbuntu on 2009-04-16
Weird, somehow the permissions went:
d-wxrwxrwx, but only viewable to root.

Simple chmod 777 /media fixed this.

---


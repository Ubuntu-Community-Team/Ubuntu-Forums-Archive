---
title: "Vim syntax highlighting"
date: 2009-05-03
forum: General Help
---

### Post by Ubikusss on 2009-05-03
Hello,
I am new to this forums, i just started with linux a couple of months ago and i have a problem with syntax highlighting.
I searched the forum for some answers but i could'n find any. So if someone could help me i would appreciate it!
I am using ubuntu 8.10 server and i have no syntax highlighting in vim. When i use :syntax it says that the command is not available in this version...
I am realy sorry if i posted in the wrong department.

---

### Post by delcypher on 2009-05-03
Ubuntu comes with vim-tiny by default which is a reduced version of vim which has various things missing. You want to use the full package so do...

```
sudo apt-get install vim-full
```

That should do the trick.

Also you might be using compatibility mode. Try :set nocp  as well and see what happens.

---

### Post by Ubikusss on 2009-05-03
Thank you very much ! It worked, i can now use syntax enable...

---


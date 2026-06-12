---
title: "just partitioned my hd and now i need some help"
date: 2009-02-13
forum: General Help
---

### Post by sleve on 2009-02-13
so as the title says i made some space for ubu since i only have 30 gigs and have used it all already

i have my paritioned space sitting on my desktop

but i need to set permissions to be able to create folders and copy wine into this new space. 

can anyone help me out with this or should i just reinstall wine into said drive?

i would much rather be able to create my own folders on this drive..

whatever info you need just tell me how to get it and i will post

---

### Post by glotz on 2009-02-13
Drop to a terminal. If your username is sleve, this is the spell```
sudo chown -R sleve:sleve /path/to/mounted/new/partition
```

You can verify it by checking out the manual page```
man chown
```

---


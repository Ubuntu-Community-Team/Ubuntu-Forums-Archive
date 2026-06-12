---
title: "Inserting CD disables Nautilus"
date: 2009-04-28
forum: Desktop Environments
---

### Post by navneeth on 2009-04-28
This is in a fresh install of Jaunty. I did not have any problems with Intrepid. 

Every time I insert a (pre-recorded) music CD (I haven't tried any other type), all the icons on the desktop vanish, I can't browse any folder using nautilus and the context menu on the desktop (right-click) doesn't work, either. 

After I eject the CD, nautilus begins to work, but the desktop icons and right-click are missing. (Although, I think they return after a reboot.)

Under Preferences, I have Rhythmbox as my default player, and I have it set to open whenever I insert an audio CD. 

What's causing this?

---

### Post by navneeth on 2009-04-29
Bump.

---

### Post by navneeth on 2009-04-29
```
Apr 29 20:27:46 ubuntu kernel: [ 2094.072227] nautilus[4278]: segfault at 949e000 ip b655b7dd sp b5a10fc0 error 4 in libbrasero-media.so.0.1.1[b654b000+1e000]
```

**Syslog**

```
Apr 29 20:27:46 ubuntu kernel: [ 2094.072227] nautilus[4278]: segfault at 949e000 ip b655b7dd sp b5a10fc0 error 4 in libbrasero-media.so.0.1.1[b654b000+1e000]
Apr 29 20:27:46 ubuntu kernel: [ 2094.399668] end_request: I/O error, dev sr0, sector 0
Apr 29 20:27:46 ubuntu kernel: [ 2094.399683] Buffer I/O error on device sr0, logical block 0
Apr 29 20:27:46 ubuntu kernel: [ 2094.399693] Buffer I/O error on device sr0, logical block 1
Apr 29 20:27:46 ubuntu kernel: [ 2094.399702] Buffer I/O error on device sr0, logical block 2
Apr 29 20:27:46 ubuntu kernel: [ 2094.399706] Buffer I/O error on device sr0, logical block 3
Apr 29 20:27:46 ubuntu kernel: [ 2094.399711] Buffer I/O error on device sr0, logical block 4
Apr 29 20:27:46 ubuntu kernel: [ 2094.399716] Buffer I/O error on device sr0, logical block 5
Apr 29 20:27:46 ubuntu kernel: [ 2094.399721] Buffer I/O error on device sr0, logical block 6
Apr 29 20:27:46 ubuntu kernel: [ 2094.399726] Buffer I/O error on device sr0, logical block 7
Apr 29 20:27:46 ubuntu kernel: [ 2094.399731] Buffer I/O error on device sr0, logical block 8
Apr 29 20:27:46 ubuntu kernel: [ 2094.405155] end_request: I/O error, dev sr0, sector 0
Apr 29 20:27:46 ubuntu kernel: [ 2094.406663] end_request: I/O error, dev sr0, sector 4
```


I found this message in the log viewer immediately after inserting the CD. Could someone "decipher" it for me?

---


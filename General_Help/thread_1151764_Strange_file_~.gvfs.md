---
title: "Strange file ~/.gvfs"
date: 2009-05-07
forum: General Help
---

### Post by Arndt on 2009-05-07
I have an entry in my home directory which is named ".gvfs". It's a strange thing, for example when using "lsof" (on any file), it does what it's supposed to, but also reports

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home_local/arndt/.gvfs
```

ls -la shows

```
d?????????  ? ?     ?            ?                ? .gvfs/
```

What is this? Can I safely remove it? (Can I even remove it - not even root shows more information than the above.)

I'm using Intrepid.

---

### Post by salvachn on 2009-05-07
It is a directory meant for the GNOME Virtual File System. In all probability, it will be empty. You need not delete it. It is not visible on your desktop, right?

---

### Post by colau on 2009-05-07
> **Arndt said:**
> I have an entry in my home directory which is named ".gvfs". It's a strange thing, for example when using "lsof" (on any file), it does what it's supposed to, but also reports

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home_local/arndt/.gvfs
```

ls -la shows

```
d?????????  ? ?     ?            ?                ? .gvfs/
```

What is this? Can I safely remove it? (Can I even remove it - not even root shows more information than the above.)

I'm using Intrepid.
[http://www.linuxquestions.org/questions/ubuntu-63/.gvfs-file-670405/](http://www.linuxquestions.org/questions/ubuntu-63/.gvfs-file-670405/)

---


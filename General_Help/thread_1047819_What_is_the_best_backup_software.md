---
title: "What is the best backup software"
date: 2009-01-22
forum: General Help
---

### Post by ttallos on 2009-01-22
I want to syncronise my data on drive(1)with a slave drive(2). I would like to mirror my data then just update changes every day. What is the best software for this?

---

### Post by Ahadiel on 2009-01-22
rsync

---

### Post by albinootje on 2009-01-22
Indeed rsync.
If you prefer a GUI for rsync, see grsync.
In either case make sure you read a bit about rsync.
This is a simple example of rsync and the update parameter :
```

rsync -avuz source-dir destination-dir

```

Be careful with typos and the --delete parameter.

Here are some more examples :
[http://samba.anu.edu.au/rsync/examples.html](http://samba.anu.edu.au/rsync/examples.html)

---

### Post by ttallos on 2009-01-22
I can use the command line or grsync what is the command to mirror changes?

---

### Post by albinootje on 2009-01-22
> **ttallos said:**
> I can use the command line or grsync what is the command to mirror changes?

The "u" in the -avuz parameters is about "updating".
Check :
```

man rsync

```

---

### Post by mdpalow on 2009-02-03
QuickStart can help you do that and more. See link in Signature.

---


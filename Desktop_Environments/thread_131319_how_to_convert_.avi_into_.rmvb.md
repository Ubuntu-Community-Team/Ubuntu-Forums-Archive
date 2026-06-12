---
title: "how to convert .avi into .rmvb?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by forbmj on 2006-02-16
any idea? Is there any script for this purpose?

Many thanks.

---

### Post by el3ktro on 2006-02-16
What the hell is rmvb? Never heart of that!

Tom

---

### Post by christhemonkey on 2006-02-16
mencoder looks like it can do the job.
```
mencoder -ovc divx4 -oac CoPy -filme.avi filme.rmvb
```
Something like that! try reading the man page for it.

---

### Post by forbmj on 2006-02-16
thanks, but I got errors:

Couldn't find video filter 'divx4'.
Failed to open the encoder.

---

### Post by anirban.sam on 2006-02-16
install divx encoder librarys, try automatix

---


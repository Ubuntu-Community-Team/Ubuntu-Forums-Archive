---
title: "How to start a program with low priority?"
date: 2009-05-13
forum: General Help
---

### Post by DouglasCaixeta on 2009-05-13
Hi,
I use the following script to start conky during the session

```
#!/bin/bash
sleep 10;
exec conky
exit
```

I would like to know if its possible to start it with low priority. Like Nice 13, for example.
Is there a command to put on this script to make this?

---

### Post by sir_nasty on 2009-05-13
[http://ubuntuforums.org/showthread.php?t=179547](http://ubuntuforums.org/showthread.php?t=179547)

---

### Post by DouglasCaixeta on 2009-05-13
Thanks! Solved

---


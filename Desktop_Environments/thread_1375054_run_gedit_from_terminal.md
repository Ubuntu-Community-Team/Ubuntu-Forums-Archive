---
title: "run gedit from terminal"
date: 2010-01-07
forum: Desktop Environments
---

### Post by jk.cheng on 2010-01-07
i saw in mac, ppl are using this command "mate -w" to bring up textmate without hanging the terminal...

wonder, how it can be done in Ubuntu terminal...

---

### Post by adelphos on 2010-01-07
You mean, run gedit and still use the terminal for new commands? "gedit &"

---

### Post by jk.cheng on 2010-01-07
[PHP]gedit &
[1] 15058[/PHP]

how to make it totally clean??? i after gedit & nothing will display on the terminal...

---

### Post by adelphos on 2010-01-07
> **jk.cheng said:**
> [php]gedit &
[1] 15058[/php]how to make it totally clean??? i after gedit & nothing will display on the terminal...

Oh, you don't want it to output warnings or anything? You can output that to a log file... so "gedit > log &". When you first enter that, you'll still see the process number as above, but nothing else afterward. Just press enter and you won't hear from gedit. The output will be in that file.

---

### Post by mcduck on 2010-01-07
You can also use "nohup" (as in No Hang Up). Some programs will still hang up if you close the terminal when started with an "&" in the end. Using ohup solves that problem since it starts the program as a separate process from the terminal, and redirects all messages to a text file (~/nohup.out).

```
nohup gedit &
```

---


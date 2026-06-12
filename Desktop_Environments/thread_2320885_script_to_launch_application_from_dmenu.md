---
title: "script to launch application from dmenu"
date: 2016-04-18
forum: Desktop Environments
---

### Post by Schema_Query on 2016-04-18
I want to write a bash script or a launcher to connect to localhost from dmenu... something like this  "firefox localhost". I want to be able to run this shortcut from dmenu. how do I do that? How do I use export path /to/bin correctly for this example?

---

### Post by vasa1 on 2016-04-18
> **Schema_Query said:**
> I want to write a bash script or a launcher to connect to localhost from dmenu... something like this  "firefox localhost". I want to be able to run this shortcut from dmenu. how do I do that? How do I use export path /to/bin correctly for this example?

Do you have *~/bin* in your PATH? Check the output of *env* for that. If you do, put any script there and *dmenu* will find it.

```
...
PATH=/home/vasa1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
...

```

---


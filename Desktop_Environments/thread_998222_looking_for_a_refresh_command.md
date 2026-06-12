---
title: "looking for a refresh command"
date: 2008-11-30
forum: Desktop Environments
---

### Post by Underpants on 2008-11-30
I'm looking for a command I found a while back and can't find it no matter how much digging I do.

The command basically refreshed a given command line every x number of seconds....

so i want to keep an eye on a raid expansion with my command of "cat /proc/mdstat" but I want to refresh the data that it shows me every 2 seconds...

anyone help me out?

---

### Post by __Ryan__ on 2008-11-30
Your thinking of the watch command:

```
$ watch -n *seconds* **command**
```

specifically:

```
watch cat /proc/mdstat
```

or this also works well:

```
tail -f /proc/mdstat
```

---


---
title: "All Icons desappeared in Unity launcher"
date: 2016-08-13
forum: Desktop Environments
---

### Post by vv7 on 2016-08-13
All icons just hidden and they work. I don't know why and when ... just *BAM* and disappeared ...

[IMG]http://i.imgur.com/ocaJOtq.png[/IMG]

Why and how I can repair without restarting machine ?

---

### Post by Frogs Hair on 2016-08-13
Hello and Welcome 

I can't explain why this would happen, but you can try the following in the terminal.

```
sudo apt-get install dconf-tools
``` ```
dconf reset -f /org/compiz/
```

---

### Post by vv7 on 2016-08-13
Thanks, worked, but ... why this happened ? :o

---


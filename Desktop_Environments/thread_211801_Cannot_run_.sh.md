---
title: "Cannot run .sh"
date: 2006-07-08
forum: Desktop Environments
---

### Post by plexi50 on 2006-07-08
When I try to run ./make_iso.sh I get the following error:

bash: ./make_iso.sh: Permission denied

What am I missing? It will not run as root either, and I am in the correct directory. I can run the same script in my Mepis terminal on my desktop, but not in Ubuntu on my laptopl

---

### Post by bluevoodoo1 on 2006-07-08
Try making it executable first...

```
chmod +x make_iso.sh
```
then to run it...
```
./make_iso.sh
```

---

### Post by plexi50 on 2006-07-08
That did the trick, thanks for your help.

---


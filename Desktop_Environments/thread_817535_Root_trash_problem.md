---
title: "Root trash problem"
date: 2008-06-03
forum: Desktop Environments
---

### Post by Valsodar on 2008-06-03
running on Ubuntu 8.04 with Gnome

This is the problem I experience: if I run sudo nautilus and click the root trash from the left side panel nautilus freezes. My trash folder is located under /root/.local/share/Trash with permission drwx------ (or 0700, just like my normal user trash folder). I also noticed that if I type in nautilus address bar "trash:///" it comes with the following: Couldn't find "/root/.local/share/trash:".

Now this is not a big deal, I can aways use terminal to remove it or navigate nautilus to it and shift+delete but I wonder what is causing this? Any suggestions?

---

### Post by bullon on 2008-06-21
I have the same problem, except that I have no idea how of how to empty my root trash from the terminal :S

---

### Post by aysiu on 2008-06-21
Unrelated issue: the proper command is ```
gksudo nautilus
``` not *sudo nautilus*. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

No idea about the freezes. It could be anything from a crappy theme to a bad X configuration... or just a bug the Ubuntu developers haven't fixed or aren't aware of yet.

---

### Post by Valsodar on 2008-06-22
I tried gksudo nautilus, but the problem is persistent. I think this might be a nautilus problem. Anyhow to delete your root trash from the command line use:

```
rm -r /root/.local/share/Trash
```

However be extremely careful with that and I will recommend aways to use

```
rm -ri /root/.local/share/Trash
```

---

### Post by aysiu on 2008-06-22
*Be extremely careful with that* means *make sure you **paste** that command instead of retyping it.*

---


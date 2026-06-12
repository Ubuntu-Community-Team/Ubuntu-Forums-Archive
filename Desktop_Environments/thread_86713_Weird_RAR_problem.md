---
title: "Weird RAR problem"
date: 2005-11-06
forum: Desktop Environments
---

### Post by spdfrk on 2005-11-06
Hi!

I can't extract rar files in Ark, Krusader or from the console. I've tried unrar-free & nonfree. Currently running the nonfree version. I can open the archive and see the content but when I try to extract it aborts in 1 second.

Any ideas?

---

### Post by 23meg on 2005-11-06
```
sudo apt-get install rar unrar
```

Did you try this?

---

### Post by nSTKo on 2005-11-06
Maybe try like this...
```

1) sudo apt-get install unrar
2) cd /.....
3) unrar e file.rar

```

---

### Post by spdfrk on 2005-11-06
Yes, I tried that too. Same error!

Is there rar files that are too new for rar & unrar to handle?

---

### Post by 23meg on 2005-11-06
Can you tell us the exact error you're getting when you do it from console?

---

### Post by nSTKo on 2005-11-06
[QUOTE=spdfrk]
Is there rar files that are too new for rar & unrar to handle?[/QUOTE]
Don't think so... I'm using **U**buntu, unrar is workin` for me ideally.

---

### Post by spdfrk on 2005-11-06
[QUOTE=23meg]Can you tell us the exact error you're getting when you do it from console?[/QUOTE]

The console says the archive is corrupt, which I'm pretty sure is wrong.

---


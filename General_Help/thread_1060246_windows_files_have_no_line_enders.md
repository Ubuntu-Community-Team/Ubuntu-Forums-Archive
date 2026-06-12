---
title: "windows files have no line enders"
date: 2009-02-04
forum: General Help
---

### Post by kkruecke on 2009-02-04
On Ubuntu Intrep using Nautilus, I copied and pasted several Windows Vista directories (and their files). But now the line ending are gone.

So when I edit one these pasted files in vim, I see numerous "^M" where the line endings should be. I can correct this by doing
:%s/\r/\r/g
But I don't want to have to edit every single file. How can I do this in one command. I've tried 
```
tofrodos -d 
```
but that didn't work. I've tried using sed but that didn't work.

---

### Post by kkruecke on 2009-02-04
This seems to work (to insert line endings at the appropriate spots) but I don't know how to turn it into a bash script.
```

tr -s "\r\n" "\012" < inputfile > temp
cat temp > inputfile

```

---


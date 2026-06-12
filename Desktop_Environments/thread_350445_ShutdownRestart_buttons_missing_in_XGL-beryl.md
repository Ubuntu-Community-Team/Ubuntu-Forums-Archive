---
title: "Shutdown/Restart buttons missing in XGL-beryl"
date: 2007-01-31
forum: Desktop Environments
---

### Post by lilredfoxie on 2007-01-31
hi, I finally get beryl working after doing research on the forums here and stuff, and now my shutdown/restart buttons are missing. Ive tried adding the hack to startxgl.sh

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f9)"
xauth -i add :1 . "$cookie"
```

and it still doesnt give me the buttons, is there anything else i'm missing


My sytstem specs:
Dell Inspiron E1505/6400
ATi X1300 with fglrx drivers

---

### Post by lilredfoxie on 2007-02-01
Should I post my xorg.conf or startxgl.sh?

---


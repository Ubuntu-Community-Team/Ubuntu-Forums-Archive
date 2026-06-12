---
title: "Steam won't update."
date: 2018-11-14
forum: Gaming &amp; Leisure
---

### Post by malikiag on 2018-11-14
So I downloaded Steam on my computer via the Ubuntu Sowtware app and started it up. It loads in a window mark as "Unknown". once the update bar gets close to finishing, it stops and displays the message "Fatal Error: Failed to load steamui.so". Does anyone know what is going on?

---

### Post by oldrocker99 on 2018-11-14
Try this:
```
sudo apt purge steam && sudo apt install steam
```

That error you got would indicate that the first installation was nerfed somehow.

---

### Post by ununtrium on 2018-12-18
did method given work or do you still need help?

---


---
title: "copy"
date: 2006-08-18
forum: Desktop Environments
---

### Post by simukas on 2006-08-18
i need to copy some files to /usr/share but i don't have the permitoin and when i use sudo cp i get ommiting directory and that's all

---

### Post by meng on 2006-08-18
What's the exact command you're typing?
sudo cp -- what's the rest?

---

### Post by simukas on 2006-08-18
sudo cp /home/simukas/scourge_data /usr/share/

---

### Post by taurus on 2006-08-18
> **simukas said:**
> sudo cp /home/simukas/scourge_data /usr/share/
Try

```

sudo cp -R /home/simukas/scourge_data /usr/share

```

---

### Post by simukas on 2006-08-18
ok

---


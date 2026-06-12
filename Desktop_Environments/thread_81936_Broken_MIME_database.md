---
title: "Broken MIME database"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Corvillus on 2005-10-25
Earlier today, building a package from source and installing it, i ovewrote the MIME database, and now all of my non-multimedia files are either text/plain or application/x-octet-stream. Is there a way to rebuild the MIME database without reinstalling all the associated packages or the whole OS?

---

### Post by Corvillus on 2005-10-25
Fixed it, for those who are interested, I used the following command
```
sudo update-mime-database /usr/share/mime
```

---


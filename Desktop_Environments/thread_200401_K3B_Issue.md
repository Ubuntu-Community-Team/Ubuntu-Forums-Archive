---
title: "K3B Issue"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Mike_N on 2006-06-20
Everytime i start a new session, K3B takes like five minutes to open. After that, it opens just fine but the first time seems to take forever. What could be causing this?

Thanks, Mike

---

### Post by Sgood1971 on 2006-06-20
Are you running KDE or Gnome? If you are running Gnome, you will see a delay as KDE Libraries are loaded. When you close K3B, it will not automatically dump everything from RAM, but instead keep it cached in case you need it again. (Unless something else happens to need that RAM) that's why it is quicker the second time.

---


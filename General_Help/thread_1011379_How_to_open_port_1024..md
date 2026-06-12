---
title: "How to open port 1024."
date: 2008-12-14
forum: General Help
---

### Post by miked860 on 2008-12-14
I can't use the webmail extension for Thunderbird.

---

### Post by adult swim on 2008-12-14
from a terminal run ```
sudo ufw enable

sudo ufw allow 1024
``` that will take care of your software firewall, you may need to open the port on your router too.

---

### Post by miked860 on 2008-12-14
Thank you very much. I appreciate the help.

---

### Post by karlr42 on 2008-12-14
Is your issue resolved? If so, mark the thread as solved. If not, please don't hesitate to ask for further help.

---


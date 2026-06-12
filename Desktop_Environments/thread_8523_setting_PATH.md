---
title: "setting PATH"
date: 2004-12-18
forum: Desktop Environments
---

### Post by Razvan on 2004-12-18
Hi all,

how can i add "/opt/jdk1.5.0/bin" to PATH, so that its still there, when i open the terminal the next time and also in the consoles?

preferably for all users...

thanks in advance, Martin

---

### Post by jiyuu0 on 2004-12-18
sudo gedit /etc/bash.bashrc

at the end of file

PATH=$PATH:/opt/jdk1.5.0/bin
export PATH

---

### Post by Razvan on 2004-12-18
[QUOTE=jiyuu0]sudo gedit /etc/bash.bashrc

at the end of file

PATH=$PATH:/opt/jdk1.5.0/bin
export PATH[/QUOTE]
 thanks a lot!

---


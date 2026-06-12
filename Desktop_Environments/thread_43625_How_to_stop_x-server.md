---
title: "How to stop x-server"
date: 2005-06-22
forum: Desktop Environments
---

### Post by billiejoex on 2005-06-22
Hi all! :) 
How can I definitively stop the x-server?
When I try to stop it by pressing ctrl+alt+canc it just restart. :\

---

### Post by az on 2005-06-22
CTRL-ALT-F1
login
sudo /etc/init.d/gdm stop



To stop it forever, 
sudo apt-get remove gdm

---


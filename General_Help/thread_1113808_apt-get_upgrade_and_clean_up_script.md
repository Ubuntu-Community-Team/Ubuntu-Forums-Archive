---
title: "apt-get upgrade and clean up script"
date: 2009-04-02
forum: General Help
---

### Post by magnus0 on 2009-04-02
I have made a simple script, that updates the system and cleans up after it. Very handy, because you don't have to enter all the commands  by yourself.


You must first install deborphan to find orphaned packages:
```
sudo apt-get install deborphan
```

```
#!/bin/bash/
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo deborphan | xargs sudo apt-get remove --purge
```

You can just download the attachment file too.

---


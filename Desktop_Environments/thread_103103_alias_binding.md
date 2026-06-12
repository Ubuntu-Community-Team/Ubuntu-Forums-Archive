---
title: "alias binding?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by jaykup on 2005-12-13
How can I set it up so i just type "steam" in the terminal to load it up?  It needs to load through wine, so usually i have to CD to the directory, then wine steam.exe

---

### Post by kaamos on 2005-12-13
Hello! You can try:

sudo gedit /usr/local/bin/steam

insert this text to the file:```

#!/bin/bash
cd **/directory/to/go**
wine steam.exe

```
sudo chmod +x /usr/local/bin/steam
steam

---

### Post by jaykup on 2005-12-13
thank you, that was amazingly simple.  That also explains a lot.

---


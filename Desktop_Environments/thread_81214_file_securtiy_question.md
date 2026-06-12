---
title: "file securtiy question"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Georgie-o on 2005-10-23
is their any way to put a password on a file or folder on your desktop?

---

### Post by invalid on 2005-10-23
You could make it owned by another user (root, for example)
sudo chown root:root file

And then make it only accesable by that user
sudo chmod 700 file

Cheers,
Cb

---

### Post by Georgie-o on 2005-10-23
possible to explain a solution, this or other, that is easy enough for a true newb...

thanks for the help

---


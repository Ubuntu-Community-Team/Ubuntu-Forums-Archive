---
title: "Accidently Encrypted the /etc/group file...cant do anything now!"
date: 2009-06-15
forum: General Help
---

### Post by razorman8669 on 2009-06-15
I was making an edit to my /etc/group file using VIM by adding a user to the polkituser line, and when I went to save the file...my caps lock button was on so I typed :X instead of :x and it encrypted my file...I wasnt sure why it asked for an encryption key so I just typed my password for the encryption key...well now the file is encrypted, and for some reason I cant even sudo into the file for editing, its only read only...I need to decrypt this file but I dont know how???  Does anyone know how I would go about solving this issue?

---

### Post by rfreedman on 2009-06-15
try  "sudo vim -x /etc/group"

---


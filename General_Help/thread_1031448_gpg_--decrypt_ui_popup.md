---
title: "gpg --decrypt ui popup"
date: 2009-01-05
forum: General Help
---

### Post by kbuel on 2009-01-05
When I do:

gpg --decrypt myFile.pgp

a popup window appears and asks for the password for the key used to decrypt the file.


I think this is new with integration with seahorse.  I really don't like the popup window, and would like everything to be contained in the terminal.  Is there a way to disable this popup window and allow me to type the password in the terminal window like old times?

Thanks.

---

### Post by kbuel on 2009-01-06
is there a seahorse setting that can be performed, or a gpg setting?

---

### Post by heindsight on 2009-01-06
try
```
gpg --no-use-agent --decrypt file.pgp
```

---


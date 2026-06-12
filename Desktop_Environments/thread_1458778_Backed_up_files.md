---
title: "Backed up files"
date: 2010-04-20
forum: Desktop Environments
---

### Post by d1brian on 2010-04-20
Is there a way to auto-delete (or avoid creation) of backed up files (if that's what they are called) with the ~ character at the end?

---

### Post by utnubuuser on 2010-04-20
Referring to documents created or edited with Gedit?

Gedit has preference controls to enable/disable automatic backups.

Edit>>Prefernces>>Editor

And > rm *~will remove any file ending with ~ -USE WITH CAUTION

If you give rm an -i argument, like so: > rm -i *~ confirmation will be required before deletion.

(it's actually good to alias rm with -i so any deletions require confirmation - -i stands for 'interactive' - you can setup aliases in your bashrc file)

---

### Post by d1brian on 2010-04-20
Thanks. Guess i didn't look hard enough cause i looked serveral times in the preference menu for that option.

---


---
title: "Permission issue when copying from a CD"
date: 2005-10-20
forum: Desktop Environments
---

### Post by marion on 2005-10-20
I've backed up my files to CD, and made the change to Ubuntu 5.10.  How can I change the files back to a read/write/execute state for the user with 1 command.

Can I do a chmod recursively through the file folders?

I really don't want to have to change the permissions on every file/folder 1 at a time.

---

### Post by RAOF on 2005-10-20
chmod -R <whatever> will recurse through subdirectories.  So chmod -R 755 * will give everything 755 permisions.  Chmod -R u+w * will add user write permissions to everything, etc.

But for future reference, tar-ing everything and then copying that onto a CD will preserve the correct permissions.

---

### Post by marion on 2005-10-20
Thanks you, and thanks for the advice.

---


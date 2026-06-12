---
title: "website update"
date: 2009-05-09
forum: General Help
---

### Post by oldgarol on 2009-05-09
I'm trying to update my website which runs in Ubuntu 8.04. I have to overwrite files and folders but the system will not allow me. I have tried Filezilla and SSH secure shell, any advice please?

---

### Post by mb_webguy on 2009-05-09
If it's a default LAMP installation, the default Apache web directory is /var/www, and is only writable by root.  If you want to add or alter files in that directory as your own user account, you need to either use sudo or else change the permissions on the directory (and likely the files it contains).

---


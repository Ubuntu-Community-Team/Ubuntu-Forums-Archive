---
title: "Running .bin files"
date: 2009-01-02
forum: General Help
---

### Post by arsen13 on 2009-01-02
I've run a .bin file for installing JRE for ubuntu with this commands using terminal:
chmod a+x name_of_file.bin
sudo ./name_of_file.bin
it created a directory on the desktop with for JRE application.
and now i can't delete it from my desktop, can anyone help me?
by the way i'm running ubuntu x664
Thanks
-arsen13

---

### Post by donkyhotay on 2009-01-02
It was created when the .bin was run as root so it's owner/group are root. The only way to delete this is with root permission
```
sudo rm -fr ./name_of_directory
```

---


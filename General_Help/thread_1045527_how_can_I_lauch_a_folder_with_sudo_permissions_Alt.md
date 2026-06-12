---
title: "how can I lauch a folder with sudo permissions Alt-F2?"
date: 2009-01-20
forum: General Help
---

### Post by Lukasz Tarkowski on 2009-01-20
how can I lauch a folder with sudo permissions Alt-F2?

---

### Post by taurus on 2009-01-20
You mean open a directory using nautilus with root privilege?

```
gksudo nautilus *directory*
```

---

### Post by Lukasz Tarkowski on 2009-01-20
Thank you taurus

---

### Post by ubuntu27 on 2009-01-20
You can install "nautilus-gksu" to open files with root privileges in nautilus:

```
sudo apt-get install nautilus-gksu
```

That way you won't have to resort in going to the terminal every time you want to open-up something as root.

I also recommend you to install "nautilus-open-terminal". It is an nautilus plugin for opening terminals by just right clicking a directory.

```
sudo apt-get install nautilus-open-terminal
```

---


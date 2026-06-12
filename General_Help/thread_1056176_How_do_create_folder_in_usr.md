---
title: "How do create folder in /usr"
date: 2009-01-31
forum: General Help
---

### Post by jfinner1 on 2009-01-31
I need to create a folder in the /usr folder, and then paste a file into it. But, I don't have the correct permissions. So, is there a way to do this? How? Thanks in advance.

---

### Post by taurus on 2009-01-31
Applications -> Accessories -> Terminal
```
sudo mkdir /usr/new_directory
sudo mv filename /usr/new_directory
```
Or run nautilus with root privilege.

```
gksudo nautilus
```

---

### Post by jfinner1 on 2009-01-31
Worked like a charm, thank you!

---


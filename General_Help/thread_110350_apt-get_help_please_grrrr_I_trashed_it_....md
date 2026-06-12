---
title: "apt-get help please grrrr I trashed it ..."
date: 2005-12-30
forum: General Help
---

### Post by stevewabc on 2005-12-30
I deleted the files in /var/lib/apt/lists/partial can someone please post there files so I can past them back in ... thanks then I will be able to run update..:confused: or I hope.


Homefront:/home/steven#sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by timfrost on 2005-12-30
try the foilllowing:

```

sudo mkdir -p /var/lib/apt/lists/partial

```

The erorr refers to the directory itself, not the contents.

What command did you issue to remove it?

---

### Post by justinesalo on 2005-12-30
mine's empty...maybe you just deleted the directory and need to mkdir?  just a guess.

---

### Post by stevewabc on 2005-12-30
thanks for your help....

---


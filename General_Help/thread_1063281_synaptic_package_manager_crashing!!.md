---
title: "synaptic package manager crashing?!?!?"
date: 2009-02-07
forum: General Help
---

### Post by morbid_bean on 2009-02-07
after a fresh install and updates i decide to install some programs...during the download it will crash

```
(synaptic:5959): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
Illegal instruction

```

---

### Post by utnubuuser on 2009-02-08
Something must have went awry during the install.  Try re-installing synaptic, and maybe try (in terminal):> sudo dpkg --configure -a

---

### Post by Mozenrath on 2010-08-11
Worked like a charm!  Thanks utnubuuser!

---


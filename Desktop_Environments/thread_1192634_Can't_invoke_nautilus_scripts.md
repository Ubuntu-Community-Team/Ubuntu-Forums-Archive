---
title: "Can't invoke nautilus scripts"
date: 2009-06-20
forum: Desktop Environments
---

### Post by gruszczy on 2009-06-20
I have installed nautilus collections of scripts for svn, but when I right click somewhere there is no scripts option in the context menu. Could you give me a hint, what am I doing wrong or what else I have to do?

---

### Post by days_of_ruin on 2009-06-20
[http://g-scripts.sourceforge.net/faq.php]("http://g-scripts.sourceforge.net/faq.php")

---

### Post by gruszczy on 2009-06-20
I wouldn't dare post here, if I haven't checked nautilus FAQ first, but I haven't found any information there. Maybe some other source?

---

### Post by days_of_ruin on 2009-06-20
When did you install it? Have you logged out since then?
If not try "killall nautilus".

---

### Post by gruszczy on 2009-06-20
Several hours ago. I have rebooted just after installing, because I believed, that it is needed to take effect. Trying killall nautilus didn't help.

---

### Post by Xgen on 2009-06-20
Where are the scripts? To be recognized they should be under your home directory in .gnome2/nautilus-scripts.

---

### Post by gruszczy on 2009-06-20
Yep, they weren't there. And when I googled for it, I found this magic line:

```

nautilus-script-manager enable Subversion

```

that did the trick.

Thanks a lot for your help.

---


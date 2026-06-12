---
title: "Konsole doesn't save the state about opened tabs"
date: 2008-11-03
forum: Desktop Environments
---

### Post by Marabu on 2008-11-03
Hi folks

Since I upgraded to Kubuntu 8.10 I've got the following problem:

In KDE 3 I could always leave my Konsole open when shutting down my computer. I use many different tabs for different users and machines. Upon restart, Konsole would open in the  state I left it. It opened all the tabs and also changed to the different directories.

Since I upgraded to KDE 4, Konsole still opens when I log in but only with one tab. This is a bit annoying as I have to restore all my tabs with their names and `cd` to the different directories.

Does anybody know if there is a way to store the current session in Konsole of KDE 4 including open tabs with their names and directories?

Thanks,
Michael

---

### Post by Azazelus on 2008-11-05
> **Marabu said:**
> 
Does anybody know if there is a way to store the current session in Konsole of KDE 4 including open tabs with their names and directories?

Unfortunately, this is the only thing keeping me away from upgrading Kubuntu to 8.10 on my "working" machine. I consider this as important feature and I am really surprised it disappeared from KDE4.
I spent some time looking for the solution, and the only information I found was that it should be introduced in KDE 4.2, not sure it was reliable source of information though.

Does anyone know if there is some other terminal program available supporting restoring sessions and tabs?

---

### Post by at165db on 2008-11-05
Yeah... this is a feature I miss.  I'd be interested in the fix.

---

### Post by cameronsstone on 2008-11-05
This is apparently fixed in kdebase trunk, and will be part of the KDE 4.2 release. It may also be included in a minor release of 4.1, which means intrepid updates might get it.

See [http://bugs.kde.org/show_bug.cgi?id=152761]("http://bugs.kde.org/show_bug.cgi?id=152761") for the details.

---

### Post by gizmobay on 2009-01-27
Thanks for the info. I do hope they fix this in 4.2.

---


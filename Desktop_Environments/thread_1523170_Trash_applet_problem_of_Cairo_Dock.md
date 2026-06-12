---
title: "Trash applet problem of Cairo Dock"
date: 2010-07-03
forum: Desktop Environments
---

### Post by chaopoch on 2010-07-03
The hard disk is divided into three partitions, root (sda3)&#12289;sda1 and sda2, the trash applet will change from empty to full if I delete something on the Desktop, but the trash remains empty when I delete documents from sda1 and sda2, any way to fix it? thanks.

---

### Post by fabounet on 2010-07-06
you can add maunally the paths of the other trash folders in the applet's config.
at the moment it doesn't find them automatically.

---

### Post by chaopoch on 2010-07-06
> **fabounet said:**
> you can add maunally the paths of the other trash folders in the applet's config.
at the moment it doesn't find them automatically.

Which section should I add the paths of the other trash folders in the applet's config window? I can not find it, could you describe more detailedly? thanks a lot.

---

### Post by fabounet on 2010-07-07
there is a widget with an "add" button, where you can add paths of trash folders.

---

### Post by chaopoch on 2010-07-08
> **fabounet said:**
> there is a widget with an "add" button, where you can add paths of trash folders.

there is NOT a widget with an "add" button, here are the screenshots of trash config window for your reference.

[ATTACH]162749[/ATTACH]
[ATTACH]162750[/ATTACH]
[ATTACH]162751[/ATTACH]

---

### Post by fabounet on 2010-07-08
ah sorry, I thought there were an "add" button.
you can add them in the penultimate text entry, separated by semi-colon ';'

---

### Post by fabounet on 2010-07-29
The problem is fixed in the latest beta.
Now the dock handles all the volumes correctly.

---


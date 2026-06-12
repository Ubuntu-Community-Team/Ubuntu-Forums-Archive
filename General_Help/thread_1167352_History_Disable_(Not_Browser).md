---
title: "History Disable (Not Browser)"
date: 2009-05-22
forum: General Help
---

### Post by jaydee3 on 2009-05-22
I have been looking all over and can not find the command to disable the folder history. The history located under the "Go" menu in the file browser.

Thanks in advance

---

### Post by unutbu on 2009-05-22
I don't know if this has bad secondary effects, but it does erase the directory history under Nautilus' Go menu:
```

pkill nautilus
```
This kills the current nautilus process. It appears a new nautilus process is restarted immediately afterwards.

---

### Post by jaydee3 on 2009-05-22
Still no luck. Is there a way to just shut off all tracking/history?

---

### Post by asmoore82 on 2009-05-22
This is a very old Gnome "bug" with much discussion,
there *should* be a simple way to remove "Recent Docs" from the menu entirely ...

but for now the good old Hack still works:
```
rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel
```

^you are putting a directory where nautilus expects a plain file
so that it will be unable to store the recent file history.

---

### Post by jaydee3 on 2009-05-23
Thanks, that did work to remove the Docs. I am still having trouble removing the history in the file browser.

Example: Go to your Home Folder, Click GO and look towards the bottom. It lists the history of every folder you have visited.

---


---
title: "Trash can always empty?"
date: 2009-05-08
forum: General Help
---

### Post by Roxlo on 2009-05-08
It seems as if when I delete anything the trash can stays empty and doesn't get filled with whatever I send it. Are the files actually being deleted or moved somewhere else? How can I make it back to normal?

---

### Post by drs305 on 2009-05-08
You can check your trash bin with this command:
```

nautilus $HOME/.local/share/Trash/files

```
You should also be able to get to the folder by typing this in the nautilus address bar:
> 
trash:///

This is where the user's trash is kept until you empty the trash bin. If there is nothing there, delete something and it should show up. If it does and the trash icon still shows empty, it's an icon problem. 

PS: Root's trash is at /root/.local/share/Trash and should be emptied from time to time as well. If deleting trash from within nautilus, use SHIFT-DELETE to permanently remove it.

If nothing shows up, you may have your system set to immediately delete trash without sending it to the bin.

---

### Post by Roxlo on 2009-05-08
> **drs305 said:**
> You can check your trash bin with this command:
```

nautilus $HOME/.local/share/Trash/files

```
You should also be able to get to the folder by typing this in the nautilus address bar:

This is where the user's trash is kept until you empty the trash bin. If there is nothing there, delete something and it should show up. If it does and the trash icon still shows empty, it's an icon problem. 

PS: Root's trash is at /root/.local/share/Trash and should be emptied from time to time as well. If deleting trash from within nautilus, use SHIFT-DELETE to permanently remove it.

If nothing shows up, you may have your system set to immediately delete trash without sending it to the bin.

A simple restart solved the problem. Thanks!

---


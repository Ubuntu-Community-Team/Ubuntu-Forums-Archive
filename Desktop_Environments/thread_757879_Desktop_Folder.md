---
title: "Desktop Folder"
date: 2008-04-17
forum: Desktop Environments
---

### Post by Rmg12 on 2008-04-17
I accidentally copied my desktop folder into the desktop, and I then moved it to the deleted items folder. Now when I try to delete it its comes up with an error. I then looked inside the desktop folder and there was another. When  I clicked properties, it said 501 subfolders. Is there anyway of deleting it?

---

### Post by pytheas22 on 2008-04-17
You could probably delete the folder with the command:

```

rm -rf ~/.Trash/*
```

(note that this will also remove any other files in the Trash folder)

If that doesn't solve the problem, please tell us exactly what the error message says when you try to delete the folder.

---

### Post by Rmg12 on 2008-04-19
> **pytheas22 said:**
> You could probably delete the folder with the command:

```

rm -rf ~/.Trash/*
```

(note that this will also remove any other files in the Trash folder)

If that doesn't solve the problem, please tell us exactly what the error message says when you try to delete the folder.

Sorry, that didn't work :(
The error message came up once and said: 
Error while deleting.
Couldn't remove folder: Desktop

Directory not empty.




Within the desktop folder there is another desktop folder and within that there is another: This carries on and on and it has about 500 folders in.

---

### Post by pytheas22 on 2008-04-19
In that case, you could try:
```

rm -rf ~/Desktop
```

this will delete your entire desktop and everything on it, so be sure to move anything that you don't want deleted.  I'm not sure what will happen if you try this command while in graphical mode; it might cause problems for Nautilus, or prompt Nautilus to automatically recreate your desktop.  If possible, it would be best to run the command while X is not running.  But either way it shouldn't be a big deal.

If necessary, you can recreate your desktop with:
```

mkdir ~/Desktop
```

---

### Post by Rmg12 on 2008-04-20
> **pytheas22 said:**
> In that case, you could try:
```

rm -rf ~/Desktop
```

this will delete your entire desktop and everything on it, so be sure to move anything that you don't want deleted.  I'm not sure what will happen if you try this command while in graphical mode; it might cause problems for Nautilus, or prompt Nautilus to automatically recreate your desktop.  If possible, it would be best to run the command while X is not running.  But either way it shouldn't be a big deal.

If necessary, you can recreate your desktop with:
```

mkdir ~/Desktop
```

So I should run it in safe mode (terminal only?) - I forgot to say the folder was a copy into the desktop (when a message saying cannot move deskop/desktop/desktop ... and on) so then I moved to the deleted items bin, and when I tried to empty it comes up with the message above.

---

### Post by pytheas22 on 2008-04-20
Yes, safe mode or something like that would be the best way to do it, only because there are some things running with the graphical interface that expect there to be a desktop, and they might crash if it gets temporarily deleted.  The easiest approach would be doing it from the "failsafe terminal" -- when you get to the Ubuntu login screen, under the "choose session" menu, you can select this.

---


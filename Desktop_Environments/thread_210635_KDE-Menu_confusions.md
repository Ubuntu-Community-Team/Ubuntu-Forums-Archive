---
title: "KDE-Menu confusions"
date: 2006-07-07
forum: Desktop Environments
---

### Post by theFallen on 2006-07-07
Hi,

can somebody explain why I need the .local folder, while using KDE and while having the .kde folder.

How can I configure my system so, that the menu items are saved under .kde/share/applnk/AFolder/
Or for that matter that .local is not used.

How can I move the trashbin from .local/Trash to .kde/share/Trash and also be able to delete files into the bin :)

I managed, while trying to get some hdd space, to delete, without a chance to recover, the .local directory and I think there's more than just the menu items in it... ](*,)

---

### Post by theFallen on 2006-07-14
Someone, anyone?

---

### Post by aysiu on 2006-07-14
Try this: ```
mv ~/.local ~/.kde/.local
ln -s ~/.kde/.local ~/.local
```

---

### Post by theFallen on 2006-07-15
Thanks,

but I think

 ln -s ~/.kde ~/.local

is better?!

But still why is the .local Folder necessary?
And how do I configure the KDE Menu Editor correctly, so that it generates *.desktop Files in the appropriate Folder
e.g. ~./kde/share/applnk/System/

---

### Post by aysiu on 2006-07-16
Why is this better? ```
ln -s ~/.kde ~/.local
``` I thought you didn't want a local folder...

Do you understand what the command does? It makes a symbolic link from .kde to .local. That means the .local folder will appear to exist but not really exist. When you click on the .local folder, it will just take you to the .kde folder.

---

### Post by theFallen on 2006-07-16
Yes I do know what ln does.
But I have no ~/kde/.local, so with
ln -s ~/.kde/.local ~/.local
it would make no difference if I left .local in place.

I mentioned before I wrongly deletet my .local folder and I only know that there is at least a share Folder in it. So I mapped ~/.local/share folder with ~/.kde/share

Okay I see, my last command is misleading. But because I only know of share Folder in .local it made sense.

---

### Post by theFallen on 2006-08-08
Can someone please tell me what ~/.local/ contains?

---


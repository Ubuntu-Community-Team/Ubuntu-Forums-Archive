---
title: "Trying to unbind a key in KDE"
date: 2007-07-28
forum: Desktop Environments
---

### Post by KhaaL on 2007-07-28
A long time ago i have set the key win+E to open up my ~/ folder. The bad thing is that I cant remember how i did it, thus I don't know how to remove it (since i want to replace it with dolphin... love at first sight you know ;))

Anyone who can help me with finding this lost child?

---

### Post by GeneralZod on 2007-07-28
Does Win+E currently open ~ in Konqueror? If so, right-click on Konqueror in K-Menu->System, Edit Item, click on the Current Shortcut Key box and clear it with the cross symbol.  Post here afterwards to let us know if it worked!

---

### Post by KhaaL on 2007-07-28
It's not listed there at all. I've looked into every item and none have a shortcut assigned. Weird, because I thought that it was there were i bound the shortcut...

Do you think it's possible to make a search through the files in the .kde folder after the shortcut or something similiar?

---

### Post by GeneralZod on 2007-07-28
> **KhaaL said:**
> 
Do you think it's possible to make a search through the files in the .kde folder after the shortcut or something similiar?

Try:

```

grep -niR "Win+E" ~/.kde/share/config

```

---

### Post by KhaaL on 2007-07-28
YARR! found it in khotkeysrc and removed the shortcuts from it after backing it up. Restarted KDE and now my win+e is assigned to dolphin.

Thanks a bunch for the command, and for your help... You seriously made my day :-D

---

### Post by GeneralZod on 2007-07-28
> **KhaaL said:**
> YARR! found it in khotkeysrc and removed the shortcuts from it after backing it up. Restarted KDE and now my win+e is assigned to dolphin.

Thanks a bunch for the command, and for your help... You seriously made my day :-D

Glad to be of service :)

---


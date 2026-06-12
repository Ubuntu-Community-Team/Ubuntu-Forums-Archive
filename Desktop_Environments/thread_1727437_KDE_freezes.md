---
title: "KDE freezes"
date: 2011-04-12
forum: Desktop Environments
---

### Post by tadaskr on 2011-04-12
hello everybody.
I have strange problem with kde freezes. It always hapens when I downloading something at full speed of my connection. Freezes I mean I cant switch programs, all widgets stop working, can't even press K button (Kmeniu), because nothing happens. After finishing download it back to normal and all I press buttons of switch programs happening after that. Can anybody help?

P.S. I'm using Kubuntu 10.10. Tried upgrade KDE but same problem now

---

### Post by ankspo71 on 2011-04-12
Hi,
Sorry, I don't have any definite answers for you, but...

Which application are you using for the downloads when this happens? (Firefox, Chromium, Rekonq, Kget, Ktorrent, etc). This might help find an answer.

To me it sounds like whatever is doing the downloading is causing the CPU usage to be stuck at 100% until the download is finished. Try running the command 'top' in the terminal while you are downloading files to see if you notice any applications causing unusually high CPU and memory usage. 

Hope this helps.

---

### Post by tadaskr on 2011-04-12
it's no matter which program.. even I downloading updates. I CPU 100% I don't think so, because I can whatch videos without problem, and I can switch windows only with alt+tab

---

### Post by ankspo71 on 2011-04-12
Hi again,
Also, if you have enabled the "strigi" plugin for KDE's desktop search indexing, make sure you exclude your download location, and exclude the file types that don't need to be indexed, such as *.iso files. Using strigi to index these large or compressed files can cause very poor desktop performance, and probably even more so while downloading.
Hope this helps too.

Edit: I just read your second post so this won't help either.

---

### Post by tadaskr on 2011-04-12
it's really strange, because for example if i put speed limit lover thank maximum connction speed for downloading torrents no freezes no nothing. if i remove limit it's freezes

EDIT: is there possible to set download speed for everything? I mean updates, mozilla downloads youtube. and for everything

---

### Post by tadaskr on 2011-08-27
so, i tried 32-bit and same. it freezes. now i have very slow connection so to unfreeze it i should restart kdm or logout and login. anyone can help?

---


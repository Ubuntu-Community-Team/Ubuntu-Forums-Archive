---
title: "netbook version, cant remove plasma pages i have created"
date: 2010-05-23
forum: Desktop Environments
---

### Post by h2sammo on 2010-05-23
i made some desktops, some as folders, a new search page... now i cannot remove them. i am not give the option to remove any of them. 

also if i try to change the page type, a NEW page is created instead of a change occuring to existing page.

help please

---

### Post by h2sammo on 2010-05-24
wow... nothing?

---

### Post by maharaja2 on 2010-05-25
I had the same problem when i was using Kubuntu. 

Now i use Ubuntu Netbook Remix on my Netbook, it is much more stable. I still use Kubuntu on my desktop PC

---

### Post by h2sammo on 2010-05-25
i fixed by doing

```
bobby@aspireb:~$ sudo rm /home/bobby/.kde/share/config/plasma*
```

then reboot.

back to normal now. guys on kubuntuforums helped.

---


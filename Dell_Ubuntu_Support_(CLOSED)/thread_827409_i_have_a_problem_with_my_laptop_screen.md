---
title: "i have a problem with my laptop screen"
date: 2008-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vincent Martin on 2008-06-12
I have a dell latatude C800 and i hate it(actually love it) 
the following attachments show my problem i need someone to help me 
[ATTACH]73853[/ATTACH]  -what it should look like

[ATTACH]73854[/ATTACH]  -what it looks like

[ATTACH]73855[/ATTACH]  -my laptop-googled image
its not a hardwear problem because konoppix works on it but konoppix sux and i really want ubuntu on it could someone help me 
the install works file so does the live cd but i have this problem(problem shown on attachment)
thank you to every one who helps me.

---

### Post by pauper on 2008-07-20
Try setting a different video driver (VESA, for example):
```
sudo dpkg-reconfigure xserver-xorg
```

---


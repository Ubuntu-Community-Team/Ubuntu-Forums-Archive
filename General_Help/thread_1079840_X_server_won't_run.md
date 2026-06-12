---
title: "X server won't run"
date: 2009-02-24
forum: General Help
---

### Post by metalhead0010 on 2009-02-24
The X server won't run at all, and I'm using lynx.  I checked xorg.conf and it only says configured ****.  When I tried to reboot I got an error message that said no screens were configured.  Tell me if you need any more info and thanks in advance.  Never mind I fixed the xorg.conf but there are still no screens configured.

---

### Post by metalhead0010 on 2009-02-28
Bump

---

### Post by metalhead0010 on 2009-03-01
Bump

---

### Post by metalhead0010 on 2009-03-04
You were all so very helpful with my problem but I think I'll just use a different forum from now on!

---

### Post by Nepherte on 2009-03-04
You can regenerate a xorg file with:
```
sudo dpkg-reconfigure xserver-xorg
```

You should also be able to run X without a xorg.conf file (as in, delete it).

---

### Post by Firestem4 on 2009-03-04
Why don't you try reposting this question in the Desktop Enviroments section, as this specifically relates to It i'm sure you will get a better help.

There is a chance someone who does not check this sub-forum (General Help) may know the answer, as not every one of the 900,000 people who use this forum even use the Help sections.

And No, i'm sorry I don't know any answer to your question. The only thing I know about the x server is startx.

---


---
title: "system tray bar"
date: 2010-05-01
forum: Desktop Environments
---

### Post by ratcat on 2010-05-01
The bottom tray bar with open programs vanished. How to get it back. 
Thank you from a Apple user.

---

### Post by mac9416 on 2010-05-01
ratcat, right-click the bottom panel and click "Add to panel" (or something similar). Then choose the Window Switcher from the list that comes up.

---

### Post by mhgsys on 2010-05-01
Hi ratcat..  just for you I deleted my bottom panel in ubuntu 10.04.
When clicking new panel on my top panel, no new panel showed up.
So I lost my bottom panel.

Anyway;
To recover all the panels and restore them to original open up a terminal and typ;
```
gconftool-2 --recursive-unset /apps/panel
```

```
sudo service gdm restart
```

Panels should be back to original

---

### Post by ratcat on 2010-05-01
Thank you, works perfect

---

### Post by mhgsys on 2010-05-01
Which command did you follow up?
Mine or the one from mac9416 ?

I think it's useful and helpful to mention the name of the one your thanking, so other users who are having the same problem know which solution to follow.

In this case I guess both commands could work out, unless the bottom panel disappeared completely ; like I made it do in my case.... then the command I gave you will be the only one to  work out.

---

### Post by ratcat on 2010-05-01
used yours mhgsys,
worked great

---

### Post by mhgsys on 2010-05-01
Great to know it worked out for you. 

Thanks for letting me (and others) know.

As I mentioned before; 

Explaining which command(s) you followed/ gave  makes it easier for other users to find a solution to their problem.

---


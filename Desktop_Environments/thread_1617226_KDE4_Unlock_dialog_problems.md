---
title: "KDE4 Unlock dialog problems"
date: 2010-11-09
forum: Desktop Environments
---

### Post by ario on 2010-11-09
Hi guys,
I have two problems with KDE4 Unlock dialog:
[LIST=1]
[*]When I set one of KDE openGL screen savers, I can not see the unlock dialog after pressing any key. I must guess that there must be a dialog to enter my password and do so!
[*]Whenever I changed my keyboards layout, I can not change it back in unlock dialog, so I can not enter my password correctly, so I have no choice than hard reseting my PC, which is annoying!
[/LIST]
Please help me solve these issues.
Thanks:)

---

### Post by ario on 2010-11-14
Bump!:(

---

### Post by hellnest on 2010-11-14
> **ario said:**
> Bump!:(

What version you use?

---

### Post by ario on 2010-11-14
For now decided to run this:
```
sudo chown root:root /usr/lib/kde4/libexec/kcheckpass
sudo chmod 4755 /usr/lib/kde4/libexec/kcheckpass

```
which I took from [here]("http://kubuntuforums.net/forums/index.php?topic=3108318.0").
Will come here and write if it changed any thing.

---

### Post by hellnest on 2010-11-14
> **ario said:**
> For now decided to run this:
```
sudo chown root:root /usr/lib/kde4/libexec/kcheckpass
sudo chmod 4755 /usr/lib/kde4/libexec/kcheckpass

```which I took from [here]("http://kubuntuforums.net/forums/index.php?topic=3108318.0").
Will come here and write if it changed any thing.

Well ok keep inform about the result :)

---


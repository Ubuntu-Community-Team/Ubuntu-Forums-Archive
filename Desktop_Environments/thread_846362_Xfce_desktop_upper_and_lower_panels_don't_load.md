---
title: "Xfce desktop upper and lower panels don't load"
date: 2008-07-01
forum: Desktop Environments
---

### Post by PianycistHezaa on 2008-07-01
About a month ago, I installed Kubuntu 8.04 on my desktop computer, an eMachines T1090 that I've had since 2001. It has 128 MB of RAM. About two weeks ago, I installed an Xfce desktop environment in order to use fewer system resources than the KDE environment. It worked great until about a week ago. Now, when I log in using the Xfce desktop environment, the background image and the icons I've placed on the desktop appear, but the upper and lower panels do not load. It appears to happen only when I specifically log in: the upper and lower panels load just fine when my sister logs in on her (non-administrator) account.

I'm not sure how to go about fixing this, since it only seems to affect the Xfce desktop on my own user account.

---

### Post by TinkerJ on 2008-07-01
Have you tried removing your saved xfce session?

Try deleting ~/.config/xfce4-session folder.

---

### Post by mali2297 on 2008-07-01
Open the run dialog (Alt+F2) and type
```

xfce4-panel

```
Remember to save your session when you log out.

---

### Post by PianycistHezaa on 2008-07-01
> **mali2297 said:**
> Open the run dialog (Alt+F2) and type
```

xfce4-panel

```
Remember to save your session when you log out.

Thank you! It worked.

---


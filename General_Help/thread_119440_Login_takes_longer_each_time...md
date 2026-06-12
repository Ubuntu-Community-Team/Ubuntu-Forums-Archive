---
title: "Login takes longer each time.."
date: 2006-01-19
forum: General Help
---

### Post by JamesNorris on 2006-01-19
Logging in to KDE takes longer and longer each time I log in, the "restoring session" part of KDE startup. I first noticed this when I saw the %age going up in 9s, but now it seems to be going up in 5.5s taking longer each time I log in. 

Is there anything I can do to stop this? I have no need for old session data, if it's that that's causing the problem.

---

### Post by obibok on 2006-01-19
You're probably right in that something that got saved with your session is slowing down KDE startup.

Press *ALT+F2*, type **kcmshell kcmsmserver** and check *On Login -> **Start with an empty session***

---

### Post by JamesNorris on 2006-01-20
Yep, that sorted it, thanks :)

---


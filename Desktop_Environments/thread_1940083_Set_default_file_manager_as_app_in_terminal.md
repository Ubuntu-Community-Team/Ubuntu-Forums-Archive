---
title: "Set default file manager as app in terminal"
date: 2012-03-13
forum: Desktop Environments
---

### Post by adamrehard on 2012-03-13
I'm attempting to set mc (Midnight commander) as my default file manager, using preferred applications in Xfce, and it refuses to cooperate. Any thoughts? 
Thanks, Adam

---

### Post by wkrekik on 2012-03-13
Midnight-commander should run in a terminal. So the command to enter in preferred applications is :

/usr/bin/xfce4-terminal.wrapper -e mc "%s"

---


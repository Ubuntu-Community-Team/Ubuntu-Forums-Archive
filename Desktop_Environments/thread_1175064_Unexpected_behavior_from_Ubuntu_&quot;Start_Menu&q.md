---
title: "Unexpected behavior from Ubuntu &quot;Start Menu&quot; Panel"
date: 2009-05-31
forum: Desktop Environments
---

### Post by agjino on 2009-05-31
Hello,
Today I added IntelliJ IDEA to the programming submenu of the "Start Menu"-like Panel in Ubuntu 9.04. IDEA requires a variable, JDK_HOME, to be set, which I had set in bash.bashrc. However, when executing idea.sh from the panel it would not execute the scripts in bash.bashrc. I solved this by setting JDK_HOME inside idea.sh (for other newbies that come here from a Google search). But my question is, why isnt the panel shortcut executing bash.bashrc, and what IS it executing to set any variables?

Thank you.

---


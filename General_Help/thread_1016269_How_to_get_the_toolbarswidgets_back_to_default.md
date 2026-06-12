---
title: "How to get the toolbars/widgets back to default"
date: 2008-12-19
forum: General Help
---

### Post by Arukas on 2008-12-19
Hello-

  I've installed Kubuntu 64bit.  I accidently deleted the bottom panel. I put the panel back, and now there's nothing on it.  

Does anyone know how to get the default panel with all the widgets back on it?  This is the first time I am using Kubuntu, other wise I could just recreate everything.

---

### Post by TheUnabeefer on 2008-12-19
> **Arukas said:**
> Hello-

  I've installed Kubuntu 64bit.  I accidently deleted the bottom panel. I put the panel back, and now there's nothing on it.  

Does anyone know how to get the default panel with all the widgets back on it?  This is the first time I am using Kubuntu, other wise I could just recreate everything.

If you have KDE4, I believe the file is ~/.kde/share/config/plasma-appletsrc  Just rename and/or remove the file altogether (being logged out of your session... I usually Ctrl-F2 into a console window) and then when you log in, it will create a new default plasma layout as if it's your first time.

---


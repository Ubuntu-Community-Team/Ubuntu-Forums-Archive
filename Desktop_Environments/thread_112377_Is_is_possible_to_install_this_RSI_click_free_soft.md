---
title: "Is is possible to install this RSI click free software under gnome?"
date: 2006-01-04
forum: Desktop Environments
---

### Post by Jaylon on 2006-01-04
Hello. Is it possible to install [this]("http://www.mousetool.com/ergonomic-software-for-linux.html") click free KDE software in regular Ubuntu? Sorry if this is a silly question, but I don't really have any idea.

Otherwise, has anyone found any click free software for Ubuntu?

Thanks,

Jay

---

### Post by GeneralZod on 2006-01-04
```

sudo apt-get install kmousetool

```

should do the trick! :D  After installation, you can find it in the Utilities menu (possibly under the More Applications sub-menu), or press Alt+F2 and enter 

```

kmousetool

```

as the app to run.

If you have no other KDE apps installed, then this will download and install quite a lot of KDE libraries, I'm afraid.

---

### Post by Jaylon on 2006-01-04
Nice one mate. My carpal tunnel thanks you. I don't suppose you have the instructions anywhere do you? The help button does not work.

Jay

---

### Post by GeneralZod on 2006-01-04
[QUOTE=Jaylon]Nice one mate. My carpal tunnel thanks you. I don't suppose you have the instructions anywhere do you? The help button does not work.

Jay[/QUOTE]

Hmmm...try

```

sudo apt-get install khelpcenter

```

Edit:

Also, check this out:

[http://docs.kde.org/stable/en/kdeaccessibility/kmousetool/](http://docs.kde.org/stable/en/kdeaccessibility/kmousetool/)

---

### Post by Jaylon on 2006-01-04
Cheers mate. That's brilliant.

ATB, Jay

---


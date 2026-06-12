---
title: "gtk dialogs slow in kde"
date: 2007-11-13
forum: Desktop Environments
---

### Post by arsham on 2007-11-13
Hi
The gtk dialogs are so slow in KDE
Whenever I want to open/save something in firefox or gimp , it takes almost 10 seconds to open , but every dialogs in KDE are running so fast

KDE 3.5.8
Kubuntu gutsy

---

### Post by cookies on 2007-11-13
You could run the application from a terminal, and see if there are any errors, or you could try [http://kde-look.org/content/show.php/KGtk+%28Use+KDE+Dialogs+in+Gtk+Apps%29?content=36077](http://kde-look.org/content/show.php/KGtk+%28Use+KDE+Dialogs+in+Gtk+Apps%29?content=36077)

Which allows you to use KDE dialogs in some apps if you start them with, for example:
```
kgtk-wrapper gimp
```

---

### Post by arsham on 2007-11-14
Thank you for reply
There is no error in the terminal

Is there any possibilities that gtk applications need to resolve something? I had this problem before , after setting localhost in resolve.conf problem desapeared.

But I have set localhost in resolve.conf already

This is driving me crazy

---


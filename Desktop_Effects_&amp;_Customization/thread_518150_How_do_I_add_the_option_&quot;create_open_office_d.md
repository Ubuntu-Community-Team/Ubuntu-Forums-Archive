---
title: "How do I add the option &quot;create open office document&quot; when right clicking?"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Christof999 on 2007-08-05
Hello,

Most distributions I have used with KDE have Open Office Documents listed in the options to create a document when right clicking. However since I installed KDE base and it doesn't have it.

What Id like to know how to do is add items to the Create New sub menu. For example, say I am on the desktop, and I want to start writting an open office document, I right click, create new, OO Document.

How do I add that ?

Thanks
Christopher.

---

### Post by bakster on 2007-08-05
Create folder named Templates (case sensitive!!) in your home folder.Create blank Open Office document and save it in Templates folder.You may need to restart Nautilus:
alt+F2 ,type in dialog box
 ```
nautilus -q
```again, alt+F2,type
```
nautilus
```After that,when you create new office document using right click it will be copied from your Templates folder.That means it doesn't need to be empty(it can contain what ever you like).More info [_here_]("http://linux.about.com/library/gnome/blgnome6n6h.htm")

---

### Post by Christof999 on 2007-08-05
Thanks,,,, but I am using KDE. How can I do it for that ?

---

### Post by bakster on 2007-08-05
Ops, sorry my bad .Maybe [this]("http://legroom.net/2007/04/20/adding-custom-actions-kde-context-menus") ,[ this]("http://liquidweather.net/howto/index.php?id=89") and [this]("http://www.kde-look.org/index.php?xcontentmode=287") will help you.You need to create a  .desktop file and place it in ~/.kde/share/apps/konqueror/servicemenus/

---

### Post by Christof999 on 2007-08-08
> **bakster said:**
> Ops, sorry my bad .Maybe [this]("http://legroom.net/2007/04/20/adding-custom-actions-kde-context-menus") ,[ this]("http://liquidweather.net/howto/index.php?id=89") and [this]("http://www.kde-look.org/index.php?xcontentmode=287") will help you.You need to create a  .desktop file and place it in ~/.kde/share/apps/konqueror/servicemenus/

Thanks..

I am not sure what to put inside the .desktop file... could someone help me by posting the contents of their OO create new service menus ?

Thanks again
C

---

### Post by Christof999 on 2007-08-08
Anyone ?

Ive been trying to get this for weeks. Its seriously hurting my productivity. Can someone please post the contents of their OO service menu .desktop file ?

Thanks
C

---


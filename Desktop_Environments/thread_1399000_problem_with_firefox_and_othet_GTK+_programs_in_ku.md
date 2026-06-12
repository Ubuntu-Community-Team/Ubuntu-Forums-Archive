---
title: "problem with firefox and othet GTK+ programs in kubuntu"
date: 2010-02-05
forum: Desktop Environments
---

### Post by farzadbashtani on 2010-02-05
hello every one

I installed kubuntu 9.10 on my VAIO laptop

and then I installed my graphic card driver successfully

but I have a big problem with my firefox and other GTK+ programs that I run on my KDE

I installed gnome too but it didnt fixed the problem

ohhh .... I was forgetting to tell you what my problem is

all the sizes in those programs are BIG .... all buttons , textboxes .... every thing is big .... even the fonts 

firefox loads the webpages so bad ... with big fonts and materials....

PLEASE guys .... tell me what to do .....

thanks a lot

My Laptop Model: SONY AR 870 NB

---

### Post by lovinglinux on 2010-02-05
Try [this](http://ubuntuforums.org/showpost.php?p=8523373&postcount=5).

---

### Post by farzadbashtani on 2010-02-05
hi

I tried to install gtk-qt-engine with apt-get

and it was the result


> eading package lists... Done
Building dependency tree
Reading state information... Done
Package gtk-qt-engine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kcm-gtk
E: Package gtk-qt-engine has no installation candidate


then I searched for this package in packages.ubuntu.com for karmic but nothing was there.....

what do you recommend?

---

### Post by cb951303 on 2010-02-05
I think it should be already installed. go to your KDE theme settings and set your GTK theme to KDE.

See the first option on the screenshot.

[IMG]http://rafal.zelazko.info/wp-content/uploads/2009/10/kde4_gtk_styles_and_fonts.png[/IMG]

---

### Post by farzadbashtani on 2010-02-05
no .... its not there ......

I attached an screenshot ..... you can see it

and i dont know what to do 

please help   ( so sorry for my bad english )

---

### Post by lovinglinux on 2010-02-05
> **farzadbashtani said:**
> no .... its not there ......

I attached an screenshot ..... you can see it

and i dont know what to do 

please help   ( so sorry for my bad english )

I don't have it either.

---

### Post by wojox on 2010-02-05
[gtk-qt-engine]("http://code.google.com/p/gtk-qt-engine/downloads/list")

---

### Post by captaincrook on 2010-02-06
Install kcm-gtk and you should get that module (whats in the image a few posts above) in the System Settings. Extract themes and placing them into the /usr/share/themes directory makes appear in the drop down list.

I would suggest [this](http://www.kde-look.org/content/show.php/Oxygen-Molecule+KDE+%26+GTK%2B+unified+theme?content=103741) theme when using Kubuntu Karmic.

---

### Post by schnelle on 2010-02-06
In System Settings, under fonts tab there is an option "Force fonts DPI: 96 DPI"

After choosing that option all my fonts in firefox became "normal" (not big).

---

### Post by farzadbashtani on 2010-02-06
THANKS A LOT ......

PROBLEM SOLVED ......


thanks a lot friends ....

---

### Post by binnaeus on 2010-04-28
> **schnelle said:**
> In System Settings, under fonts tab there is an option "Force fonts DPI: 96 DPI"

After choosing that option all my fonts in firefox became "normal" (not big).

Yep, that was enough in my case too. Thanks :)

---


---
title: "Themes"
date: 2007-10-09
forum: Desktop Environments
---

### Post by nami on 2007-10-09
Hello

If Ii go to system > preferences > themes, it shows an install button, which is telling me that new themes can be installed.  Where can I get some new themes?

I have tried gnome-looks and downloaded gdm and gdk themese but they do not work?

---

### Post by chrisTGc on 2007-10-09
Hi,

Gnome themes can be got from several sources.Gnome themselves have art.gnome.org with many themes backgrounds and so on.Try Googling that.

If you download a new theme then it can just be dragged and dropped into the system>preferences>themes window or click install theme from there and navigate to your downloaded theme file.

Now once you have installed a theme you may find it is not entire theme in itself.For instance it may not include icons and it will not be listed in the main theme window.But it is still available if you select a general theme and then click customise.You may find your newly installed theme only offers a new Window Border and Controls which are available from those respective tabs  but that is plenty to change things around. And then you can select the icons to be used with the new theme and so on.

If you have downloaded and installed a  GDM theme then this will only allow you to change the main 'Log In' background and will be available from System>Administration>Login Window. 

Hope this helps,Chris.

---

### Post by JBAlaska on 2007-10-10
"GNOME Art 0.2" can fetch themes and backgrounds for you as well.

---

### Post by 3rdalbum on 2007-10-10
GDM themes are installed into a different place: System > Administration > Login Window

When you download themes, the .tar.gz file IS the file you need to install; so DON'T unpack it. Tell the Themes panel to install that actual .tar.gz file.

When you download themes that are not full themes (i.e. they just do the window borders, or they just do the controls), you need to then select Customise... in the Themes panel and choose the Window theme, the Controls theme, etc.

Just so you know, GDM is the login screen, Metacity is the window manager, Emerald is the window borders on Compiz, and GTK is the buttons, scrollbars, menus etc.

---

### Post by nami on 2007-10-14
i just downloaded a gtk 2 theme from gnome look and when i dragged dropped it into the theme window, it said "invalid file format"...

where do i get more of these type of themes?

see attached image.

---

### Post by chrisTGc on 2007-10-14
Hi,

 [http://art.gnome.org/](http://art.gnome.org/)

Assume you did not extract the files before dropping them in the themes window?,leave them as tar.gz before doing so.Could be a duff file or one intended for something else eg fluxbox.Look over to the right of the above link for themes.


Chris

---

### Post by aysiu on 2007-10-14
Can you post a link to the offending theme?

---

### Post by nami on 2007-10-15
Absolutely.

I did not extract the files

One of the themes I tried was this:
[http://www.gnome-look.org/content/show.php/Complete+Green+Theme+pack?content=66491&PHPSESSID=e5b8aa48e42780a16c637a69e8a5832c](http://www.gnome-look.org/content/show.php/Complete+Green+Theme+pack?content=66491&PHPSESSID=e5b8aa48e42780a16c637a69e8a5832c)

---

### Post by misfitpierce on 2007-10-15
One thing you can do is go under System - Admin - Synaptic Package Manager

Search gtk2

Install every gtk2 theme ENGINE in there. Very small install for all and every GTK2 theme should work :) lol

---

### Post by nami on 2007-10-15
> **misfitpierce said:**
> One thing you can do is go under System - Admin - Synaptic Package Manager

Search gtk2

Install every gtk2 theme ENGINE in there. Very small install for all and every GTK2 theme should work :) lol

interesting approach!!!

i'll try it tonight. :D

---

### Post by aysiu on 2007-10-15
> **nami said:**
> Absolutely.

I did not extract the files

One of the themes I tried was this:
[http://www.gnome-look.org/content/show.php/Complete+Green+Theme+pack?content=66491&PHPSESSID=e5b8aa48e42780a16c637a69e8a5832c](http://www.gnome-look.org/content/show.php/Complete+Green+Theme+pack?content=66491&PHPSESSID=e5b8aa48e42780a16c637a69e8a5832c)
That's a theme pack.

Those *do* need to be unpacked, because they aren't themes but *collections* of themes.

---

### Post by nami on 2007-10-15
ok, i downloaded this one: [http://www.gnome-look.org/content/show.php/imetal?content=63734](http://www.gnome-look.org/content/show.php/imetal?content=63734)
extracted it and it game me a folder with lots of folders in it.  i have no idea what to do next...


help.

---

### Post by chrisTGc on 2007-10-15
Hi

The file you have containing many themes i should think you will have to copy each theme folder to /home/your-user-name/.themes please note thats a hidden file as is indicated by the . in front of its name.In Nautilus click view,tick hidden files and scroll to .themes.Try copy each of the theme folders to there.

Best Wishes Chris.

---

### Post by aysiu on 2007-10-15
And if it's an icon theme, it'll have to be extracted and copied to /home/*username*/.icons instead of /home/*username*/.themes

---

### Post by nami on 2007-10-16
I'll try that asap.

---


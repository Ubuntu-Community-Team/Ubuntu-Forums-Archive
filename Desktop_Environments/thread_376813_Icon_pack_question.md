---
title: "Icon pack question"
date: 2007-03-05
forum: Desktop Environments
---

### Post by blackstealth007 on 2007-03-05
I downloaded a icon pack with folders inside that are different sizes. An example is the following,  /32*32/apps (there is also devices, filesystems, and stock)/"icon images are in this part"

How would i go about using them? I am new at this, and so I dont know where i would need to put them in order to be able to use them.

---

### Post by ardchoille42 on 2007-03-05
> **blackstealth007 said:**
> I downloaded a icon pack with folders inside that are different sizes. An example is the following,  /32*32/apps (there is also devices, filesystems, and stock)/"icon images are in this part"

How would i go about using them? I am new at this, and so I dont know where i would need to put them in order to be able to use them.

What you downloaded is an icon theme. There are two main places to unpack an icon theme.

If you want the icon theme to be available only to your user, unpack the icon theme into ~/.icons.

If you want the icon theme to be available to all users, unpack the icon theme into /usr/share/icons, you'll need sudo to do this since it is a system directory.

Once you have them unpacked, open System -> Preferences -> Themes, go to the icon tab and choose the new icon theme.

---

### Post by mcduck on 2007-03-05
The easiest way is to open the Theme Manager in System/Preferences/Theme and then just drag&drop the theme package into the Theme Manager window. (do not unpack the theme yourself). This will install the theme for current user.

---

### Post by ComplexNumber on 2007-03-05
> **mcduck said:**
> The easiest way is to open the Theme Manager in System/Preferences/Theme and then just drag&drop the theme package into the Theme Manager window. (do not unpack the theme yourself). This will install the theme for current user.
best to unpack them yourself and place them either in .icons or /usr/share/icons. as an example, try installing [this]("http://gnome-look.org/content/show.php?content=46010") icon theme in gnome-theme-manager. you will notice that, even though it contains about 10 different themes, it will only install 1 of them. other packages that contain more than 1 theme bring up errors.

---

### Post by mcduck on 2007-03-06
> **ComplexNumber said:**
> best to unpack them yourself and place them either in .icons or /usr/share/icons. as an example, try installing [this]("http://gnome-look.org/content/show.php?content=46010") icon theme in gnome-theme-manager. you will notice that, even though it contains about 10 different themes, it will only install 1 of them. other packages that contain more than 1 theme bring up errors.
well, that's true when the package contains more than  one theme. But most of them don't, so installing with the theme manager works about 9 times out of ten ;)

---

### Post by ComplexNumber on 2007-03-06
> **mcduck said:**
> well, that's true when the package contains more than  one theme. But most of them don't, so installing with the theme manager works about 9 times out of ten ;)
probably less than that. many gtk/metacity themes these days also include the beryl/compiz theme too, and sometimes a panel pixmap etc. thats why i always unzip them myself so that i can see what else has been included.

---

### Post by mcduck on 2007-03-06
> **ComplexNumber said:**
> probably less than that. many gtk/metacity themes these days also include the beryl/compiz theme too, and sometimes a panel pixmap etc. thats why i always unzip them myself so that i can see what else has been included.
Yeah, that's true for GTK and Metacity themes. But most icon packs still only have one icon theme :)

Anyway, both ways are almost as easy. I also usually check what's inside the package before I install it, so unzipping it into correct folder wouldn't be much of extra job.

---

### Post by ardchoille42 on 2007-03-06
> **ComplexNumber said:**
> best to unpack them yourself and place them either in .icons or /usr/share/icons. as an example, try installing [this]("http://gnome-look.org/content/show.php?content=46010") icon theme in gnome-theme-manager. you will notice that, even though it contains about 10 different themes, it will only install 1 of them. other packages that contain more than 1 theme bring up errors.

This is why I never recommend using the theme manager installer, it doesn't do a very good job consitently.

---


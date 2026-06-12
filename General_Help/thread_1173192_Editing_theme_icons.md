---
title: "Editing theme icons"
date: 2009-05-29
forum: General Help
---

### Post by Muscovy on 2009-05-29
I was trying to use the Clearlooks theme, but replace the folder icons with the Human ones, but I do not have permission. How would I go around that?

---

### Post by ActiveFrost on 2009-05-29
You can change your theme but have no permissions to change it's icon set ? 
Click on your theme -> Customize -> Icons .. you don't have a permission to this area ? :o

---

### Post by randiroo76073 on 2009-05-29
If that doesn't work you can open a terminal and type or copy/paste ```
gksu gnome-appearance-properties %F
``` and change relevant files that way. But you should already have permission to change them thru menu/system/preferences/appearance

---

### Post by Mirages on 2009-05-29
> **Muscovy said:**
> I was trying to use the Clearlooks theme, but replace the folder icons with the Human ones, but I do not have permission. How would I go around that?

Maybe your user account doesn't have administrative abilities 
-to check, try going to System>Administrator>Users and Groups. 
-Click on your user account then got to Properties>User Privledges
-is the second item on the list "Administer the System" checked?

If not you can exit properties so you are back to the users and groups window click Unlock at the bottom provide your root pw  and re-enable it.

Just a guess based on the fact that you didn't have permission

hope you figure it out!

---

### Post by CatKiller on 2009-05-29
For general information about changing files outside your Home folder, you might find [this page]("https://wiki.ubuntu.com/RootSudo") useful.

For your particular task, you might want to just copy the icon files you want to use into the ~/.icons directory (Ctrl-H to show hidden files, create it if it isn't there already) to create a whole new theme. It's relatively straightforward. Icons that you can't be bothered to specify can be handled automatically by specifying another theme in the Inherits= line of the index.theme file.

---

### Post by Muscovy on 2009-05-29
> **CatKiller said:**
> For general information about changing files outside your Home folder, you might find [this page]("https://wiki.ubuntu.com/RootSudo") useful.

For your particular task, you might want to just copy the icon files you want to use into the ~/.icons directory (Ctrl-H to show hidden files, create it if it isn't there already) to create a whole new theme. It's relatively straightforward. Icons that you can't be bothered to specify can be handled automatically by specifying another theme in the Inherits= line of the index.theme file.
I'll try that.

Edit: Wait, I never saw -> Customize -> Icons before. Still, I'll find creating a new theme useful. I've been intending to do that sooner or later...

---

### Post by CatKiller on 2009-05-29
> **Muscovy said:**
> Still, I'll find creating a new theme useful. I've been intending to do that sooner or later...

You might find [this page]("http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html") useful as background. I think there are some tutorials on gnome-look or something, too (couldn't find it, but [here's another one]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes")). Mostly you'll pick it up if you just copy the way that a theme that works does things.

---


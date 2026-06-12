---
title: "How do I install themes"
date: 2009-01-24
forum: General Help
---

### Post by Shadow12313 on 2009-01-24
I know this is a silly question but I don't really know the answer to it.  How do I install GTK themes?

---

### Post by oldos2er on 2009-01-24
Easiest way is to drag & drop the tar.gz file into the Appearance Preferences 'Theme' window.

---

### Post by Shadow12313 on 2009-01-24
Are there any other ways?

---

### Post by Gondee on 2009-01-24
Use Emerald

sudo apt-get install emerald

---

### Post by oldos2er on 2009-01-24
You can fiddle around in /usr/share/themes, but I don't recommend doing that. What exactly are you looking for?

---

### Post by Shadow12313 on 2009-01-24
> **Gondee said:**
> Use Emerald

sudo apt-get install emerald

Thanks emerald works great! :)

---

### Post by blackened on 2009-01-24
> **Shadow12313 said:**
> Thanks emerald works great! :)

Um, great, but emerald has absolutely nothing to do with the question you began this thread with.

You can install new gtk themes by unzipping them, then dropping the folder in ~/.themes (subdirectory of your user directory) or /usr/share/themes (requires superuser privileges).

If you install a theme to ~/.themes, then only you are able to use it. This is what happens by default when you install by drag-and-drop into the "Appearances" dialog.

If you install a theme to /usr/share/themes, then it will be available to all users.

---

### Post by Shadow12313 on 2009-01-25
> **blackened said:**
> Um, great, but emerald has absolutely nothing to do with the question you began this thread with.

You can install new gtk themes by unzipping them, then dropping the folder in ~/.themes (subdirectory of your user directory) or /usr/share/themes (requires superuser privileges).

If you install a theme to ~/.themes, then only you are able to use it. This is what happens by default when you install by drag-and-drop into the "Appearances" dialog.

If you install a theme to /usr/share/themes, then it will be available to all users.

Whenever I drag and drop it, it doesn't install the icons.
Any ideas?

---

### Post by blackened on 2009-01-25
Install them manually. Unzip the file and drop the resulting folder in /home/*yourusername*/.icons

---

### Post by Shadow12313 on 2009-01-31
> **blackened said:**
> Install them manually. Unzip the file and drop the resulting folder in /home/*yourusername*/.icons

Ok, thanks :)

---


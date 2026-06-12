---
title: "what to do with tar.gz"
date: 2009-01-23
forum: General Help
---

### Post by banana jama on 2009-01-23
i've downloaded a file thats tar.gz. how do i install it in ubuntu?

---

### Post by sowelie on 2009-01-23
A tar.gz is like a zip file, it's an archive.  What is it that you downloaded?

---

### Post by banana jama on 2009-01-23
it was an ubuntu theme from gnome-look.org. but in general how to you install tar.gz files?

---

### Post by Iowan on 2009-01-23
[Here]("http://ubuntuforums.org/archive/index.php/t-805102.html") is a similar topic.  Depending on the program, the repositories may have the same thing - already packaged.

---

### Post by sowelie on 2009-01-23
It depends on what is inside the file, a tar.gz can contain anything, you can make one yourself.  To install a theme...execute this:

```
sudo tar xzvf name-of-file.tar.gz --directory=/usr/share/themes
```

That is only for GTK themes though.  Like I said, depending on what is in the file you install things in different ways.

---

### Post by Yashiro on 2009-01-23
Open the Appearance/theme manager window. Drop the tar.gz onto it.

---

### Post by banana jama on 2009-01-23
thanks using Iowan link i found this link it help alot. [http://ubuntuforums.org/showthread.php?t=500020]("http://ubuntuforums.org/showthread.php?t=500020")

i can't seem to mark this thread as solved

---

### Post by sowelie on 2009-01-23
> **Yashiro said:**
> Open the Appearance/theme manager window. Drop the tar.gz onto it.

The problem with installing themes this way is that when you open programs as administrator, the theme isn't available because the theme manager installs the them in your home directory.

---

### Post by Yashiro on 2009-01-23
That is correct.

---

### Post by sowelie on 2009-01-24
Is there an idea to fix that on brainstorm?  I think that the theme manager should automatically install the themes in /usr/share/themes.

---


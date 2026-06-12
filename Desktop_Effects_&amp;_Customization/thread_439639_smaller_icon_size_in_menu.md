---
title: "smaller icon size in menu?"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by Bashed on 2007-05-10
can someone please explain how to make the icons in the menu smaller? 

Using ubuntu feisty fawn / gnome/beryl

---

### Post by kpolice on 2007-05-10
Paste the following in your .gtkrc-2.0 file, if it doesn't exist then create it.

```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=24,24:gtk-small-toolbar=16,16:gtk-button=16,16" 
```

Adjust the rest of the sizes if you want.

---

### Post by Bashed on 2007-05-10
I'm new to linux. Where is that file, or where should it go?

---

### Post by kpolice on 2007-05-10
In your home

---

### Post by Bashed on 2007-05-11
Odd. I placed it there in /home/user/ with that file name, rebooted and they are still the same size

---

### Post by kpolice on 2007-05-11
Are you sure you named it .gtkrc-2.0 , a dot is the first character.

Another reason could be that your GTK theme defines the size of the icons.

---


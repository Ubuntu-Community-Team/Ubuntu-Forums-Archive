---
title: "Gdesklets"
date: 2005-01-29
forum: Desktop Environments
---

### Post by Smash on 2005-01-29
Hello, i have a problem with gdesklets. This is the error:

```

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)

```

---

### Post by bob k on 2005-01-29
[QUOTE=Smash]Hello, i have a problem with gdesklets. This is the error:

```

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)

```[/QUOTE]

It's just telling you that the version of python does not match what the desklet was looking for. It is just a warning not an error. In other words don't worry about it.

---

### Post by Mattias on 2005-01-30
Hello
I see the same error message ... the problem is that the desklet doesn´t do anything after that error message (or warning ..).  I should mention that i´m running warty . Am I missing something or do I need some other package installed. Other posts in this forum seems to discuss problems with the Hoary release. A problem mentioned in these posts  is that python gnome extras is needed and I can´t find that package for python 2.3 which is the one I have installed..

grateful for any assistance 
/newbie mattias

---

### Post by Smash on 2005-01-30
Thanks.
I tried, and it works good.

Bye

---

### Post by Mattias on 2005-01-30
sorry, too quick before asking 
found this... [http://ubuntuforums.org/showthread.php?t=3012](http://ubuntuforums.org/showthread.php?t=3012)

---


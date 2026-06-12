---
title: "Compiz-Extra - Installed But How to Use Them?!"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by maher_79 on 2007-06-11
Hi all,
I just installed Compiz-Extra package successfully but don't see any extra effects!  I guess i don't know where to find them and how to activate them if they are not activated.

Please any help would be greatly appreciated :)

---

### Post by kevinbeard on 2007-06-12
If you only have the basic "Desktop Effects" like me,  i.e. you haven't installed Beryl or Compiz yourself then the way I did it was to use gconf-editor.

Go to apps->compiz->general->allscreens->options

and add the name of the plugin you want to activate to the list in active_plugins

---

### Post by maher_79 on 2007-06-12
> **kevinbeard said:**
> If you only have the basic "Desktop Effects" like me,  i.e. you haven't installed Beryl or Compiz yourself then the way I did it was to use gconf-editor.

Go to apps->compiz->general->allscreens->options

and add the name of the plugin you want to activate to the list in active_plugins

i'm at work now using windows [-X but i will sure try this when i get home!

I was trying to install gnome-compiz-manager-extra but was getting the error below:

```
[COLOR="Red"]The following packages have unmet dependencies:
  gnome-compiz-manager-extra: Depends: libgnome-compiz-manager which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-compiz-manager-extra [Not Installed][/COLOR]Score is -10001

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If your way works then that would be great.  It looks like the gnome-compiz-manager-extra packages is broken.  Anyone know anything about this?!

---


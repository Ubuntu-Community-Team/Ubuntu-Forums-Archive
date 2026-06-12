---
title: "Animated Progress bar in Gnome"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Optimal Aurora on 2005-11-04
How can you get your progress bar to re-animate when you somehow accidently turned it of? I don't know how I turned it off, but now it doesn't show that cute animated effect that it once did. Any help on this subject is greatly appreciated. And any help to make this occur in Fedora is also greatly appreciated, since I have a linux class and the animated effect doesn't work in Fedora.

---

### Post by psychicdragon on 2005-11-04
Did you recently change themes by any chance?

Clearlooks based themes have a line in their gtkrc file that controls what progressbar style they use.

To change it, open the file: **/path/to/theme/gtk-2.0/gtkrc**

Look for a section like this:
```
  engine "clearlooks" 
  {
    sunkenmenubar     = 1
    menuitemstyle     = 1
    listviewitemstyle = 0
    **progressbarstyle  = 0**
  }
```
A value of 0 is the animated progressbar, 1 is the flat one.

---

### Post by iimess on 2005-11-04
[http://ubuntuforums.org/showthread.php?t=76571](http://ubuntuforums.org/showthread.php?t=76571)

no answer yet

---

### Post by Optimal Aurora on 2005-11-04
Yes I had recently change themes, but I am currently using clearlooks and that could be the reason.

---

### Post by Optimal Aurora on 2005-11-04
Thanks it all works pretty well too.  Thank you...

---


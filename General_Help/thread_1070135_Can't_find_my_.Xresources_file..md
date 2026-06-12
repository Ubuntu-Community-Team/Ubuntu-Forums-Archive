---
title: "Can't find my .Xresources file."
date: 2009-02-14
forum: General Help
---

### Post by PoopLoops on 2009-02-14
What I am trying to do is see if I can customize individual applications because I like having a dark theme and dark text on a dark background hurts my eyes even more.  I was told to look for my .Xresources (or .Xdefaults, which I can't find either) file.

I found *something* in /etc/X11, but it's another directory and all it has is x11-common in it.  I'm using Ubuntu 8.04.

Also, I can't find a .Xresources in my home folder, either.  This confused me even more.  I am using Compiz if it matters.

Thanks

---

### Post by x1a4 on 2009-02-14
Hi,
.Xresources is used to change Xorg compiled-in defaults.  Don't use it unless you know exactly what you are doing.  

To change defaults for X applications use .Xdefaults .  Create it and save to ~

To enable your changes run: 
```
xrdb -merge ~/.Xdefaults
```

---

### Post by PoopLoops on 2009-02-14
Okay, cool.  Thanks!  Now is there somewhere that I could find out what it is I can put into that file and what that would do?  What I mean is, how do I tell program X to run settings Y and program A to run settings B?  I don't know the syntax.

I found some examples for other programs, like XTerm or something, but I'd just like some sort of manual page or syntax list or whatever so I can figure out what to do with my specific apps.

---

### Post by ichilton on 2009-02-27
Hi,

Is it possible to get things to read .Xdefaults automatically without having to run that merge command after every change?

Also, if you remove something from Xdefaults it doesn't get removed because of the merge I assume....how can you get around that?

Thanks

Ian

---


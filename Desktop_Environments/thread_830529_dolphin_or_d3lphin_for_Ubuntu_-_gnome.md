---
title: "dolphin or d3lphin for Ubuntu - gnome"
date: 2008-06-15
forum: Desktop Environments
---

### Post by jimmy the saint on 2008-06-15
I am running Ubuntu Hardy Heron and I am wondering if the newer Dolphin file manager would be ok to run, of if I should stick with d3lphin, which is the version that keeps the 3.5 code alive.  Or would it make a difference?

Also, on a side note, if I install one and don't like it, is there a command to get rid of all the libraries and extra stuff that get installed along with it?  

Thanks

JTS

---

### Post by angry_johnnie on 2008-06-16
The easiest way to remove something along with all its dependencies is to install it with aptitude.

like:
```

sudo aptitude install something
```

will install something, as well as something's dependencies.

and then
```

sudo aptitude remove something
```

will get rid of something and its dependencies.

I would advise to stay away from kde4 until it's stable.

Other than that, I think it would be too much of a pain to run dolphin, or any other qt app, in GNOME.  Why don't you just install kde-core, or kubuntu-desktop?

But then, if you really want to, you can.  Just use aptitude, and then it will be easier to get rid of things, if you decide you no longer want them.

---


---
title: "Properties changing for multiple Launcher instances"
date: 2008-08-08
forum: Desktop Environments
---

### Post by rschigas on 2008-08-08
Hi everyone,

Just switched to Ubuntu and I'm now learning Gnome.  I have two Firefox launchers in my Gnome panel, one for general browsing and one for my development environment.  One I created by copying from the Applications menu, and the other I created from scratch using "Add to panel > Create custom launcher".

The problem is that every time I log in, both of them have the same properties.  It appears that the properties of the first one get copied onto the second one I created.

Here are their properties as I originally set them up:

```

  Type: Application
  Name: Firefox
  Command: firefox

  Type: Application
  Name: Dev instance
  Command: firefox %U http://127.0.0.1:8080/dev http://localhost:8080/dev
```

Any ideas how I can fix this to have multiple instances of an application in the panel?

Thanks,
Roland

---


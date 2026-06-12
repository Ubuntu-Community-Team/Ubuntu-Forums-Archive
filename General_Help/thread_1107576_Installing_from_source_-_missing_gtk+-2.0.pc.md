---
title: "Installing from source - missing gtk+-2.0.pc"
date: 2009-03-26
forum: General Help
---

### Post by WhiskyChris on 2009-03-26
When trying to install a program from source it returns an error that it can't find a certain package:

```
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```

So after searching in the package manager for something I thought would solve this, I found libgtk2.0-dev, version 2.14.4-0ubuntu1. On marking for installation and accepting its dependencies however, it returns an error about unresolvable dependencies:

```
libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.14.4-0ubuntu1) but 2.14.4-0ubuntu2 is to be installed
```

Any ideas about how I should continue?

Bump: I notice that I have libgtk2.0-0 version xxxubuntu2 installed. I can Package-Force Version to change that to xxxubuntu1 and not it doesn't squawk when I try to install libgtk2.0-dev version xxxubuntu1. Anyone know what the difference between version names such as these is? I notice ubuntu1 is labeled (Intrepid) which is what I use, while ubuntu2 is labeled (now).

I hope doing this won't break anything...

---

### Post by mc4man on 2009-03-27
You currently have libgtk2.0-0  - 2.14.4-0ubuntu2 which you got from Intrepid - proposed.
Safest, easiest way now is to enable Intrepid - proposed in your software sources, reload and then apt-get install libgtk2.0-dev.
Then I'd probably go back and disable proposed in software sources.

---

### Post by WhiskyChris on 2009-03-27
Thanks - doing this worked and what I was originally trying to install also now installs (pretty much) happily!

---


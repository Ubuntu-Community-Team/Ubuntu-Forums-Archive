---
title: "Midori prefs missing"
date: 2008-12-30
forum: General Help
---

### Post by dbbolton on 2008-12-30
There are several options in Midori that I can't alter. I attached a few screenshots. Anyone know why?

---

### Post by dbbolton on 2008-12-31
-

---

### Post by fragos on 2009-01-01
I'm running Medori 0.1.1 and it has fewer preference choices. Some of my parameters are greyed out and others accept changes but the next time Midori is run the changes are lost. Midori is in development and has yet to implement all it's features. If you're interested in the webkit rendering Midori uses you can also install Epiphany-webkit.

---

### Post by dbbolton on 2009-01-01
> **fragos said:**
> I'm running Medori 0.1.1 and it has fewer preference choices. Some of my parameters are greyed out and others accept changes but the next time Midori is run the changes are lost. Midori is in development and has yet to implement all it's features. If you're interested in the webkit rendering Midori uses you can also install Epiphany-webkit.
Hmm, so this isn't a bug then?

---

### Post by fragos on 2009-01-01
Not a bug -- just work in progress.

---

### Post by dbbolton on 2009-01-03
Not sure if I ought to start a new thread, but I'll as anyway. I just compiled the latest versions of webkit and midori, but when I launch midori I get this message:

```
midori: error while loading shared libraries: libwebkit-1.0.so.1: cannot open shared object file: No such file or directory

```

---

### Post by fragos on 2009-01-03
When you compile you need to have the .dev for libraries you use. Perhaps you're missing libwebkit-dev.

---

### Post by dbbolton on 2009-01-03
> **fragos said:**
> When you compile you need to have the .dev for libraries you use. Perhaps you're missing libwebkit-dev.
Do I need to have libwebkit-dev installed before I compile WebKit as well?

Also, libwebkit-dev depends on libwebkit-1.0-1 . Can I have this package installed and still build WebKit from source?

---

### Post by fragos on 2009-01-03
Yes -- it's not a package in the normal sense it's used to resolve entry points to the actual addresses in the library.

---


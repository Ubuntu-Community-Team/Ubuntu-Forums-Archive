---
title: "upgrading xsane"
date: 2008-09-25
forum: Desktop Environments
---

### Post by prezbedard on 2008-09-25
I am trying to upgrade xsane. I was unable to do it through aptitude. It couldn't find the package even after I did an update.

So I downloaded the latest sources that went fine until it told me I needed a higher version of sane. I downloaded those and installed np. Then back to installing xsane now it tells me I need a higher version of gtk. I'm not sure how to upgrade the gtk since there are what seems like thousands of packages with gtk. 

What is the proper method to get the latest gtk lib?

Thanks!!

---

### Post by prezbedard on 2008-09-25
ok this is what it tells me when running ./configure and make for xsane

```
ERROR: GTK-1.2.0 or newer is needed for compiling xsane
       if you installed gtk as rpm make sure you also included
       gtk-devel

```

I checked under /usr/lib it appears I have gtk2.0

so I'm not sure what is going on?

---

### Post by javacentrum on 2010-01-01
You must have installed libgim2.0-dev package.

---

### Post by meho_r on 2010-01-01
> **javacentrum said:**
> You must have installed libgim2.0-dev package.

Don't you think it's a little bit late for that info?

---


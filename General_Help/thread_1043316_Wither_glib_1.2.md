---
title: "Wither glib 1.2?"
date: 2009-01-18
forum: General Help
---

### Post by efalk on 2009-01-18
I wrote a package ([http://fplan.sf.net](http://fplan.sf.net)) which links to glib 1.2

Upon upgrading to Hardy, I find it can no longer be installed.

The problem seems to be a missing glib1.2

Synaptic shows libglib 1.2-dbg, libglib 1.2-dev, and libglib 1.2ldbl, but no libglib 1.2.  What gives?  Installing all the packages that Synaptic *did* find was of no help.

---

### Post by mssever on 2009-01-18
> **efalk said:**
> I wrote a package ([http://fplan.sf.net](http://fplan.sf.net)) which links to glib 1.2

Upon upgrading to Hardy, I find it can no longer be installed.

The problem seems to be a missing glib1.2

Synaptic shows libglib 1.2-dbg, libglib 1.2-dev, and libglib 1.2ldbl, but no libglib 1.2.  What gives?  Installing all the packages that Synaptic *did* find was of no help.
If you install libglib1.2-dev (notice that there's no space in the name), then you will have the full lib pulled in with dependencies. (The main lib package is libglib1.2ldbl.) If you still have problems, you can be certain that they're not related to this lib not being installed.

---

### Post by efalk on 2009-01-18
> **mssever said:**
> If you install libglib1.2-dev (notice that there's no space in the name), then you will have the full lib pulled in with dependencies. (The main lib package is libglib1.2ldbl.) If you still have problems, you can be certain that they're not related to this lib not being installed.

Thanks.  I had thought that libglib1.2ldbl was what I needed, and I did install it, but it didn't help.

I've installed libglib1.2ldbl and I can see  /usr/lib/libglib-1.2.so.0 is installed just fine, but installing xfplan still produces this error message:

>  xfplan depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.

The xfplan package says:

> Depends: gdk-imlib11, libart2 (>= 1.2.13-5), libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.4-1), libdb3 (>= 3.2.9-23), libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libglib1.2 (>= 1.2.0), libgnome32 (>= 1.2.13-5), libgnomesupport0 (>= 1.2.13-5), libgnomeui32 (>= 1.4.2-3), libgtk1.2 (>= 1.2.10-4), libice6, libpng12-0 (>= 1.2.8rel), libsm6, libx11-6, libxext6, libxi6

And the libglib1.2ldbl package says:

> Replaces: libglib1.2

So I'm at a loss as to what more I can do to satisfy this dependency.

---

### Post by mssever on 2009-01-18
> **efalk said:**
> Thanks.  I had thought that libglib1.2ldbl was what I needed, and I did install it, but it didn't help.

I've installed libglib1.2ldbl and I can see  /usr/lib/libglib-1.2.so.0 is installed just fine, but installing xfplan still produces this error message:



The xfplan package says:



And the libglib1.2ldbl package says:



So I'm at a loss as to what more I can do to satisfy this dependency.
It would be nice if libglib1.2ldbl also had a Provides: libglib1.2. But it doesn't. It's an outdated lib, and the .deb you're trying to install is probably also ancient. Your best bet is probably to build from source.

(I suppose gdebi or dpkg might also have an option to force installation ignoring dependencies. That might work, but I wouldn't really recommend it. See the respective man pages.)

EDIT: I just noticed that the package is one you created. In that case, just change the dependency to ```
libglib1.2 | libglib1.2ldbl
```

---

### Post by efalk on 2009-01-18
> **mssever said:**
> I just noticed that the package is one you created. In that case, just change the dependency to ```
libglib1.2 | libglib1.2ldbl
```

If I did that, would the package still install onto Ubuntu 6.x systems, or will I have to start releasing two different packages?

Also, I believe the dependency was created automatically by the build process; I'll have to figure out how to change it.

---

### Post by efalk on 2009-01-18
> **mssever said:**
> It would be nice if libglib1.2ldbl also had a Provides: libglib1.2. But it doesn't.

I wonder if I could convince the maintainers of libglib1.2ldbl to fix that.

---

### Post by mssever on 2009-01-18
> **efalk said:**
> If I did that, would the package still install onto Ubuntu 6.x systems, or will I have to start releasing two different packages?
It should still work, because the pipe means "or". So either package will satisfy the dependency. I did that once on one of my programs when a dependency got renamed.

---

### Post by efalk on 2009-01-18
> **mssever said:**
> It should still work, because the pipe means "or". So either package will satisfy the dependency. I did that once on one of my programs when a dependency got renamed.

Got it, thanks.

---


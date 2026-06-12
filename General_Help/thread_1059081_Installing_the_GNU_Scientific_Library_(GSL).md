---
title: "Installing the GNU Scientific Library (GSL)"
date: 2009-02-03
forum: General Help
---

### Post by spacelem on 2009-02-03
Hi,

I recently moved to Ubuntu from another distro, and I've been having problems with using the GSL. Doing "apt-cache search gsl" gives me multiple options, and I've installed all the ones that seem appropriate, but my program still won't compile. Synaptic only shows two packages, and I haven't quite got my apt-fu up to scratch yet.

The error I'm getting when I run make is:
```

defs.h:7:59: error: gsl/gsl_rng.h: No such file or directory
defs.h:8:61: error: gsl/gsl_randist.h: No such file or directory

```

The program compiles cleanly under CentOS at work, and on Gentoo, so I'm confident that the code is not the problem.

So my question is: what is the package(s) I need to install to use the GSL?

Thanks.

---

### Post by Idaho Dan on 2009-02-03
spacelem,
I have no idea what I am talking about, but.
I have Intrepid installed in my computer, and when I go to the synaptic package manager and search "gnu scientific" I get a lot of things that show up.
Are none of these what you need?
I even show having libgsl0ldbl installed as a package, but I would not know how to use it.

---

### Post by niteshifter on 2009-02-03
Hi,

Did you install libgsl0-dev? libgsl0 is just the runtime lib. Generally here in Debian / Ubuntu land you need the -dev versions of a lib to get the various header files and such installed to support compilation.

---

### Post by spacelem on 2009-02-03
Ah, brilliant!

I don't know why that didn't show up in synaptic (I just searched for "gsl"), and I didn't think to install the developer package because I am an idiot.

Thanks!

---


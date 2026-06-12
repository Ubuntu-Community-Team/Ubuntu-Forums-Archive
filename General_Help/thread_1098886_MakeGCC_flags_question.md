---
title: "Make/GCC flags question"
date: 2009-03-17
forum: General Help
---

### Post by chemicalfan on 2009-03-17
This is a bit of a noob question, but I'm looking for some guidance on implementing GCC flags when running 'make'. I've recently discovered information on GCC and compiling optimized 'custom' versions of modules and other software (mainly borrowed from Gentoo users). My question is: When using make, how do I include GCC flags? I'm hoping it doesn't involve modifying the makefiles (I can't believe it would be that complicated). I've heard that I can modify "make.conf", but I can't find that file anywhere. I've also heard that the flags can be included somewhere on the command line when running make, but I can't find any information on correct syntax.

Can someone provide me with the required way forward?

---

### Post by sdennie on 2009-03-17
It will probably involve invoking make like this:

```

make CXX_FLAGS=-some_flag -some_other_flag

```

But, you may want to look at:

```

./configure --help

```

You can probably have your flags appended to what the build process normally uses.

Note: Regardless of what the gentoo forums say, the vast majority of apps won't benefit from raising the optimization level from what it already is set at.

---

### Post by chemicalfan on 2009-03-17
Thanks mate, I'll give it a go when I'm next compiling. Incidentally, I struggled to find the ./configure file - I'm new to compiling, I've just done it without thinking before!

---

### Post by sdennie on 2009-03-17
Glad to help but, I'll again stress that compiling with more optimization probably won't help most apps.  If you have a known CPU bound application that you've measured and understand, then, yes, by all means, play with compiler options and see if you can make it faster.  If you are just wanting a generally faster system, recompiling everything with higher optimization is likely to leave you your system in a horribly destroyed state with no performance gains to show for it.

---


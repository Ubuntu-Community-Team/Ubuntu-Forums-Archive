---
title: "xwindows programming problem"
date: 2008-03-22
forum: Dell  Ubuntu Support
---

### Post by matrix13 on 2008-03-22
Hi
I am using inspiron 1420 with Ubuntu 7.04 on it. I installed it from the respective CD.
I wanted to do some xwindows programming like displying a window, interfacing input devices etc.. for my rpoject work.
But i didnt find any Xlib and such directories. Do I have to install some other packages for doing Xwindows programming in my machine?
Please help. Tell me what to do

---

### Post by sdennie on 2008-03-22
Yes, on Ubuntu you won't have very much in the way of development tools or headers installed by default.  A reasonable starting point would be to:

```

sudo apt-get install build-essential

```

That should grab things like gcc/g++/make for you.  To get the proper headers you'll need for development, I've found the easiest way is to use synaptic and just search for what you need.  In Ubuntu, package names ending in -dev install things like headers and anything else that a package needs to be built against.  In your case, as a starting point, it sounds like you would want to go to System->Administration->Synaptic Package Manager and then just search for "x11 dev".  That will bring up a bunch of packages but, I think the one you are looking for is going to be libx11-dev.  Some of the other -dev packages in that list are likely to be useful if you are doing X11 dev work though so, you may want to look through them.

---


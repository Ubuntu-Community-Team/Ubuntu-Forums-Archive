---
title: "C compiler needed"
date: 2005-12-11
forum: Desktop Environments
---

### Post by ToiletDuck on 2005-12-11
Hi all, 

 I get this error while trying to install a program "configure: error: no acceptable C compiler found in $PATH"

Ive looked through Synaptic but not sure weather i found what i need or not. Can someone bump me in the right direction as to how i can obtain the C compiler.

Thanks

---

### Post by aysiu on 2005-12-11
build-essential

It's in Synaptic.

---

### Post by arpunk on 2005-12-11
The C compiler is *gcc*, you can install it with *synaptic* followed by the *build-essentials* meta-package. I would recommend the gcc-3.x branch, since ive had issues dealing with the new 4.x branch (screwed binaries, bad optimizations, etc...) in some software (thus i compile my laptop kernel with 4.x branch, it optimizes it a bit more and gives me a faster kernel.)

---

### Post by ToiletDuck on 2005-12-11
Thanks for the help guys, but now im getting this error.

"Unable to initialize the video driver. The errors are:
fb: Unsupported in X"

---

### Post by arpunk on 2005-12-11
What did you compile?

---

### Post by ToiletDuck on 2005-12-11
Sorry, forgot to add that. the program would be advancemame

---

### Post by arpunk on 2005-12-11
I guess you see this already:

[http://advancemame.sourceforge.net/doc-build.html](http://advancemame.sourceforge.net/doc-build.html)
[http://advancemame.sourceforge.net/doc-install.html#1.1](http://advancemame.sourceforge.net/doc-install.html#1.1)

Directly quoting the second link:

> To allow the Advance programs to display in X you must install the SDL library. Generally it's already present in all the recent distributions.

To allow the Advance programs to directly control your video board in console mode, you must install and configure the Linux Frame Buffer driver or a recent SVGALIB library.

The Linux Frame Buffer drivers are always included in the Linux kernel source, but generally they must be explicitly compiled or loaded. Please note that you cannot use the VESA Linux Frame Buffer driver, you must use a driver specific for your video board.

And:

> If you are using the `fb' driver, ensure to don't use the VESA Frame Buffer. It doesn't work for the Advance programs.

Try using SDL video driver if in X.

---


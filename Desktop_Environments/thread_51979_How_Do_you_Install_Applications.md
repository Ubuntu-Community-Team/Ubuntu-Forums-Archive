---
title: "How Do you Install Applications?"
date: 2005-07-25
forum: Desktop Environments
---

### Post by Ian Gordon on 2005-07-25
I am confused. I am new to Linux application installation and I am not sure how I can successfully install an application that I download.

Usually they are tar'd and I need to compile them. I want to use them in a graphical interface: Gnome.

People keep saying to type

```

# ./configure
# make
# make install

```

But, "./configure" is taken as a directory and doesn't exist. Can someone people help me!

---

### Post by heimo on 2005-07-26
If the application is available as a package in Ubuntu repositories, you should probably install using synaptic or apt-get.

Check the menu:
System->Administration->Synaptic

Additional reading:
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

If the application is not available as a package and it has to be compiled, check the INSTALL and README files in the root directory of .tar -file. The normal procedure is to uncompress source files, change directory to the directory that was created, run ./configure script, run make (to compile) and make install (to copy binaries to system directories like /usr). This can vary and some other debendencies may be needed (mostly libraries), that's why it's much, much easier to use pre-packaged software when ever it's available / possible.

For more detailed instructions, please tell us what's the program you're trying to install, version and where you downloaded the .tar.gz. Thanks.

---

### Post by charlieg on 2005-07-26
Are there any applications in particular?

Some applications are not directly available for Hoary - that is, in Synaptic, you need to specify some additional sources.  Here's a howto here for getting up and running with Backports which includes a lot of upgrades and some additional applications:
[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---


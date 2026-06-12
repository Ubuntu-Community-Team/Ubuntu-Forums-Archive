---
title: "ld.so.conf - why no /usr/local/lib?"
date: 2005-12-07
forum: General Help
---

### Post by chocorisu on 2005-12-07
First time post - hope I put it in the right place. :???: 

I'm an experienced programmer but a first time user of Ubuntu (and relatively inexperienced with Linux generally) and I'm trying to compile some software using external libraries, i.e. ones not in the repositories. I've noticed that several projects put their .so files in **/usr/local/lib** but that path is not included, by default, in **/etc/ld.so.conf.**

Isn't /usr/local/lib a standard path? I understand that I'd never run into this problem just installing software through the official repositories but it seems like an unnecessary hurdle even for programmers new to the system.

As it is, I found the solution through a bit of Googling, but I'm still curious why it isn't just set up this way in the first place. Perhaps someone could change it for the next release?

---

### Post by Jacky_J on 2006-03-23
I agree.  This makes setting up external libraries, such as fmod, a hassle.

---

### Post by Barrakketh on 2006-03-23
[QUOTE=chocorisu]I'm an experienced programmer but a first time user of Ubuntu (and relatively inexperienced with Linux generally) and I'm trying to compile some software using external libraries, i.e. ones not in the repositories. I've noticed that several projects put their .so files in **/usr/local/lib** but that path is not included, by default, in **/etc/ld.so.conf.**

Isn't /usr/local/lib a standard path? I understand that I'd never run into this problem just installing software through the official repositories but it seems like an unnecessary hurdle even for programmers new to the system.[/quote]

Not really.  You should read the Debian Policy Manual for information on the directory structure for files.  From chapter 8, section 8.1:

> The run-time shared library needs to be placed in a package whose name changes whenever the shared object version changes. The most common mechanism is to place it in a package called librarynamesoversion, where soversion is the version number in the soname of the shared library. Alternatively, if it would be confusing to directly append soversion to libraryname (e.g. because libraryname itself ends in a number), you may use libraryname-soversion and libraryname-soversion-dev instead. 

If your package includes run-time support programs that do not need to be invoked manually by users, but are nevertheless required for the package to function, then it is recommended that these programs are placed (if they are binary) in a subdirectory of /usr/lib, preferably under /usr/lib/package-name. If the program is architecture independent, the recommendation is for it to be placed in a subdirectory of /usr/share instead, preferably under /usr/share/package-name. 

If you have several shared libraries built from the same source tree you may lump them all together into a single shared library package, provided that you change all of their sonames at once (so that you don't get filename clashes if you try to install different versions of the combined shared libraries package). 

The package should install the shared libraries under their normal names. For example, the libgdbm3 package should install libgdbm.so.3.0.0 as /usr/lib/libgdbm.so.3.0.0. The files should not be renamed or re-linked by any prerm or postrm scripts; dpkg will take care of renaming things safely without affecting running programs, and attempts to interfere with this are likely to lead to problems. 

Shared libraries should not be installed executable, since the dynamic linker does not require this and trying to execute a shared library usually results in a core dump. 

The run-time library package should include the symbolic link that ldconfig would create for the shared libraries. For example, the libgdbm3 package should include a symbolic link from /usr/lib/libgdbm.so.3 to libgdbm.so.3.0.0. This is needed so that the dynamic linker (for example ld.so or ld-linux.so.*) can find the library between the time that dpkg installs it and the time that ldconfig is run in the postinst script.
You can read the DPM online [Here](http://www.us.debian.org/doc/debian-policy/) or [download the PDF](http://www.us.debian.org/doc/debian-policy/policy.pdf.gz).

---

### Post by taurus on 2006-03-23
If /usr/local/lib is not in /etc/ld.so.conf, just add it in there...
```

sudo gedit /etc/ld.so.conf

```
Save it and run
```

sudo ldconfig

```

---


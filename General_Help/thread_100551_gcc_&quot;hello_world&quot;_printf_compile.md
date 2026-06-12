---
title: "gcc &quot;hello world&quot; printf compile"
date: 2005-12-07
forum: General Help
---

### Post by chaz1951 on 2005-12-07
After installing gcc from the CD using synaptic, a simple "hello world" program will not compile:

chaz@sys15:/home/chaz#cc helo.c
helo.c:1:19: error: stdio.h: No such file or directory
helo.c: In function ‘main’:
helo.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
chaz@sys15:/home/chaz#

---

### Post by Grey on 2005-12-07
try installing the package build-essential.  It's telling you that you are missing standard C libraries, which will probably be included there.  :)

```
sudo apt-get install build-essential
```

---

### Post by rplantz on 2005-12-07
[QUOTE=chaz1951]After installing gcc from the CD using synaptic, a simple "hello world" program will not compile:

chaz@sys15:/home/chaz#cc helo.c
helo.c:1:19: error: stdio.h: No such file or directory
helo.c: In function &#8216;main&#8217;:
helo.c:4: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
chaz@sys15:/home/chaz#[/QUOTE]

Try ```

locate stdio.h

```
to see if stdio.h is installed okay.

It seems like I had to install several gcc things, but I don't recall everything I did.

---

### Post by chaz1951 on 2005-12-07
[QUOTE=Grey]try installing the package build-essential.  It's telling you that you are missing standard C libraries, which will probably be included there.  :)

```
sudo apt-get install build-essential
```[/QUOTE]

Thank you!  That did it.  I had assumed that synaptic would drag over everything needed for general compiling of C programs when told to install gcc.

---

### Post by atoponce on 2005-12-07
I believe to get everything, you also need to install the G++ packages.

---

### Post by Grey on 2005-12-07
Yeah, it can be a little confusing.  Installing the GCC package will just install the compiler and nothing else.  The build-essential package is a meta-package that depends upon everything you absolutely need to get a program to compile.

Anyways, glad to be of help.

---

### Post by chaz1951 on 2005-12-07
[QUOTE=Grey]Yeah, it can be a little confusing.  Installing the GCC package will just install the compiler and nothing else.  The build-essential package is a meta-package that depends upon everything you absolutely need to get a program to compile.

Anyways, glad to be of help.[/QUOTE]


Is there a way for me to mark this as a closed issue?

---

### Post by matthew on 2005-12-07
[quote=chaz1951]Is there a way for me to mark this as a closed issue?[/quote]Edit your first post, click "go advanced" or whatever the box says, then add something like this to your title:
```
gcc "hello world" printf compile (solved) 
```

---

### Post by rplantz on 2005-12-08
[QUOTE=Grey]try installing the package build-essential.  It's telling you that you are missing standard C libraries, which will probably be included there.  :)

```
sudo apt-get install build-essential
```[/QUOTE]

Upon further investigation, I believe that the required package is libc6-dev. Since it is a dependency for build-essential, it gets installed when you install build-essential.

I'm being picky here, but the error message says that the header file is missing, not the library. I taught computer science for 20 years, and one of the things that always bugged me is that many textbooks say that including the header files is the same as including libraries. It is not the same. The header files contain certain declarations. Linkage to the libraries is created during the linking phase (the last one) of creating a program.

I'm being very picky here, and I don't mean to offend anyone. I can certainly understand how people get this idea since many textbooks say so.

The important thing is that chaz1951 can now say "Hello, World."  :-)

---


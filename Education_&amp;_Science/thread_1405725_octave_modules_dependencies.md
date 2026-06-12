---
title: "octave modules dependencies"
date: 2010-02-13
forum: Education &amp; Science
---

### Post by carandraug on 2010-02-13
Hi

I installed octave 3.2. Later, I also installed some modules (statistics and image modules to be more exact) and noticed that these have octave 3.0 as dependencies. When I now run octave it's version 3.0 not 3.2.
Is there any reason for the modules to require octave 3.0? Would they not work in 3.2?
Thanks in advance

EDIT 1: I was told by a friend (MatLab user) that the "modules" should actually be referred as toolkits. I'm a new user of this languages, all I knew was Perl.

EDIT 2: I'm using ubuntu 9.10

---

### Post by carandraug on 2010-03-12
I got it working. Seems that they are actually different. The modules/toolkits/packages in the repositories seem to be for octave 3.0 only. When I was running octave from the terminal it would choose to run 3.0 instead of 3.2 because it had both installed. This can be solved by running
```
/usr/bin/octave3.2
```
instead of just
```
octave
```

This however does not solve the fact that I couldn't use the packages. They are, however, fairly easy to install manually. Just download the packages you want from [http://octave.sourceforge.net/packages.php]("octave-forge") and then from the octave prompt run
```
pkg install package_file_name.tar.gz
```
some packages may have other packages as dependencies but they should be listed in the package details page.

---


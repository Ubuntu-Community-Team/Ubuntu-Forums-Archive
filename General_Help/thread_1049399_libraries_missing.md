---
title: "libraries missing"
date: 2009-01-24
forum: General Help
---

### Post by Kathgar on 2009-01-24
hi I'm using ubuntu 8.10 and I need to use molden for my collage class: [http://www.cmbi.ru.nl/molden/molden.html](http://www.cmbi.ru.nl/molden/molden.html) I tried using the executables and it wont work with the .linux files i get the error message that libg2c.so.0 is missing and with the .gfortran files I get the errormessage that the libgfortran.so.1 is missing.
I installed the libraries with:
sudo apt-get install libg2c0 libgfortran2
but when I got this errormessage when starting the damn molden programm:
 libgfortran.so.1: cannot open shared object file: No such file or directory
I linked the ligfortran libraries:
sudo ln -s /usr/lib/libgfortran.so.2 /usr/lib/libgfortran.so.1
and now I got this stupid error where I get stuck:
./gmolden4.7.gfortran: symbol lookup error: ./gmolden4.7.gfortran: undefined symbol: _gfortran_copy_string

thanks for ur help

---

### Post by WylieE on 2009-01-26
I'm having a similar problem posted here:
[http://ubuntuforums.org/showthread.php?t=1051256](http://ubuntuforums.org/showthread.php?t=1051256)

---

### Post by darius007 on 2010-11-10
Hi..I have the same problem. First I got this error message that the  libgfortran.so.1 is missing. So I decided to link the libgfortran libraries:

sudo ln -s /usr/lib/libgfortran.so.3 /usr/lib/libgfortran.so.1

and now I got this error:

symbol lookup error: ../../program/main/liblapack.so.3: undefined symbol: _gfortran_copy_string


Thanks for ur help.

---


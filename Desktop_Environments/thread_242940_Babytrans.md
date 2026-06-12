---
title: "Babytrans"
date: 2006-08-24
forum: Desktop Environments
---

### Post by neymac on 2006-08-24
Babytrans is an excellent program to translate words from english to other languages.It uses the Babylon's dictionaries that are very good ones.
I installed it using synaptic and it works fine, but when I close it and try launch again it didn't start. 
If I delete the config file located at ~./babytrans (/home/<user name>./babytrans) it starts again, asks for select the language to use for translation and if I keep it running it works fine. If I close it I have to delete again the config file to restart it.

The version is babytrans 0.9.1.

I tried compile the source that I found at  [http://fjolliton.free.fr/babytrans/](http://fjolliton.free.fr/babytrans/) , but at ./configure I got stuck with error related to GLIB 1.2.0, then I come back to the synaptic and reinstall the repo's package babytrans 0.9.1-0.3ubuntu2(dapper).

Does anyone use Babytrans in Ubuntu 6.10 and know how fix this?

---

### Post by neymac on 2006-08-24
This is what I got when tried compile the source for Babytrans:
> a:~/Desktop/babytrans-0.9.1$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for POSIXized ISC... no
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking how to run the C++ preprocessor... c++ -E
checking if compiler use ISO headers... yes
checking if compiler know namespace keyword... yes
checking how compiler handle std namespace... as expected by a good C++ compiler :)
checking if C++ library include stringstream... yes
checking for glib-config... /usr/local/bin/glib-config
checking for GLIB - version >= 1.2.0...
*** 'glib-config --version' returned 1.2.0, but GLIB (1.2.10)
*** was found! If glib-config was correct, then it is best
*** to remove the old version of GLIB. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If glib-config was wrong, set the environment variable GLIB_CONFIG
*** to point to the correct copy of glib-config, and remove the file config.cache
*** before re-running configure
no
configure: error: *** GLIB >= 1.2.0 not installed - please install first ***

But when I install via synaptic there is no error messages at all.

---

### Post by neymac on 2007-10-22
Babytrans worked fine with Gusty. Finally I can use this helpfull translator.
 It did not work well with the previous release of Ubuntu (Dapper and Feisty).

---


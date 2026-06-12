---
title: "Trouble compiling libiphone"
date: 2009-03-30
forum: General Help
---

### Post by mikimis on 2009-03-30
I'm trying to install either itunnel or ifuse so I can use my iPod Touch via USB.  Both of these programs seem to need libiphone to work.  Following the instructions [here]("http://github.com/MattColyer/libiphone/tree/master") leads to the following when running ./autogen.sh


```
root@mikimis-laptop:/home/mikimis/MattColyer-libiphone-443edc808d8b2e0ac8d6c497248815a5a1a5a9c9# ./autogen.sh
./autogen.sh: 3: libtoolize: not found
configure.ac:14: installing `./compile'
configure.ac:6: installing `./install-sh'
configure.ac:6: installing `./missing'
dev/Makefile.am: installing `./depcomp'
src/Makefile.am:14: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:14:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:14:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:14:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:14:   its definition is in aclocal's search path.
configure.ac:10: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
```

I've been at this all day and just don't know what else to do ](*,)




UPDATE: installing libtools helped, but now I have other issues...If anyone else is having trouble with iFuse or libiphone, here's the development page: [http://libiphone.lighthouseapp.com/projects/27916-libiphone/tickets?q=all]("http://libiphone.lighthouseapp.com/projects/27916-libiphone/tickets?q=all")

---

### Post by Tex-Twil on 2009-08-25
What are the issues you have now ? I compiled everything successfully.

---


---
title: "Oprofile 0.9.4 install problems on Ubuntu 8.10."
date: 2008-12-07
forum: General Help
---

### Post by Dhruv2008 on 2008-12-07
Hi,

While trying to install the latest version of Oprofile 0.9.4 on Ubuntu 8.10 (with 2.6.27-9 generic kernel), I keep getting the following error message after make:

Making all in libutil++
make[2]: Entering directory `/home/dhruv/oprofile-0.9.4/libutil++'
Making all in .
make[3]: Entering directory `/home/dhruv/oprofile-0.9.4/libutil++'
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I ../libutil -I ../libop -I ../libpp  -W -Wall -fno-common -ftemplate-depth-50 -g -O2 -MT file_manip.o -MD -MP -MF ".deps/file_manip.Tpo" -c -o file_manip.o file_manip.cpp; \
	then mv -f ".deps/file_manip.Tpo" ".deps/file_manip.Po"; else rm -f ".deps/file_manip.Tpo"; exit 1; fi
In function ‘int open(const char*, int, ...)’,
    inlined from ‘bool copy_file(const std::string&, const std::string&)’ at file_manip.cpp:47:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[3]: *** [file_manip.o] Error 1
make[3]: Leaving directory `/home/dhruv/oprofile-0.9.4/libutil++'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dhruv/oprofile-0.9.4/libutil++'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dhruv/oprofile-0.9.4'
make: *** [all] Error 2

I have the latest version of binutils which came with the distribution, and I also installed the latest binutils-devel package using the package manager.

The repositories of Ubuntu contain the older, 0.9.3 version of Oprofile which does get installed correctly but I can't use it to profile the INST_RETIRED.ANY_P event, the opreport generates an error message complaining bad event specification. This problem was fixed in 0.9.4 and I am using it on Suse 10.3 on a separate machine with no problems.

I am in a fix, since I urgently need to profile my system for a research project and neither can I debug the 0.9.4 nor can I use the older 0.9.3.

Any help will be greatly appreciated. 

Thanks in advance !

-Dhruv

---


---
title: "libtool error while compiling Thrift"
date: 2009-12-24
forum: Desktop Environments
---

### Post by jamess_jack on 2009-12-24
Hi,

I am trying to compile thrift on my Ubuntu machine.

I did ./configure -- which works fine.

But When I do --  make --> It gives the following errors.
========================================================================
../../libtool: line 841: X--tag=CXX: command not found
../../libtool: line 874: libtool: ignoring unknown tag : command not found
../../libtool: line 841: X--mode=link: command not found
../../libtool: line 1008: *** Warning: inferring the mode of operation is deprecated.: command not found
../../libtool: line 1009: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
gcc: no input files
gcc: no input files
gcc: no input files
gcc: no input files
../../libtool: line 2253: X-Wall: command not found
../../libtool: line 2253: X-I./src: No such file or directory
../../libtool: line 2253: X-I/usr/include: No such file or directory
../../libtool: line 2253: X-g: command not found
../../libtool: line 2253: X-O2: command not found
../../libtool: line 2253: X-Wall: command not found
../../libtool: line 1967: X-L/usr/lib: No such file or directory
../../libtool: line 2422: Xthrift: command not found
X: user not authorized to run the X server, aborting.
../../libtool: line 2434: Xthrift: command not found
../../libtool: line 2442: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make[3]: *** [thrift] Error 1
make[3]: Leaving directory `/home/bhavinkumar/Desktop/thrift-0.2.0/compiler/cpp'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bhavinkumar/Desktop/thrift-0.2.0/compiler/cpp'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bhavinkumar/Desktop/thrift-0.2.0'
make: *** [all] Error 2
========================================================================

can somebody guide -- how to solve this problem ?

Thanks,
Bhavin

---

### Post by arsenepark on 2010-04-01
This is my issue, anyone knows where the prob is?
bootstrap.sh and configure are good.
make is the problem. The following is the error.
I am using ubuntu 8.04 and cassandra 0.5.1 and thrift-0.2.0-incubating.

Thanks.
Dennis



mv -f .deps/thrift-t_html_generator.Tpo .deps/thrift-t_html_generator.Po
/bin/sh ../../libtool --tag=CXX   --mode=link g++ -Wall -I./src -I/usr/include -g -O2 -Wall -L/usr/lib  -o thrift thrift-thrifty.o thrift-thriftl.o thrift-main.o md5.o thrift-t_generator.o thrift-t_cpp_generator.o thrift-t_java_generator.o thrift-t_csharp_generator.o thrift-t_py_generator.o thrift-t_rb_generator.o thrift-t_perl_generator.o thrift-t_php_generator.o thrift-t_erl_generator.o thrift-t_cocoa_generator.o thrift-t_st_generator.o thrift-t_ocaml_generator.o thrift-t_hs_generator.o thrift-t_xsd_generator.o thrift-t_html_generator.o -lfl -lrt -lpthread 
../../libtool: line 841: X--tag=CXX: command not found
../../libtool: line 874: libtool: ignoring unknown tag : command not found
../../libtool: line 841: X--mode=link: command not found
../../libtool: line 1008: *** Warning: inferring the mode of operation is deprecated.: command not found
../../libtool: line 1009: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
gcc: no input files
gcc: no input files
gcc: no input files
gcc: no input files
../../libtool: line 2253: X-Wall: command not found
../../libtool: line 2253: X-I./src: No such file or directory
../../libtool: line 2253: X-I/usr/include: No such file or directory
../../libtool: line 2253: X-g: command not found
../../libtool: line 2253: X-O2: command not found
../../libtool: line 2253: X-Wall: command not found
../../libtool: line 1967: X-L/usr/lib: No such file or directory
../../libtool: line 2422: Xthrift: command not found

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

../../libtool: line 2434: Xthrift: command not found
../../libtool: line 2572: X-lfl: command not found
../../libtool: line 2572: X-lrt: command not found
../../libtool: line 2572: X-lpthread: command not found
../../libtool: line 2659: X-L/var/lib/thrift/compiler/cpp: No such file or directory
../../libtool: line 2572: X-lfl: command not found
../../libtool: line 2572: X-lrt: command not found
../../libtool: line 2572: X-lpthread: command not found
../../libtool: line 2659: X-L/var/lib/thrift/compiler/cpp: No such file or directory
../../libtool: line 2572: X-lfl: command not found
../../libtool: line 2572: X-lrt: command not found
../../libtool: line 2572: X-lpthread: command not found
../../libtool: line 5207: Xg++ "" "" "" "" "" "" -o @OUTPUT@ thrift-thrifty.o thrift-thriftl.o thrift-main.o md5.o thrift-t_generator.o thrift-t_cpp_generator.o thrift-t_java_generator.o thrift-t_csharp_generator.o thrift-t_py_generator.o thrift-t_rb_generator.o thrift-t_perl_generator.o thrift-t_php_generator.o thrift-t_erl_generator.o thrift-t_cocoa_generator.o thrift-t_st_generator.o thrift-t_ocaml_generator.o thrift-t_hs_generator.o thrift-t_xsd_generator.o thrift-t_html_generator.o  -L/var/lib/thrift/compiler/cpp -lfl -lrt -lpthread: File name too long
../../libtool: line 5208: Xg++ "" "" "" "" "" "" -o @OUTPUT@ thrift-thrifty.o thrift-thriftl.o thrift-main.o md5.o thrift-t_generator.o thrift-t_cpp_generator.o thrift-t_java_generator.o thrift-t_csharp_generator.o thrift-t_py_generator.o thrift-t_rb_generator.o thrift-t_perl_generator.o thrift-t_php_generator.o thrift-t_erl_generator.o thrift-t_cocoa_generator.o thrift-t_st_generator.o thrift-t_ocaml_generator.o thrift-t_hs_generator.o thrift-t_xsd_generator.o thrift-t_html_generator.o  -L/var/lib/thrift/compiler/cpp -lfl -lrt -lpthread: File name too long

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

../../libtool: line 5217: : command not found
make[3]: Leaving directory `/var/lib/thrift/compiler/cpp'
make[2]: Leaving directory `/var/lib/thrift/compiler/cpp'
Making all in lib
make[2]: Entering directory `/var/lib/thrift/lib'
Making all in cpp
make[3]: Entering directory `/var/lib/thrift/lib/cpp'
/bin/sh ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..  -I/usr/include -I./src  -Wall -g -O2 -MT Thrift.lo -MD -MP -MF .deps/Thrift.Tpo -c -o Thrift.lo `test -f 'src/Thrift.cpp' || echo './'`src/Thrift.cpp
../../libtool: line 841: X--tag=CXX: command not found
../../libtool: line 874: libtool: ignoring unknown tag : command not found
../../libtool: line 841: X--mode=compile: command not found
../../libtool: line 1008: *** Warning: inferring the mode of operation is deprecated.: command not found
../../libtool: line 1009: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../../libtool: line 1152: Xg++: command not found
../../libtool: line 1152: X-DHAVE_CONFIG_H: command not found
../../libtool: line 1152: X-I.: command not found
../../libtool: line 1152: X-I../..: No such file or directory
../../libtool: line 1152: X-I/usr/include: No such file or directory
../../libtool: line 1152: X-I./src: No such file or directory
../../libtool: line 1152: X-Wall: command not found
../../libtool: line 1152: X-g: command not found
../../libtool: line 1152: X-O2: command not found
../../libtool: line 1152: X-MT: command not found
../../libtool: line 1152: XThrift.lo: command not found
../../libtool: line 1152: X-MD: command not found
../../libtool: line 1152: X-MP: command not found
../../libtool: line 1152: X-MF: command not found
../../libtool: line 1152: X.deps/Thrift.Tpo: No such file or directory
../../libtool: line 1152: X-c: command not found
../../libtool: line 1205: XThrift.lo: command not found
../../libtool: line 1210: libtool: compile: cannot determine name of library object from `': command not found
make[3]: *** [Thrift.lo] Error 1
make[3]: Leaving directory `/var/lib/thrift/lib/cpp'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/lib/thrift/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/lib/thrift'
make: *** [all] Error 2

---

### Post by arsenepark on 2010-04-01
AND 
When I run "configure", it tells me "no" sometimes, does that metter?

......
checking for gawk... [COLOR="Red"]no[/COLOR]
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... [COLOR="red"]no[/COLOR]
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
......

---

### Post by seppyr on 2010-06-09
I got the same error under debian lenny. 

The problem is the libool 1.5.26 installed via apt which raises the errors.  

To build thrift download the libtool 1.5.24 source from 

[ftp://ftp.gnu.org/gnu/libtool/libtool-1.5.24.tar.gz](ftp://ftp.gnu.org/gnu/libtool/libtool-1.5.24.tar.gz)  

build it (./configure;make) and copy the libtool executable to the thrift source directory after you ran ./configure.  

Now 'make' should work and generate the thrift executable.

---


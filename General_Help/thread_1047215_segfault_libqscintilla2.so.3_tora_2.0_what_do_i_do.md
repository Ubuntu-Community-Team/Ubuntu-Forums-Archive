---
title: "segfault libqscintilla2.so.3 tora 2.0 what do i do wrong?"
date: 2009-01-22
forum: General Help
---

### Post by bloom on 2009-01-22
Hi, i installed tora 2.0 on ubuntu 8.10. Launching the program from console i
receive the following error 'Segmentation Fault' when i try to connect to a
database or simply when i try to open modify->preference. typing dmesg |
grep -i segfault, i receive:
[ 3586.122336] tora[6906]: segfault at 0 ip b7205973 sp bfdea550 error 4 in
libqscintilla2.so.3.0.0[b71a4000+16f000]
[ 3640.396607] tora[7004]: segfault at 0 ip b7204973 sp bfce8fb0 error 4 in
libqscintilla2.so.3.0.0[b71a3000+16f000]
trying gdb tora; run; i have:
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb568a6d0 (LWP 7018)]
0xb70a5973 in QsciLexerSQL::writeProperties ()
  from /usr/lib/libqscintilla2.so.3
the result of "ls -l /usr/lib | grep -i libqscintilla" is:
lrwxrwxrwx  1 root root      23 2009-01-18 18:59 libqscintilla2.so ->
libqscintilla2.so.5.0.1
lrwxrwxrwx  1 root root      23 2009-01-07 14:00 libqscintilla2.so.3 ->
libqscintilla2.so.3.0.0
lrwxrwxrwx  1 root root      23 2009-01-07 14:00 libqscintilla2.so.3.0 ->
libqscintilla2.so.3.0.0
-rw-r--r--  1 root root  1526324 2008-05-30 19:14 libqscintilla2.so.3.0.0
lrwxrwxrwx  1 root root      23 2009-01-18 18:59 libqscintilla2.so.5 ->
libqscintilla2.so.5.0.1
lrwxrwxrwx  1 root root      23 2009-01-18 18:59 libqscintilla2.so.5.0 ->
libqscintilla2.so.5.0.1
-rwxr-xr-x  1 root root  1659952 2009-01-18 18:59 libqscintilla2.so.5.0.1
lrwxrwxrwx  1 root root      22 2009-01-17 19:52 libqscintilla.so ->
libqscintilla.so.7.0.1
lrwxrwxrwx  1 root root      22 2008-12-23 15:34 libqscintilla.so.7 ->
libqscintilla.so.7.0.1
lrwxrwxrwx  1 root root      22 2008-12-23 15:34 libqscintilla.so.7.0 ->
libqscintilla.so.7.0.1
-rw-r--r--  1 root root  1424864 2007-10-24 16:50 libqscintilla.so.7.0.1

i do not find anything on internet and don't know what i can do to solve my
problem. Could anyone suggest me what do i do wrong? thank you.

Andrea

---

### Post by sismo on 2009-01-29
Same problem here

$ tora
Segmentation fault

$ dmesg | grep -i segfault
[ 3524.567798] tora[10142]: segfault at 0 ip b7086973 sp bff67e30 error 4 in libqscintilla2.so.3.0.0[b7025000+16f000]

also using 8.10 

Any ideas? :(

---

### Post by mike.wilmoth on 2009-04-25
On 8.10, try installing libqscintilla2-3.  That worked for me.

On 9.04, I am having the same issue and installing  libqscintilla2-3 doesn't fix the issue.

---

### Post by mike.wilmoth on 2009-04-25
For Ubuntu 9.04, there appear to changes in package libqscintilla2-3.  TOra is looking for libqscintilla2.so.3, but libqscintilla2.so.5.  You can make a symbolic link, and TOra will come up, there are stability issues - as soon as I try to connect to a connection, the program exits with a error: symbol lookup error: tora: undefined symbol: _ZN13QsciScintilla10setFoldingENS_9FoldStyleE

I installed the libqscintilla2-3 package from intreprid, and TOra seems to working correctly.  

Mike

---

### Post by dusk33 on 2009-04-29
hello. first of all sorry for my bad English.

I change the lib file and tora start and work properly. It was yesterday.
But when I start it today, I have the next problem:

tora opens normally. I select Oracle (instant client) connection.
"Unable to connect......" - its normal, and always  be so.
I close error message, and try to open menu File. When I click it Tora terminate wiyh message "Aborted"

Anybody have the same problem?

Kubuntu 9.04, Tora - deb package for intrepid. libqscintilla from Intrepid

---

### Post by huangyy on 2009-05-06
i have same question.

---

### Post by huangyy on 2009-05-07
haha, i resolve this problem
because, tora 2.0 base qt 4.4, and the qt that 9.04 includes is 4.5, so run tora 2.0 in 9.04 will got error.
to resolve this is to rebuild tora from source.
1. run configure
2. before make, should change some source file.
   in src path, change all the file that named moc_to*.cpp:
#elif Q_MOC_OUTPUT_REVISION != 59
change to:
#elif Q_MOC_OUTPUT_REVISION != 61
3. make, make install

is ok!

---

### Post by gombihu on 2009-06-18
Didn't work for me:
moc_utils.cpp:14:2: error: #error "This file was generated using the moc from 4.4.0. It"
moc_utils.cpp:15:2: error: #error "cannot be used with the include files from this version of Qt."
moc_utils.cpp:16:2: error: #error "(The moc has changed too much.)"
make[3]: *** [tora-moc_utils.o] Error 1

---


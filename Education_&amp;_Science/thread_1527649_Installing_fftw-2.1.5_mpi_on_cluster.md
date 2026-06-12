---
title: "Installing fftw-2.1.5 mpi on cluster"
date: 2010-07-09
forum: Education &amp; Science
---

### Post by lemafyoyo on 2010-07-09
Hi,
I have to make some tests of fftw on a cluster.
I first installed it on my own machine, and started the fftw_test session.
Now I need to install it on a cluster.

What I did is :

./configure --enable-mpi=/opt/mpich2/ --prefix /home/../fftw-2.1.5?
make
make install

I get no problem and no warning when I do it.
After this I would like to start fftw_mpi_test, but I only have fftw_mpi_test.c
I found on the web
1  gcc -c test_sched.c -o test_sched.o
2  gcc -I/usr/lib/mpich/include -I../tests -c fftw_mpi_test.c -o fftw_mpi_test.o
3  gcc -I/usr/lib/mpich/include -I../tests -c rfftw_mpi_test.c -o rfftw_mpi_test.o
4  gcc -I/usr/lib/mpich/include -c test_transpose_mpi.c -o test_transpose_mpi.o
5  gcc -lfftw_mpi test_sched.o -o test_sched
6  gcc -lfftw_mpi fftw_mpi_test.o ../tests/test_main.o -o fftw_mpi_test
7  gcc -lrfftw_mpi rfftw_mpi_test.o ../tests/test_main.o -o rfftw_mpi_test
8  gcc -lfftw_mpi test_transpose_mpi.o -o test_transpose_mpi
But when I arrive line 5, it can't get -lfftw_mpi, and I don't have any fftw_mpi file.
What can I do?

THx for your answers.

PS sry for my bad english

---

### Post by Azrael3000 on 2010-07-11
sorry I have never done this, but from what I can see is that you try to link you test_sched in line 5. And you also want to link you fftw_mpi installation (aka fftw library). The problem I think is that the library can't be found in your LD_LIBRARY_PATH.

So I don't know where your fftw_mpi library is, or what it's name has. According to you configuration you should have it somewhere in /home/../fftw-2.1.5 maybe in a directory called lib (try to search for *.so files). You would need to add this path to your LD_LIBRARY_PATH and then things should work.

I'm not sure whether this will work, but either way it shouldn't do any harm.

In case it works you need to permanently add this folder to your LD_LIBRARY_PATH. Your favorite search engine will tell you how to do it.

HTH,
Arno

---

### Post by lemafyoyo on 2010-07-12
Hey,
I found my problem.
During installation I was linking mpi directory, but it wasn't installing it correctly.
ANd it didn't tel me anything about it in the verbose.
Now it's working, it automatically created fftw_mpi_test.
Thanks for your help.
CIao

---


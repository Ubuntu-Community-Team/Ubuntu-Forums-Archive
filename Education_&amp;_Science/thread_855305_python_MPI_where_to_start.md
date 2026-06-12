---
title: "python MPI where to start?"
date: 2008-07-10
forum: Education &amp; Science
---

### Post by ssam on 2008-07-10
Hi

I'd like to have a go at using MPI with python to write some simulation code, but i am not really sure where to start.

It seems that there are many python MPI modules. pyMPI, mpi4pi, PyPar etc.
ubuntu has a package called python-mpi which i think is the scipy version (pyMPI).

is this a good choice, or should i build one of the others?

pyMPI (if thats what it is comes with an example)

but if i run it i get an error:
```

sam@oberon:~/docs/computer/python/mpi$ python mpi.py 
Traceback (most recent call last):
  File "mpi.py", line 12, in <module>
    communicator.send(data, 1, 0)
  File "/usr/lib/python2.5/site-packages/Scientific/MPI/core.py", line 301, in send
    raise MPIError, "invalid MPI destination"
Scientific.MPI.core.MPIError: invalid MPI destination

```

I think maybe i have to run it with an mpi program. but i dont get any further.
```

sam@oberon:~/docs/computer/python/mpi$ mpirun mpi.py
mpirun: application schema syntax error, line 1

```

```

sam@oberon:~/docs/computer/python/mpi$ mpipython.mpich mpi.py
Traceback (most recent call last):
  File "mpi.py", line 12, in <module>
    communicator.send(data, 1, 0)
Scientific.MPI.core.MPIError: invalid MPI destination
*** glibc detected *** mpipython.mpich: munmap_chunk(): invalid pointer: 0x00007f0837394230 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x7f0836181d46]
mpipython.mpich[0x40fbd4]
/usr/lib/libpython2.5.so.1.0[0x7f0836f81f6d]
/usr/lib/libpython2.5.so.1.0(PyDict_SetItem+0x7f)[0x7f0836f83d5f]
/usr/lib/libpython2.5.so.1.0(_PyModule_Clear+0x167)[0x7f0836f85fb7]
/usr/lib/libpython2.5.so.1.0(PyImport_Cleanup+0x3de)[0x7f0836fe886e]
/usr/lib/libpython2.5.so.1.0(Py_Finalize+0xb9)[0x7f0836ff4659]
/usr/lib/libpython2.5.so.1.0(Py_Main+0x481)[0x7f0836ffe7f1]
mpipython.mpich(main+0x41)[0x40f8c9]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f08361281c4]
mpipython.mpich[0x40f7f9]
======= Memory map: ========
00400000-0045c000 r-xp 00000000 08:0a 34616                              /usr/bin/mpipython.mpich
0065c000-0065f000 rw-p 0005c000 08:0a 34616                              /usr/bin/mpipython.mpich
0065f000-0085c000 rw-p 0065f000 00:00 0                                  [heap]
7f0830cf9000-7f0830d00000 r-xp 00000000 08:0a 106959                     /usr/lib/python2.5/lib-dynload/operator.so
7f0830d00000-7f0830f00000 ---p 00007000 08:0a 106959                     /usr/lib/python2.5/lib-dynload/operator.so
7f0830f00000-7f0830f02000 rw-p 00007000 08:0a 106959                     /usr/lib/python2.5/lib-dynload/operator.so
7f0830f02000-7f0830f06000 r-xp 00000000 08:0a 108379                     /usr/lib/python2.5/lib-dynload/_locale.so
7f0830f06000-7f0831106000 ---p 00004000 08:0a 108379                     /usr/lib/python2.5/lib-dynload/_locale.so
7f0831106000-7f0831107000 rw-p 00004000 08:0a 108379                     /usr/lib/python2.5/lib-dynload/_locale.so
7f0831107000-7f0831148000 rw-p 7f0831107000 00:00 0 
7f0831148000-7f0831237000 r-xp 00000000 08:0a 34868                      /usr/lib/libstdc++.so.6.0.9
7f0831237000-7f0831437000 ---p 000ef000 08:0a 34868                      /usr/lib/libstdc++.so.6.0.9
7f0831437000-7f083143d000 r--p 000ef000 08:0a 34868                      /usr/lib/libstdc++.so.6.0.9
7f083143d000-7f0831440000 rw-p 000f5000 08:0a 34868                      /usr/lib/libstdc++.so.6.0.9
7f0831440000-7f0831453000 rw-p 7f0831440000 00:00 0 
7f0831453000-7f083151e000 r-xp 00000000 08:0a 34578                      /usr/lib/libapt-pkg-libc6.7-6.so.4.6.0
7f083151e000-7f083171d000 ---p 000cb000 08:0a 34578                      /usr/lib/libapt-pkg-libc6.7-6.so.4.6.0
7f083171d000-7f0831720000 rw-p 000ca000 08:0a 34578                      /usr/lib/libapt-pkg-libc6.7-6.so.4.6.0
7f0831720000-7f0831721000 rw-p 7f0831720000 00:00 0 
7f0831721000-7f0831744000 r-xp 00000000 08:0a 107697                     /usr/lib/python2.5/site-packages/apt_pkg.so
7f0831744000-7f0831944000 ---p 00023000 08:0a 107697                     /usr/lib/python2.5/site-packages/apt_pkg.so
7f0831944000-7f0831949000 rw-p 00023000 08:0a 107697                     /usr/lib/python2.5/site-packages/apt_pkg.so
7f0831949000-7f0831a4b000 rw-p 7f0831949000 00:00 0 
7f0831a4b000-7f0831a4f000 r-xp 00000000 08:0a 106971                     /usr/lib/python2.5/lib-dynload/zlib.so
7f0831a4f000-7f0831c4f000 ---p 00004000 08:0a 106971                     /usr/lib/python2.5/lib-dynload/zlib.so
7f0831c4f000-7f0831c51000 rw-p 00004000 08:0a 106971                     /usr/lib/python2.5/lib-dynload/zlib.so
7f0831c51000-7f0831c8a000 r-xp 00000000 08:0a 108458                     /usr/lib/python2.5/lib-dynload/pyexpat.so
7f0831c8a000-7f0831e89000 ---p 00039000 08:0a 108458                     /usr/lib/python2.5/lib-dynload/pyexpat.so
7f0831e89000-7f0831e8d000 rw-p 00038000 08:0a 108458                     /usr/lib/python2.5/lib-dynload/pyexpat.so
7f0831e8d000-7f0831f0f000 rw-p 7f0831e8d000 00:00 0 
7f0831f0f000-7f0831f11000 r-xp 00000000 08:0a 106953                     /usr/lib/python2.5/lib-dynload/grp.so
7f0831f11000-7f0832110000 ---p 00002000 08:0a 106953                     /usr/lib/python2.5/lib-dynload/grp.so
7f0832110000-7f0832111000 rw-p 00001000 08:0a 106953                     /usr/lib/python2.5/lib-dynload/grp.so
7f0832111000-7f0832127000 r-xp 00000000 08:0a 34943                      /usr/lib/libz.so.1.2.3.3
7f0832127000-7f0832327000 ---p 00016000 08:0a 34943                      /usr/lib/libz.so.1.2.3.3
7f0832327000-7f0832328000 rw-p 00016000 08:0a 34943                      /usr/lib/libz.so.1.2.3.3
7f0832328000-7f0832482000 r-xp 00000000 08:0a 36721                      /usr/lib/libcrypto.so.0.9.8
7f0832482000-7f0832682000 ---p 0015a000 08:0a 36721                      /usr/lib/libcrypto.so.0.9.8
7f0832682000-7f08326a5000 rw-p 0015a000 08:0a 36721                      /usr/lib/libcrypto.so.0.9.8
7f08326a5000-7f08326a8000 rw-p 7f08326a5000 00:00 0 
7f08326a8000-7f08326ec000 r-xp 00000000 08:0a 36722                      /usr/lib/libssl.so.0.9.8
7f08326ec000-7f08328ec000 ---p 00044000 08:0a 36722                      /usr/lib/libssl.so.0.9.8
7f08328ec000-7f08328f2000 rw-p 00044000 08:0a 36722                      /usr/lib/libssl.so.0.9.8
7f08328f2000-7f08328f6000 r-xp 00000000 08:0a 108388                     /usr/lib/python2.5/lib-dynload/_ssl.so
7f08328f6000-7f0832af6000 ---p 00004000 08:0a 108388                     /usr/lib/python2.5/lib-dynload/_ssl.so
7f0832af6000-7f0832af7000 rw-p 00004000 08:0a 108388                     /usr/lib/python2.5/lib-dynload/_ssl.so
7f0832af7000-7f0832b03000 r-xp 00000000 08:0a 106941                     /usr/lib/python2.5/lib-dynload/_socket.so
7f0832b03000-7f0832d02000 ---p 0000c000 08:0a 106941                     /usr/lib/python2.5/lib-dynload/_socket.so
7f0832d02000-7f0832d06000 rw-p 0000b000 08:0a 106941                     /usr/lib/python2.5/lib-dynload/_socket.so
7f0832d06000-7f0832d09000 r-xp 00000000 08:0a 106939                     /usr/lib/python2.5/lib-dynload/_random.so
7f0832d09000-7f0832f08000 ---p 00003000 08:0a 106939                     /usr/lib/python2.5/lib-dynload/_random.so
7f0832f08000-7f0832f09000 rw-p 00002000 08:0a 106939                     /usr/lib/python2.5/lib-dynload/_random.so
7f0832f09000-7f0832f4a000 rw-p 7f0832f09000 00:00 0 
7f0832f4a000-7f0832f4d000 r-xp 00000000 08:0a 106951                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f0832f4d000-7f083314c000 ---p 00003000 08:0a 106951                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f083314c000-7f083314e000 rw-p 00002000 08:0a 106951                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f083314e000-7f0833151000 r-xp 00000000 08:0a 106961                     /usr/lib/python2.5/lib-dynload/select.so
7f0833151000-7f0833351000 ---p 00003000 08:0a 106961                     /usr/lib/python2.5/lib-dynload/select.so
7f0833351000-7f0833352000 rw-p 00003000 08:0a 106961                     /usr/lib/python2.5/lib-dynload/select.so
7f0833352000-7f0833356000 r-xp 00000000 08:0a 106967                     /usr/lib/python2.5/lib-dynload/time.so
7f0833356000-7f0833555000 ---p 00004000 08:0a 106967                     /usr/lib/python2.5/lib-dynload/time.so
7f0833555000-7f0833557000 rw-p 00003000 08:0a 106967                     /usr/lib/python2.5/lib-dynload/time.so
7f0833557000-7f083355b000 r-xp 00000000 08:0a 106945                     /usr/lib/python2.5/lib-dynload/cStringIO.so
7f083355b000-7f083375a000 ---p 00004000 08:0a 106945                     /usr/lib/python2.5/lib-dynload/cStringIO.so
7f083375a000-7f083375c000 rw-p 00003000 08:0a 106945                     /usr/lib/python2.5/lib-dynload/cStringIO.so
7f083375c000-7f0833761000 r-xp 00000000 08:0a 106949                     /usr/lib/python2.5/lib-dynload/binascii.so
7f0833761000-7f0833960000 ---p 00005000 08:0a 106949                     /usr/lib/python2.5/lib-dynload/binascii.so
7f0833960000-7f0833961000 rw-p 00004000 08:0a 106949                     /usr/lib/python2.5/lib-dynload/binascii.so
7f0833961000-7f0833967000 r-xp 00000000 08:0a 106943                     /usr/lib/python2.5/lib-dynload/_struct.so
7f0833967000-7f0833b67000 ---p 00006000 08:0a 106943                     /usr/lib/python2.5/lib-dynload/_struct.so
7f0833b67000-7f0833b69000 rw-p 00006000 08:0a 106943                     /usr/lib/python2.5/lib-dynload/_struct.so
7f0833b69000-7f0833baa000 rw-p 7f0833b69000 00:00 0 
7f0833baa000-7f0833bb7000 r-xp 00000000 08:0a 2662463                    /lib/libgcc_s.so.1
7f0833bb7000-7f0833db7000 ---p 0000d000 08:0a 2662463                    /lib/libgcc_s.so.1
7f0833db7000-7f0833db8000 rw-p 0000d000 08:0a 2662463                    /lib/libgcc_s.so.1
7f0833db8000-7f0833e76000 r-xp 00000000 08:0a 1584066                    /usr/lib/libgfortran.so.2.0.0
7f0833e76000-7f0834075000 ---p 000be000 08:0a 1584066                    /usr/lib/libgfortran.so.2.0.0
7f0834075000-7f0834077000 rw-p 000bd000 08:0a 1584066                    /usr/lib/libgfortran.so.2.0.0
7f0834077000-7f08340f1000 r-xp 00000000 08:0a 34635                      /usr/lib/libblas.so.p0_7034:  p4_error: interrupt SIGx: 6

```

```

sam@oberon:~/docs/computer/python/mpi$ mpipython.lam mpi.py
Traceback (most recent call last):
  File "mpi.py", line 12, in <module>
    communicator.send(data, 1, 0)
Scientific.MPI.core.MPIError: invalid MPI destination

```

i think i am probably doing something wrong. any pointers?

---

### Post by ssam on 2008-07-11
i found this thread [http://groups.google.com/group/comp.lang.python/browse_thread/thread/861a511d289cdc1f/74b8d9fbf3592b42?lnk=gst&q=mpi](http://groups.google.com/group/comp.lang.python/browse_thread/thread/861a511d289cdc1f/74b8d9fbf3592b42?lnk=gst&q=mpi) where Robert Kern says

> 
The people who I know who use MPI and Python have been using mpi4py. I haven't
used it myself, though.
[http://mpi4py.scipy.org/](http://mpi4py.scipy.org/)


he seems to be a regular poster in that forum, so i'll trust him.

mpi4py seems to have had a 0.5 release on 2007-07-31 and to have an exciting new (and not ready yet) branch based on cython at [http://code.google.com/p/mpi4py/](http://code.google.com/p/mpi4py/)

==== updated findings
from the svn mpi4py 0.6.0 was tagged in june [http://projects.scipy.org/mpi4py/browser/mpi4py/tags](http://projects.scipy.org/mpi4py/browser/mpi4py/tags) there is a tarball at [http://pypi.python.org/pypi/mpi4py/0.6.0](http://pypi.python.org/pypi/mpi4py/0.6.0)

---


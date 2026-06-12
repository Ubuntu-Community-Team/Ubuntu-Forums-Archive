---
title: "Cedega Error on Install"
date: 2005-10-18
forum: Gaming &amp; Leisure
---

### Post by EnderTheThird on 2005-10-18
I followed the instructions [here]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45") for installing Cedega but didn't have any luck.  I get the following error during make:
```
--------- Error log - file /home/phil/.WineCVS/sources/cvscedega/ErrorLog : ---------o to http://www.transgaming.com/ for more info.
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o gdbremote.o gdbremote.c
make: *** Waiting for unfinished jobs....
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o handle.o handle.c
gcc -shared -Wl,-soname,libwine_tsx11.so  locking.o ts_xf86dga.o ts_xf86dga2.o ts_xf86vmode.o ts_xshm.o ts_xlib.o ts_xresource.o ts_xvideo.o ts_xutil.o ts_shape.o      -o libwine_tsx11.so.1.0 -L/usr/X11R6/lib -lSM -lICE -lXv -lGL -lGLU -lXext -lX11
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mapping.o mapping.c
rm -f libwine_tsx11.so && ln -s libwine_tsx11.so.1.0 libwine_tsx11.so
handle.c: In function ‘enum_objects’:
handle.c:615: warning: pointer targets in passing argument 3 of ‘cb’ differ in signedness
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tsx11'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mem_malloc.o mem_malloc.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mutex.o mutex.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o named_pipe.o named_pipe.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o object.o object.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o process.o process.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o ptrace.o ptrace.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o queue.o queue.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o registry.o registry.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o request.o request.c
request.c: In function ‘master_socket_poll_event’:
request.c:486: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
registry.c: In function ‘load_value’:
registry.c:1205: warning: pointer targets in passing argument 1 of ‘parse_hex’ differ in signedness
registry.c: In function ‘req_get_key_value’:
registry.c:1709: warning: pointer targets in passing argument 4 of ‘get_value’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o rpc_epmap.o rpc_epmap.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o select.o select.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o semaphore.o semaphore.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o serial.o serial.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o shm.o shm.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o snapshot.o snapshot.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o sock.o sock.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o thread.o thread.c
sock.c: In function ‘accept_socket’:
sock.c:657: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o timer.o timer.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o trace.o trace.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o unicode.o unicode.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o user.o user.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o window.o window.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o token.o token.c
gcc -shared -Wl,-soname,libwineserver.so async.o atom.o cdrom_eject.o change.o console.o context_i386.o context_sparc.o debugger.o device.o distributed.o event.o fd_server.o file.o gdbremote.o handle.o mapping.o mem_malloc.o mutex.o named_pipe.o object.o process.o ptrace.o queue.o registry.o request.o rpc_epmap.o select.o semaphore.o serial.o shm.o snapshot.o sock.o thread.o timer.o trace.o unicode.o user.o window.o token.o -o libwineserver.so.1.0
rm -f libwineserver.so && ln -s libwineserver.so.1.0 libwineserver.so
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/server'


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
```

I installed fglrx for my Radeon 9800 AIW and I have no idea what the actual error is.  I'll post the ErrorLog that was produced in a separate post, seeing as it puts me over the character limit if I put it here.  Any help?

---

### Post by EnderTheThird on 2005-10-18
ErrorLog:
```

make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/port'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o port.o port.c
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/server'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o async.o async.c
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/unicode'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o atom.o atom.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o mmap.o mmap.c
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/library'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -DUSE_PTHREADS -D_REENTRANT  -o debug.o debug.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o cdrom_eject.o cdrom_eject.c
gcc -shared -Wl,-soname,libwine_port.so  port.o mmap.o      -ldl -lm  -o libwine_port.so.1.0
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -DUSE_PTHREADS -D_REENTRANT  -o errno.o errno.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -DUSE_PTHREADS -D_REENTRANT  -o ldt.o ldt.c
rm -f libwine_port.so && ln -s libwine_port.so.1.0 libwine_port.so
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/port'
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/ole'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o uuid.o uuid.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -DUSE_PTHREADS -D_REENTRANT  -o loader.o loader.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o change.o change.c
loader.c: In function ‘map_dll’:
loader.c:205: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
loader.c:215: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o console.o console.c
gcc -shared -Wl,-soname,libwine.so  debug.o errno.o ldt.o loader.o      -ldl -lpthread -lm  -o libwine.so.1.0
rm -f libwine.so && ln -s libwine.so.1.0 libwine.so
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/library'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o context_i386.o context_i386.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o context_sparc.o context_sparc.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o debugger.o debugger.c
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tsx11'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o locking.o locking.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xf86dga.o ts_xf86dga.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xf86dga2.o ts_xf86dga2.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o device.o device.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xf86vmode.o ts_xf86vmode.c
rm -f libwine_uuid.a
ar rc libwine_uuid.a uuid.o
ranlib libwine_uuid.a
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xshm.o ts_xshm.c
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/ole'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o distributed.o distributed.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xlib.o ts_xlib.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o event.o event.c
rm -f libwine.so && ln -s library/libwine.so libwine.so
rm -f libwine_uuid.a && ln -s ole/libwine_uuid.a libwine_uuid.a
make[1]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o fd_server.o fd_server.c
make[2]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/winebuild'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xresource.o ts_xresource.c
fd_server.c: In function ‘fd_server_poll_event’:
fd_server.c:114: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xvideo.o ts_xvideo.c
make[2]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/winedump'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o file.o file.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_xutil.o ts_xutil.c
make[2]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o ts_shape.o ts_shape.c
file.c: In function ‘req_set_file_pointer’:
file.c:692: warning: pointer targets in passing argument 2 of ‘set_file_pointer’ differ in signedness
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o gdbremote.o gdbremote.c
make: *** Waiting for unfinished jobs....
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o handle.o handle.c
gcc -shared -Wl,-soname,libwine_tsx11.so  locking.o ts_xf86dga.o ts_xf86dga2.o ts_xf86vmode.o ts_xshm.o ts_xlib.o ts_xresource.o ts_xvideo.o ts_xutil.o ts_shape.o      -o libwine_tsx11.so.1.0 -L/usr/X11R6/lib -lSM -lICE -lXv -lGL -lGLU -lXext -lX11 
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mapping.o mapping.c
rm -f libwine_tsx11.so && ln -s libwine_tsx11.so.1.0 libwine_tsx11.so
handle.c: In function ‘enum_objects’:
handle.c:615: warning: pointer targets in passing argument 3 of ‘cb’ differ in signedness
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/tsx11'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mem_malloc.o mem_malloc.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o mutex.o mutex.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o named_pipe.o named_pipe.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o object.o object.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o process.o process.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o ptrace.o ptrace.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o queue.o queue.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o registry.o registry.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o request.o request.c
request.c: In function ‘master_socket_poll_event’:
request.c:486: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
registry.c: In function ‘load_value’:
registry.c:1205: warning: pointer targets in passing argument 1 of ‘parse_hex’ differ in signedness
registry.c: In function ‘req_get_key_value’:
registry.c:1709: warning: pointer targets in passing argument 4 of ‘get_value’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o rpc_epmap.o rpc_epmap.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o select.o select.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o semaphore.o semaphore.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o serial.o serial.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o shm.o shm.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o snapshot.o snapshot.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o sock.o sock.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o thread.o thread.c
sock.c: In function ‘accept_socket’:
sock.c:657: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o timer.o timer.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o trace.o trace.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o unicode.o unicode.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o user.o user.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o window.o window.c
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -DSTDHEADERS -D_REENTRANT  -o token.o token.c
gcc -shared -Wl,-soname,libwineserver.so async.o atom.o cdrom_eject.o change.o console.o context_i386.o context_sparc.o debugger.o device.o distributed.o event.o fd_server.o file.o gdbremote.o handle.o mapping.o mem_malloc.o mutex.o named_pipe.o object.o process.o ptrace.o queue.o registry.o request.o rpc_epmap.o select.o semaphore.o serial.o shm.o snapshot.o sock.o thread.o timer.o trace.o unicode.o user.o window.o token.o -o libwineserver.so.1.0
rm -f libwineserver.so && ln -s libwineserver.so.1.0 libwineserver.so
make[1]: Leaving directory `/home/phil/.WineCVS/sources/cvscedega/winex/server'

```

---

### Post by Goober on 2005-10-18
I have this same problem, and I know at least one other person does, so I am eargerly awaiting the solution.

---

### Post by Mustard on 2005-10-19
I finally managed to builld cvswine from CVS, on breezy, after following the guide at transgaming.  I tried a HOW TO that's in this forum, but it turned out to be the 'HOW TO FROM HELL', as some of the packages were different from what I could find in the breezy repositories.  I tried the 'bleeding edge' CVS profile, but it wouldn't compile, so I tried the 'regular' profile, and it compiled and installed with no problems.

It's a bit difficult for me to document how I did it, as a lot of the dependencies I had already installed in previous attempts to get either wine or cedega to compile.  I'd need to start from scratch with a clean install to work out exactly which packages were mandatory for a successful install.

---


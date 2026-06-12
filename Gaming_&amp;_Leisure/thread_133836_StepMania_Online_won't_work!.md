---
title: "StepMania Online won't work!"
date: 2006-02-20
forum: Gaming &amp; Leisure
---

### Post by wr0x2 on 2006-02-20
```
wr0x2@USSENTERPRISE:~/StepMania CVS 05-22-2005$ ./stepmania
./stepmania: error while loading shared libraries: liblua.so: cannot open shared object file: No such file or directory

```

I installed all of the lua libraries from apt, so I know I'm not missing any. I have read something about symlinks getting this working but I'm not entierly sure what to do. For anyone else that's gotten SMO working on breezy, please tell how. 

Oh, and regular singleplayer SM 3.9 works fine.

---

### Post by wr0x2 on 2006-02-21
Well, for some reason SMO does nto give me the library errors when I run it as root... but then...

```

wr0x2@USSENTERPRISE:~/Desktop/SMCVS$ sudo ./stepmania
StepMania 3.9 3.9 SMO CVS 05-22-2005
Log starting 2006-02-21 17:00:17
Loading window: gtk
OS: Linux ver 020612
Runtime library: glibc 2.3.5
Threads library: NPTL 2.3.5
TLS is available
Segmentation fault

```

Segmentation fault?

---

### Post by gerbman on 2006-02-21
[QUOTE=wr0x2]./stepmania: error while loading shared libraries: liblua.so: cannot open shared object file: No such file or directory[/QUOTE]What does ```
ls -l /usr/lib | grep liblua
``` output?

---

### Post by wr0x2 on 2006-02-21
```

wr0x2@USSENTERPRISE:~$ ls -l /usr/lib | grep liblua
lrwxrwxrwx   1 root  root       15 2006-01-15 12:57 liblua40.so.4 -> liblua40.so.4.0
-rw-r--r--   1 root  root    72796 2004-10-26 23:28 liblua40.so.4.0
-rw-r--r--   1 root  root   172924 2004-10-26 11:39 liblua50.a
lrwxrwxrwx   1 root  root       15 2006-01-15 13:05 liblua50.so -> liblua50.so.5.0
lrwxrwxrwx   1 root  root       15 2006-01-15 12:58 liblua50.so.5 -> liblua50.so.5.0
-rwxr-x---   1 root  root   118020 2004-10-26 11:39 liblua50.so.5.0
-rw-r--r--   1 root  root    89404 2004-10-26 11:39 liblualib50.a
lrwxrwxrwx   1 root  root       18 2006-01-15 13:05 liblualib50.so -> liblualib50.so.5.0
lrwxrwxrwx   1 root  root       18 2006-01-15 12:58 liblualib50.so.5 -> liblualib50.so.5.0
-rw-r--r--   1 root  root    68728 2004-10-26 11:39 liblualib50.so.5.0
lrwxrwxrwx   1 root  root       23 2006-01-28 12:06 liblualib.so -> /usr/lib/liblualib50.so
lrwxrwxrwx   1 wr0x2 root       20 2006-01-28 12:06 liblua.so -> /usr/lib/liblua50.so

```
my liblua.so link should be readible by all, right? Why then must I run the app as root, and why does it crash when I run it? I used to be able to start it as root, and it would not crash...

---

### Post by gerbman on 2006-02-21
[QUOTE=wr0x2]my liblua.so link should be readible by all, right? Why then must I run the app as root, and why does it crash when I run it? I used to be able to start it as root, and it would not crash...[/QUOTE]

Yes it should be readable, that's really odd that it says it can't find it. What does ```
ldd <stepmania executable>
```output?

---

### Post by wr0x2 on 2006-02-22
```

wr0x2@USSENTERPRISE:~/Desktop/SMCVS$ ldd stepmania
        linux-gate.so.1 =>  (0xffffe000)
        libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0xb7f7a000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7f53000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7f4e000)
        libmad.so.0 => /usr/lib/libmad.so.0 (0xb7f37000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7eaf000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e8c000)
        libXtst.so.6 => /usr/lib/libXtst.so.6 (0xb7e87000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7de8000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7d72000)
        libavformat.so => /usr/lib/libavformat.so (0xb7d1a000)
        libavcodec.so => /usr/lib/libavcodec.so (0xb7b30000)
        libpng.so.3 => /usr/lib/libpng.so.3 (0xb7b0b000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7af7000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7ad8000)
        liblua.so => not found
        liblualib.so => /usr/lib/liblualib.so (0xb7ac7000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7a0d000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb79ea000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb79df000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb78b1000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb78ae000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb77ee000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb77e1000)
        /lib/ld-linux.so.2 (0xb7f85000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb76fa000)
        liblua50.so.5.0 => not found
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb76f7000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb76f3000)

```

and when I run it as root...

```

wr0x2@USSENTERPRISE:~/Desktop/SMCVS$ sudo ldd stepmania
Password:
        linux-gate.so.1 =>  (0xffffe000)
        libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0xb7fa5000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7f7e000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7f79000)
        libmad.so.0 => /usr/lib/libmad.so.0 (0xb7f62000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7eda000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7eb7000)
        libXtst.so.6 => /usr/lib/libXtst.so.6 (0xb7eb2000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e13000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7d9d000)
        libavformat.so => /usr/lib/libavformat.so (0xb7d45000)
        libavcodec.so => /usr/lib/libavcodec.so (0xb7b5b000)
        libpng.so.3 => /usr/lib/libpng.so.3 (0xb7b36000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7b22000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7b03000)
        liblua.so => /usr/lib/liblua.so (0xb7ae5000)
        liblualib.so => /usr/lib/liblualib.so (0xb7ad4000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7a1a000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb79f7000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb79ec000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb78be000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb78bb000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb77fb000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb77ee000)
        /lib/ld-linux.so.2 (0xb7fb0000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7707000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7704000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7700000)

```

...it finds my liblua library...

---

### Post by wr0x2 on 2006-02-22
OK, I had another look at the permissions for liblua.so.5.0, which was the library my link eventually referenced. It was not readible by my user so I did a chmod 777 to it (full perms) and now I can start stepmania as a regular user... Unfortunatly, now we're back to the same error I posted earlier, which is:

```

wr0x2@USSENTERPRISE:~/Desktop/SMCVS$ sudo ./stepmania
StepMania 3.9 3.9 SMO CVS 05-22-2005
Log starting 2006-02-21 17:00:17
Loading window: gtk
OS: Linux ver 020612
Runtime library: glibc 2.3.5
Threads library: NPTL 2.3.5
TLS is available
Segmentation fault

```

---

### Post by wr0x2 on 2006-02-22
So no one knows why the app gives the error "segmentation fault"?

---

### Post by gerbman on 2006-02-22
[QUOTE=wr0x2]So no one knows why the app gives the error "segmentation fault"?[/QUOTE]

Hmmm, not really. Did you get the install from [here]("http://www.stepmania.com/wiki/Downloads") or somewhere else? That installer worked fine for me after doing the symlinks.

---

### Post by wr0x2 on 2006-02-23
I'm not having problems running regular stepmania, it runs fine and did not even have a problem with libraries. I'm having trouble running stepmania *online*, which I downloaded [here]("http://www.stepmaniaonline.com/index.php?mod=Downloads&id=8").

---

### Post by wr0x2 on 2006-02-26
*bump*

---

### Post by wr0x2 on 2006-03-06
I guess I'll let it die if no one answers this bump... The SMO site has over 1000 (ok, maybe that's not a lot) linux downloads, surely SOMEONE must know how to get it working...

---


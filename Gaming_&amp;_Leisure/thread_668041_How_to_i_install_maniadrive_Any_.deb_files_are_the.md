---
title: "How to i install maniadrive? Any .deb files are there"
date: 2008-01-15
forum: Gaming &amp; Leisure
---

### Post by melwinabraham on 2008-01-15
I downloaded maniadrive 1.2 from internet its screen shots are awesome.but i dont know how to install the tar.gz file. If any deb files for maniadrive reply me
or help me to how to make deb files

---

### Post by melwinabraham on 2008-01-15
[http://www.getdeb.net/app.php?name=ManiaDrive](http://www.getdeb.net/app.php?name=ManiaDrive)

Check this

---

### Post by Praadur on 2008-01-15
Ooh, this looks like fun!  It's a shame there's not an amd64 deb yet though, but I'll keep my eye out for that.  I'd have a go at compiling it myself but from the forums it seems like a complicated procedure, and my mind isn't in any state for complicated builds at the moment!  Still, I might just have a go at compiling this one eventually, I certainly did love Trackmania.

---

### Post by meeezo333eg on 2009-03-26
> **melwinabraham said:**
> I downloaded maniadrive 1.2 from internet its screen shots are awesome.but i dont know how to install the tar.gz file. If any deb files for maniadrive reply me
or help me to how to make deb files

extract the archive

 just dbl click mania_drive.sh

---

### Post by hikaricore on 2009-03-26
[http://www.getdeb.net/release/4093](http://www.getdeb.net/release/4093)

---

### Post by diarmuid_mcdaid on 2009-11-10
Could someone give me instructions how to install from tar.gz, as the .deb link is dead. Many thanks!

---

### Post by kinggo on 2009-12-26
You can use the interpid packages found here.
[http://old.getdeb.net/search.php?search_distro_id=11&keywords=maniadrive](http://old.getdeb.net/search.php?search_distro_id=11&keywords=maniadrive)
Works fine in jaunty.

---

### Post by giancarlocp on 2010-12-20
Hello, i try to install ManiaDrive on Maverick (10.10)

download ManiaDrive source from [raydium]("http://maniadrive.raydium.org/index.php?downloads=yes")
> 
Sources (lite Raydium snapshot):
ManiaDrive 1.2 - sources (258 KB, tar.gz)


or try
```
$ wget http://ufpr.dl.sourceforge.net/project/maniadrive/maniadrive/1.2/ManiaDrive-1.2-src.tar.gz

```

then
```

$ tar xvzf ManiaDrive-1.2-src.tar.gz
$ cd ManiaDrive-1.2-src
    After some error i found those was needed.
$ sudo aptitude install libode-dev php5-dev bison libcurl4-gnutls-dev libxml2-dev libglu-dev libglew-dev libopenal-dev libalut-dev libogg-dev libvorbis-dev libjpeg-dev libxinerama-dev

$ ./configure
 * Testing gcc...         OK
 * Testing OpenGL...      OK
 * Testing GLU...         OK
 * Testing GL/GLU hardware support...   OK
 * Testing GLEW...        OK
 * Testing OpenAL...      OK
 * Testing OpenAL 1.1 and ALUT...       OK
 * Testing Ogg/Vorbis...  OK
 * Testing libjpeg...     OK
- Build system seems ready -
- Use "make" to build Raydium, and try: "./odyncomp.sh test6.c"
- You can also use "./ocomp.sh test6.c" for a quick direct test

    Jump this step, just describe what i did.
$ make
 :
 :
gcc: raydium/ode/lib/libode.a: No such file or directory
make: *** [libraydium.so.0.0] Error 1

$ find /usr/ -iname libode.a
/usr/lib/libode.a
$ cp /usr/lib/libode.a raydium/ode/lib/

$ make
File created: libraydium.a.0.0
/usr/bin/ld: raydium/compile/callback.o: relocation R_X86_64_32 against `raydium_window_resize_callback' can not be used when making a shared object; recompile with -fPIC
raydium/compile/callback.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libraydium.so.0.0] Error 1

```

Someone know what do i have to do?

---


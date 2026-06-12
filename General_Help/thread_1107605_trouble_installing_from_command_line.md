---
title: "trouble installing from command line"
date: 2009-03-26
forum: General Help
---

### Post by huitlacoche on 2009-03-26
Hi,

I'm a newcomer to linux and I was trying to install dmg2img through the command line. I followed the instructions but I get this error:

root@dustmaster-linux:~/Desktop/dmg2img-1.3# make
gcc -O2 -Wall -c dmg2img.c
In file included from dmg2img.c:30:
dmg2img.h:20:18: error: zlib.h: No such file or directory
In file included from dmg2img.c:30:
dmg2img.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘z’
dmg2img.c: In function ‘main’:
dmg2img.c:75: error: ‘Bytef’ undeclared (first use in this function)
dmg2img.c:75: error: (Each undeclared identifier is reported only once
dmg2img.c:75: error: for each function it appears in.)
dmg2img.c:75: error: ‘tmp’ undeclared (first use in this function)
dmg2img.c:75: error: ‘otmp’ undeclared (first use in this function)
dmg2img.c:75: warning: left-hand operand of comma expression has no effect
dmg2img.c:163: error: expected expression before ‘)’ token
dmg2img.c:164: error: expected expression before ‘)’ token
dmg2img.c:206: error: ‘z’ undeclared (first use in this function)
dmg2img.c:206: error: ‘alloc_func’ undeclared (first use in this function)
dmg2img.c:206: error: expected ‘;’ before numeric constant
dmg2img.c:207: error: ‘free_func’ undeclared (first use in this function)
dmg2img.c:207: error: expected ‘;’ before numeric constant
dmg2img.c:208: error: ‘voidpf’ undeclared (first use in this function)
dmg2img.c:208: error: expected ‘;’ before numeric constant
dmg2img.c:236: warning: implicit declaration of function ‘inflateInit’
dmg2img.c:236: error: ‘Z_OK’ undeclared (first use in this function)
dmg2img.c:250: warning: implicit declaration of function ‘inflateEnd’
dmg2img.c:260: warning: implicit declaration of function ‘inflate’
dmg2img.c:260: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
dmg2img.c:261: error: ‘Z_STREAM_ERROR’ undeclared (first use in this function)
dmg2img.c:263: error: ‘Z_NEED_DICT’ undeclared (first use in this function)
dmg2img.c:264: error: ‘Z_DATA_ERROR’ undeclared (first use in this function)
dmg2img.c:266: error: ‘Z_MEM_ERROR’ undeclared (first use in this function)
dmg2img.c:278: error: ‘Z_STREAM_END’ undeclared (first use in this function)
make: *** [dmg2img.o] Error 1


I guess I'm not really sure what I'm doing wrong or if its corrupt data.
What's the process for installing in the command line?

Thanks,
~mark

---

### Post by Lunx on 2009-03-26
With Ubuntu you don't need to try and install as root, you issue the sudo apt-get command eg.

```
sudo apt-get nameofapplication
```

If you are only new and want to learn more about the command line, I suggest starting of with a read through the [_Ubuntu Pocket Guide_]("http://www.ubuntupocketguide.com/")

---

### Post by ryanhaigh on 2009-03-27
> **Lunx said:**
> With Ubuntu you don't need to try and install as root, you issue the sudo apt-get command eg.

```
sudo apt-get nameofapplication
```

If you are only new and want to learn more about the command line, I suggest starting of with a read through the [_Ubuntu Pocket Guide_]("http://www.ubuntupocketguide.com/")

Unfortunately this application doesn't appear be in the ubuntu package archive: [http://packages.ubuntu.com/search?keywords=dmg2img](http://packages.ubuntu.com/search?keywords=dmg2img)

Sorry I can't be more helpful. I had a quick look in the source archive and there don't appear to be any instructions regarding compilation dependencies or abnormal procedures. The only thing I can suggest is that you install the package [apt://build-essential]("apt://build-essential") if you haven't already.

I did stumble across this with a quick google search:
[http://ubuntuforums.org/showthread.php?t=343808](http://ubuntuforums.org/showthread.php?t=343808)

---

### Post by lloyd_b on 2009-03-27
> **huitlacoche said:**
> Hi,

I'm a newcomer to linux and I was trying to install dmg2img through the command line. I followed the instructions but I get this error:

root@dustmaster-linux:~/Desktop/dmg2img-1.3# make
gcc -O2 -Wall -c dmg2img.c
In file included from dmg2img.c:30:
dmg2img.h:20:18: **error: zlib.h: No such file or directory**
In file included from dmg2img.c:30:
dmg2img.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘z’
dmg2img.c: In function ‘main’:
dmg2img.c:75: error: ‘Bytef’ undeclared (first use in this function)
...
make: *** [dmg2img.o] Error 1


I guess I'm not really sure what I'm doing wrong or if its corrupt data.
What's the process for installing in the command line?

Thanks,
~mark

Note the part I highlighted - looks like you're missing zlib.h, and most if not all of the remaining errors are a direct result of this.

You need to install the package "zlib1g-dev" to get this file ("sudo apt-get install zlib1g-dev", or use the package manager of your choice).

I'm surprised that this *isn't* already installed.  Have you installed the "build-essential" package?

Lloyd B.

---


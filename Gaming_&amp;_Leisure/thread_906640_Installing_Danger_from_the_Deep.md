---
title: "Installing Danger from the Deep"
date: 2008-08-31
forum: Gaming &amp; Leisure
---

### Post by Warthaug on 2008-08-31
I've been trying to install danger from the deep, V0.3.0, with nothing but a headache to show for it.

I've gone two routes; downloading the .bin, and installing with dpkg.  This gives an error stating that the package does not have the correct format.

I also tried downloading from the CVS and compiling.  I get the files A-OK, but when I try to compile using the command:

> scons debug=1 usex86sse=-1 datadir=/path/to/cvs/dangerdeep/data

I get the following error:

> 
scons: Reading SConscript files ...
Compiling for Unix/Posix/Linux Environment
grep: /usr/include/GL/gl*.h: No such file or directory
Install binary path: /usr/local/bin
Using data dir: /path/to/cvs/dangerdeep/data
Checking for C library GL... no
GL library must be installed!


I'm 99% sure openGL is installed, since openGL dependent programs are running fine, as does advanced compix features like the cube.  My video card is whatever dell provides in their laptops, I didn't bother upgrading that feature.

Thanx in advance

Bryan

PS: I'm a relative newbie, so be gentle...please ;)

---

### Post by eragon100 on 2008-08-31
You need to have the development (-dev) opengl libraries installed as well if you want to compile software that depends on opengl. Just search for them in synaptic :wink:

---

### Post by Perfect Storm on 2008-09-01
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```

---

### Post by Warthaug on 2008-09-01
So I ended up having to add about a dozen libraries; after the openGL-dev there were a few others I had to download.  All the libraries installed, I thought I was good to go.  Instead, the compiler could not find the files it needed in the dangerdeep directory.  After reading some other posts in other forums I've come to realize that compiling from source isn't going to happen, apparently the CVS is quite buggy right now.

So here's a question; does anyone know if its possible to "convert" a .bin file to something that ubuntu can recognize - either a .deb for the usual package managers, or something dpkg can handle?

thanx for the advice

Bryan

---

### Post by PeterBBB on 2008-09-03
There is a .deb package on the web site;  dangerdeep_0.3.0.1_i386.deb

_[http://dangerdeep.sourceforge.net/download.html](http://dangerdeep.sourceforge.net/download.html)_

It seems to install OK, but I can't get it to run. Craps out with .. 

```
SIGSEGV caught!
Stack trace: (12 frames)
0x8070202 in dangerdeep at ??:0
0x805d560 in dangerdeep at ??:0
0xffffe500 in [0xffffe500] at ??:0
0xf7a1954c in memcpy at ??:0
0xf7bb95a0 in std::string::append(std::string const&) at ??:0
0x806f72d in std::basic_string<char, std::char_traits<char>, std::allocator<char> > std::operator+<char, std::char_traits<char>, std::allocator<char> >(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) at ??:0
0x8156807 in dangerdeep at ??:0
0x806ac5e in dangerdeep at ??:0
0x806d3b2 in dangerdeep at ??:0
0x806d4f1 in dangerdeep at ??:0
0xf79bb450 in __libc_start_main at ??:0
0x804e6a1 in dangerdeep at ??:0
Aborting program.
Aborted
```

:-(

---

### Post by PeterBBB on 2008-09-03
> **Warthaug said:**
>  apparently the CVS is quite buggy right now.

Take 2.  Use the source from the web page

_[http://downloads.sourceforge.net/dangerdeep/dangerdeep-0.3.0.tar.gz](http://downloads.sourceforge.net/dangerdeep/dangerdeep-0.3.0.tar.gz)_

It builds and runs fine!


Pete :-)

---


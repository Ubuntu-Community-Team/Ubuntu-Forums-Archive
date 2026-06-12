---
title: "what are 'lncurses'?"
date: 2009-06-10
forum: General Help
---

### Post by blurt on 2009-06-10
I did an install of freebasic and geany; the geany works fine compiling
cpp files using the gcc compiler, but when I try to compile a .bas file
I get "cannot find -lncurses, compilation not completed". I know the libs
and includes for the freebasic are present. I have never gotten a message
about 'lncurses' before.Using 8.10. --blurt.:(

---

### Post by Chronon on 2009-06-10
I think this will explain what it is:

[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

---

### Post by jyaan on 2009-06-10
Yea, -l is a flag for libraries. So it's just saying that it can't find the library ncurses. You'll need to install it.

---

### Post by blurt on 2009-06-10
Well, I got strange news and better news; I downloaded ncurses-5.7. Got some
idea from a 'readme' in there to do: sudo ./configure; wheee!! impressive;
can't figure what to do from there. Back to geany, still can't find lncurses. Better news: went to synaptic, searched on 'ncurses', found about
sixty files; checkboxed about fifty of them. Back to geany, NOW it compiles
.bas files; only problem? I have NO IDEA which of those fifty files did the
trick. Some folks find this charming about linux; some don't.--kurt.:cool:](*,)

---

### Post by kirsis on 2009-06-10
-lwhatever = file named libwhatever.so[.x.y]

-lncurses = likely a file named libncurses.so 

These libraries are usually in the "-dev" packages of the repository, likely "ncurses-dev"

---

### Post by CaptainEvilStomper on 2009-06-10
./configure only prepares the source files for installation - you still have to build and then install it, like this:

```
sudo ./configure
sudo make
sudo make install
```

Or you can consolidate everything on one line like this:

```
sudo ./configure && sudo make && sudo make install
```

Or you could do it the easy way and just install all the newest ncurses library packages:

```
sudo apt-get install libncurses*
```

---

### Post by jyaan on 2009-06-12
Yea, there is no reason to go through all the ./configure && make business for such a common library. Just install it with apt.

---

### Post by Malay37 on 2010-05-05
hi ,
 i am facing the same problem. when i write "mak menuconfig". It shows me an error. like:
[B]  HOSTLD  -static scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncursesw
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/mconf] Error 1
make: *** [menuconfig] Error 2[/B]

Please guide me.

---


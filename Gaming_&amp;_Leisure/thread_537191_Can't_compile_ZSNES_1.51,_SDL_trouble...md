---
title: "Can't compile ZSNES 1.51, SDL trouble..?"
date: 2007-08-28
forum: Gaming &amp; Leisure
---

### Post by DavidGX on 2007-08-28
Here's my output when I enter the src directory and try to compile..

```
 sh ./autogen.sh && gmake && gmake install
Generating build information using aclocal and autoconf...
./autogen.sh: 6: sdl-config: not found
aclocal: couldn't open directory `/share/aclocal': No such file or directory
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 3437: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3437: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
bash: gmake: command not found
```

I'm running fiesty (64bit) on an AMD64 processor. I've installed build-essential.

I see that SDL appears to be either missing or the wrong version, I've tried to install a newer version via synaptic but it still outputs the same message. It also appears I don't have "gmake" and I'm not sure how to solve that one as it's not showing up in synaptic.

Any ideas guys?

---

### Post by po0f on 2007-08-28
DavidGX,

Sorry I can't help with this specific problem, but the easiest way to make sure all dependencies are satisfied for a program you are going to compile from source *that's also available in the repos*:

```
$ sudo apt-get build-dep <package>
```

Whenever I compile zsnes, I go through the usual "./configure; make; sudo checkintall" dance; any reason you aren't?

[EDIT]

If you do get it compiled and use checkinstall to install it, make sure to set the version.  For some reason, zsnes in the repos reports it's version as 1.420 instead of 1.42, IIRC.  Just set the version to 1.510  This will try to downgrade zsnes on a system update, not what you want.  :)

---

### Post by DoktorSeven on 2007-08-28
You need the -dev version of SDL (the package name will end in "-dev").  Search Synaptic (or using apt-cache search) for **sdl dev**.  

**Anytime you are compiling something, you need the -dev package of a required library for what you are compiling.**  

Also, use simply **make** instead of "gmake".  "gmake" is for systems that implement their own versions of make and compiling requires the GNU version of make (thus the "g" in "gmake").

---

### Post by BoyOfDestiny on 2007-08-28
> **DavidGX said:**
> Here's my output when I enter the src directory and try to compile..

```
 sh ./autogen.sh && gmake && gmake install
Generating build information using aclocal and autoconf...
./autogen.sh: 6: sdl-config: not found
aclocal: couldn't open directory `/share/aclocal': No such file or directory
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 3437: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3437: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
bash: gmake: command not found
```

I'm running fiesty (64bit) on an AMD64 processor. I've installed build-essential.

I see that SDL appears to be either missing or the wrong version, I've tried to install a newer version via synaptic but it still outputs the same message. It also appears I don't have "gmake" and I'm not sure how to solve that one as it's not showing up in synaptic.

Any ideas guys?

Well not sure how well it will run 64-bit, I had it sort of working a while ago (I haven't run a 64-bit ubuntu since Breezy I think, and my desktop gave up the ghost after I moved...)

Try to install libsdl1.2-dev, and various other sdl-dev. And if I remember right you'll need something like ia32-libs.

Also,

./autogen.sh && make && sudo make install

Should do the trick for you :)

---

### Post by DavidGX on 2007-08-28
> **po0f said:**
> Whenever I compile zsnes, I go through the usual "./configure; make; sudo checkintall" dance; any reason you aren't?

Because I'm not the linux expert I'd like to be. I'll get there, though.

---

### Post by DavidGX on 2007-08-28
After getting sdl -dev files installed, switching to "make" instead of "gmake" it starting going, was looking great and then spat out this..

```
/usr/bin/ld: warning: i386 architecture of input file `endmem.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `init.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `vcache.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `ztime.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/c4proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp2proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp3proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp4proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2c.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxtable.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/obc1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sa1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sa1regs.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sfxproc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/st10proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/7110proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/st11proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dma.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dsp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dspproc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/execute.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/irq.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/memory.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/spc700.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/stable.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/table.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/tablec.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `debugasm.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `gui/gui.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `gui/menu.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makev16b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makev16t.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makevid.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716d.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716e.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716t.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode7.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode7ext.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mv16tms.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/m716text.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newg162.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/procvid.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/sw_draw.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/2xsaiw.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq2x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq2x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq3x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq3x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq4x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq4x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/copyvwin.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `linux/sdlintrf.o' is incompatible with i386:x86-64 output
rm -f version.o
/usr/bin/install -c -d -m 0755 //usr/local/bin
/usr/bin/install -c -m 0755 zsnes //usr/local/bin
/usr/bin/install: cannot create regular file `//usr/local/bin/zsnes': Permission denied
make: *** [install] Error 1
```

wth?

---

### Post by BoyOfDestiny on 2007-08-28
> **DavidGX said:**
> After getting sdl -dev files installed, switching to "make" instead of "gmake" it starting going, was looking great and then spat out this..

```
/usr/bin/ld: warning: i386 architecture of input file `endmem.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `init.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `vcache.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `ztime.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/c4proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp2proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp3proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/dsp4proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxemu2c.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/fxtable.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/obc1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sa1proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sa1regs.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/sfxproc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/st10proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/7110proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `chips/st11proc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dma.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dsp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/dspproc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/execute.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/irq.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/memory.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/spc700.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/stable.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/table.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cpu/tablec.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `debugasm.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `gui/gui.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `gui/menu.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makev16b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makev16t.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/makevid.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716b.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716d.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716e.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode716t.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode7.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mode7ext.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/mv16tms.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/m716text.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newg162.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/newgfx2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/procvid.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/sw_draw.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/2xsaiw.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq2x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq2x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq3x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq3x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq4x16.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/hq4x32.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `video/copyvwin.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `linux/sdlintrf.o' is incompatible with i386:x86-64 output
rm -f version.o
/usr/bin/install -c -d -m 0755 //usr/local/bin
/usr/bin/install -c -m 0755 zsnes //usr/local/bin
/usr/bin/install: cannot create regular file `//usr/local/bin/zsnes': Permission denied
make: *** [install] Error 1
```

wth?

see my post. Try to grab the 32-bit files you need. Some of ZSNES stuff is in assembly (and as such architecture specific.)

This may help as well
[http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)

---

### Post by DavidGX on 2007-08-28
I've had ia32-libs installed. No dice.

---

### Post by BoyOfDestiny on 2007-08-28
> **DavidGX said:**
> I've had ia32-libs installed. No dice.

If I had a 64-bit ubuntu box I could give more concrete help. 

You have a few options. Run a chroot and 32-bit zsnes (a bit of a hassle, and hopefully not needed) or to try and install the 32-bit binary, and see if it runs with those compatibility libraries.

I would recommend try the latter.

[http://www.getdeb.net/search.php?keywords=zsnes](http://www.getdeb.net/search.php?keywords=zsnes)

To force the install

sudo dpkg -i --force-all *whatever*.deb

sudo dpkg -r zsnes

Will remove it.

Keep at it.

---

### Post by DavidGX on 2007-08-28
> **BoyOfDestiny said:**
> If I had a 64-bit ubuntu box I could give more concrete help. 

You have a few options. Run a chroot and 32-bit zsnes (a bit of a hassle, and hopefully not needed) or to try and install the 32-bit binary, and see if it runs with those compatibility libraries.

I would recommend try the latter.

[http://www.getdeb.net/search.php?keywords=zsnes](http://www.getdeb.net/search.php?keywords=zsnes)

To force the install

sudo dpkg -i --force-all *whatever*.deb

sudo dpkg -r zsnes

Will remove it.

Keep at it.

That did it. I had downloaded that same .deb the other day but was unsuccessful in installing it because I wasn't aware of how to force it. Thanks a lot to everyone who replied to this thread. I really appreciate it.

---

### Post by aquishix on 2009-09-30
> **BoyOfDestiny said:**
> If I had a 64-bit ubuntu box I could give more concrete help. 

You have a few options. Run a chroot and 32-bit zsnes (a bit of a hassle, and hopefully not needed) or to try and install the 32-bit binary, and see if it runs with those compatibility libraries.

I would recommend try the latter.

[http://www.getdeb.net/search.php?keywords=zsnes](http://www.getdeb.net/search.php?keywords=zsnes)

To force the install

sudo dpkg -i --force-all *whatever*.deb

sudo dpkg -r zsnes

Will remove it.

Keep at it.

Old thread, I know.  But.

Can you explain the chroot thing a bit more?  I did a forced install of the 32-bit binary package and got a seg fault upon running the install binary.  I also got compiler errors trying to compile the zsnes source code on this 64-bit Ubuntu box...it complains about it being the wrong architecture.  Please tell me I'm not screwed =(.

J

---

### Post by Grishka on 2009-10-01
> **aquishix said:**
> I did a forced install of the 32-bit binary package and got a seg fault upon running the install binary.

try ```
zsnes -ad sdl
```

---


---
title: "Installation of 32 bit supermongo on 64 bit system"
date: 2009-05-23
forum: General Help
---

### Post by Lyuokdea on 2009-05-23
I'm trying to install supermongo, and getting the following error while running 'make':

cc -Wall -Dlinux -DNEED_SWAP -o sm main.o sm_main.o control.o do_for.o editor.o fft.o getlist.o help.o history.o input.o lexan.o keymac.o macros.o macroed.o math.o more.o mscanf.o name.o pow.o printv.o random.o readcol.o read_old.o restore.o spline.o tokens.o userfn.o variable.o vec_arith.o vec_logical.o vec_misc.o vec_strings.o yylex.o  libplotsub.a libutils.a libdevices.a  -lm
/usr/bin/ld: i386 architecture of input file `math.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `pow.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `random.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `libplotsub.a(dither.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `libplotsub.a(vec_image.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `libutils.a(numword.o)' is incompatible with i386:x86-64 output

Does anybody know how to resolve this?

Thanks,

~Lyuokdea

---

### Post by Aped on 2009-05-23
You can probably guess that it's because you're trying to install software designed for a 32bit architecture on a 64bit one; if there were an easy fix to this (emulating 32bit machines? maybe you could do this with VMWare) then a lot of things would be simplified in this world ;)

You can use a chroot, or even install a dual boot for that matter, but again you're just going way out of your way for a single program. 

Best bet is sudo apt-get ia32-libs I think; don't know much about it, doesn't support non-commandline or very basic programs. If the libraries you need aren't supported, you just extract them (I think) into /emul/somethingoranother folder. 

I know it's not much help... but at least it's a place to start, and a bump if nothing else.

edit: cha-ching, google paydirt
[http://www.debian-administration.org/articles/531](http://www.debian-administration.org/articles/531)

Enjoy.

---

### Post by Lyuokdea on 2009-05-23
Hmmm....the libraries were already installed, it looks like the trick is to get supermongo's make file look for those files instead of the 64 bit files they are picking up.

Thanks for the info!

~Lyuokdea

---

### Post by Yellow Pasque on 2009-05-23
I think installing gcc-multilib and adding the -m32 flag to the compile statements might help.

---

### Post by Lyuokdea on 2009-05-23
Hmm, that didn't seem to change anything. I got more errors of the same type than i did before (which is probably a good thing, because it at least means something changed.)

The command the makefile is using to compile is:

cc -Wall -Dlinux -DNEED_SWAP

I've changed to gcc and back, but that didn't change anything. Is there any way to force it to look for the 32 bit libraries?

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2009-05-25
I can't think of any more ways to get this to compile...is there some way to force it to read the 32 bit library instead of the 64 bit library?

~Lyuokdea

---

### Post by Lyuokdea on 2009-05-25
Still need some help with this....how do you get a program to read from a 32 bit library?

Thanks,

~Lyuokdea

---

### Post by Yellow Pasque on 2009-05-25
It looks like you have 32-bit object code and you're trying to create a 64-bit executable.

It's really hard to help without seeing the Makefile, and since this isn't a GPL program, you would be better off contacting the site/authors of the prgoram.

---

### Post by orbica on 2009-11-16
> **Lyuokdea said:**
> Hmm, that didn't seem to change anything. I got more errors of the same type than i did before (which is probably a good thing, because it at least means something changed.)

The command the makefile is using to compile is:

cc -Wall -Dlinux -DNEED_SWAP

I've changed to gcc and back, but that didn't change anything. Is there any way to force it to look for the 32 bit libraries?

Thanks,

~Lyuokdea
I don't know if you still need this, but the correct command to compile SM in 64bit is:
cc -Wall -Dlinux -DNEED_SWAP -L/usr/lib64 -lX11

N.B. This is for 2.6* kernels. On older kernels you should use the correct path to X11 libraries, e.g.:

cc -Wall -Dlinux -DNEED_SWAP -L/usr/X11R6/lib64 -lX11

---


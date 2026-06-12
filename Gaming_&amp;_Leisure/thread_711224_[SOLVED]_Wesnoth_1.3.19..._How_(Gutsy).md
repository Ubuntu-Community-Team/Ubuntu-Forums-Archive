---
title: "[SOLVED] Wesnoth 1.3.19... How? (Gutsy)"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by chazdraves on 2008-02-29
Hey, all. I'm looking to install the latest beta build of Wesnoth without compiling (don't even know how to). How do I get Ubuntu (Gutsy) to find 1.3.19 instead of 1.28? I tried the repository listed at Wesnoth.org, but that link doesn't work...

Any help appreciated!
- Chaz

---

### Post by Perfect Storm on 2008-02-29
[http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth)

Post back if you encounter any problems.

---

### Post by chazdraves on 2008-02-29
You, Sir, are a genius. But it didn't finish entirely. This is what I get when I ./configure

chaz@chaz-desktop:~/Desktop/wesnoth-1.3.19$ ./configure --enable-editor
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for XOpenDisplay in -lX11... no
checking for pngmeta... no
checking for sdl-config... no
checking for sdl11-config... no
configure: error: *** SDL not found! Get SDL from [www.libsdl.org](www.libsdl.org).
If you already installed it, check it's in the path. If problem remains,
please send a mail to the address that appears in ./configure --version
indicating your platform, the version of configure script and the problem.

??
- Chaz

---

### Post by Perfect Storm on 2008-02-29
Did any error happens when you did the "before installing" part? If so check if your software sources is enabled.

---

### Post by wingnux on 2008-02-29
You just have to install the libsdl dev packages from synaptic.

---

### Post by chazdraves on 2008-02-29
Well, it required quite a bit of Synaptic-searching and some Googling, but I got it to configure. Now it doesn't seem to be working. I didn't see any errors while I was doing the  "make" command (is that compiling?), but it didn't pass the checkinstall. When it asked if I wanted to see the log, I said yes, and it told me that the log was locked and already in use...?

- Chaz

---

### Post by chazdraves on 2008-02-29
I tried it a second time starting from ./configure and it definitely did some more things this time that it must have missed the first time, but it still says it's not able to install the Debian package... If I can't get this figured out with your guys' help, how do I remove all the crap this must have dumped on my HDD?

Thanks,
- Chaz

---

### Post by emergingstar123 on 2008-02-29
World of Warcraft Gold 


by  emergingstar123

---

### Post by chazdraves on 2008-02-29
^--- What?

Okay, you'll all have to excuse me if for the next while I consider myself truely amazing! Somehow it all worked out. The trick seemed to be using sudo checkinstall instead of just checkinstall. I decided to try that after I saw some of the lines seemed to be running chown commands... Anyhow, it works like a gem. A great many thanks!

- Chaz

---

### Post by chazdraves on 2008-02-29
Ah... but one more question... Now Synaptic says that all of my Wesnoth packages are broken... If I choose to remove those, will it remove 1.3.19? I guess I should have done that first?

- Chaz

---

### Post by Perfect Storm on 2008-03-01
> **chazdraves said:**
> Well, it required quite a bit of Synaptic-searching and some Googling, but I got it to configure. Now it doesn't seem to be working. I didn't see any errors while I was doing the  "make" command (is that compiling?), but it didn't pass the checkinstall. When it asked if I wanted to see the log, I said yes, and it told me that the log was locked and already in use...?

- Chaz

If checkinstall fails it means
1) you have synaptic or add/remove open as checkinstall makes a fake  debian/ubuntu package and need access to these applications.
2) The package you're trying to make tries to overwrite existing files that are being used by others (rare).
3) It doesn't support checkinstall or checkinstall doesn't support it (orther forms of compiling like scons and jam etc.)
Then use **sudo make install** if sudo checkinstall completly fails.

About make
If you added new libs it needs to **make clean** before running **./configure** so it makes a new "setup" on how to build the stuff.


Yes, good idea to remove the all version of wesnoth.

---

### Post by chazdraves on 2008-03-01
I'm trying to make sure I understand this...

If I have to add new libraires for ./configure to run sucessfully, then I should run make clean before running ./configure? And then your run make as per usual?

So you're saying I should have  run sudo make install and then checkinstall instead of running sudo checkinstall?

I guess the end result is that it works and works beautifully, but I want to make sure I have some understanding of this for the next time as this is all still Greek to me. :)

Thanks for your patience. I'm going to run Synaptic and remove the 1.2.8 files... hopefully that doesn't uninstall 1.3.19... 

- Chaz

---

### Post by Perfect Storm on 2008-03-01
> If I have to add new libraires for ./configure to run sucessfully, then I should run make clean before running ./configure? And then your run make as per usual?

No, if you ran **make** and for some reason want to add or disable a lib for the stuff you compiling you have to  **make clean** before running **./configure** again. ./configure is that file that controls what to add and what not add, also it checks if the minimum required libs are installed to compile it.

> So you're saying I should have run sudo make install and then checkinstall instead of running sudo checkinstall?

Well, no. Run sudo make install _IF_ it can't use sudo checkinstall.

---

### Post by chazdraves on 2008-03-01
Allright. I think I've got it.

One last question... is it safe to delete the wesnoth 1.3.19 folder on my desktop?

Thanks again!
- Chaz

---

### Post by Perfect Storm on 2008-03-01
> **chazdraves said:**
> Allright. I think I've got it.

One last question... is it safe to delete the wesnoth 1.3.19 folder on my desktop?

Thanks again!
- Chaz

Yep. It's not needed anymore. (unless you want re-compile it again for some reasons.)

---

### Post by chazdraves on 2008-03-01
Nah, I think my computer's had enough of that :)

Thanks for all your help (and for the time you obviously take to maintain that website, it's a real Godsend).

- Chaz

---

### Post by eragon100 on 2008-03-08
Hi!

I'm having trouble compiling. ./configure won't run,. i, followed the guide. It keeps saying that i don't have libsdl-image installed, but according to synaptic i have both the normal and the -dev package. I even compiled the library form source from libsdl.org to make sure i hd it, but ./configure still says i don't :confused:

Help!

---

### Post by chazdraves on 2008-03-08
If you haven't already, I would recommend starting a new thread.

Dumb question, but have you uninstalled and re-installed libsdl-image-dev?

- Chaz

---


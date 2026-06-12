---
title: "gimp plugin compile cant find gimp"
date: 2013-01-14
forum: Desktop Environments
---

### Post by Kilarin on 2013-01-14
I'm running Xubuntu under Ubuntu 12.04, and I have gimp 2.6.12 installed.  (typing gimp at the command line brings up gimp 2.6.12)

I'm attempting to follow the instructions here:
[http://gimp-image-reg.sourceforge.net/install-en.html](http://gimp-image-reg.sourceforge.net/install-en.html)
to compile a gimp plugin that does image registration (alignment)

I created a folder, and placed gimp-image-reg-0.5.5.tar.gz in it.  The tar command went fine, I made the build folder and cd'd into it.  Then, as instructed, I enter the command:
../gimp-image-reg-0.5.5/configure --enable-user-install

Which runs, but gets the following:

```
$ ../gimp-image-reg-0.5.5/configure --enable-user-install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GIMP... no
configure: error: Package requirements (gimp-2.0   >= 2.2.0
        gimpui-2.0 >= 2.2.0) were not met:

No package 'gimp-2.0' found
No package 'gimpui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIMP_CFLAGS
and GIMP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I don't understand.  If I have gimp 2.6 installed, why is it failing to pass the requirements?  And I'm afraid the pkg-config man page is definitely talking over my head. 

Can anyone help?

thanks very much!

---

### Post by mcduck on 2013-01-15
for compiling, you usually need the *development packages* rather than the actual executable program.

So if you the compile error asks for "gimp-2.0", the package you actually need would be something like "gimp-2.0-dev".

(I didn't check the repositories for the exact package name, but the development versions are always the ones with the "dev" part in the package name)

---

### Post by Kilarin on 2013-01-15
you are absolutely correct.  The package I needed was libgimp2.0-dev, and it was documented right there on the instructions page.  I just didn't understand what I was reading.  I also had to install intltool.  But now it works.

Thanks!

---


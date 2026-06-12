---
title: "wxMacMolPlt and openGL"
date: 2008-03-01
forum: Desktop Environments
---

### Post by metalgtr on 2008-03-01
Hello all,

I am trying to install wxMacMolPlt-7.1, a 3D molecular viewer, on Gutsy 7.10 on my Sony Vaio VGN-A290. I have already used synaptic to get the wxGTK-2.8 and its dependencies.

Following wxMacMolPlot's install directions, I enter into the console:

mfucc@vaio:/etc/wxmacmolplt-7.1$ ./configure --with-gtk --with-opengl --enable-unicode
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for Ming_init in -lming... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking wxWidgets version... 2.8.7
checking for wxWidgets libraries... yes
checking for OpenGL support in wxWidgets... not found
configure: error: wxMacMolPlt requires wxWidgets to be compiled with OpenGL support.
mfucc@vaio:/etc/wxmacmolplt-7.1$ 

Following the suggestions of the install doc, I have tried "sudo ldconfig" and I have also edited /etc/ld.so.conf to contain the following:

include /etc/ld.so.conf.d/*.conf

/usr/lib/atlas
/usr/lib/wx
/usr/include/wx-2.8/wx

And then I have retried "sudo ldconfig" to no avail.

I appreciate anyone's thoughts on this.

---

### Post by metalgtr on 2008-03-01
I ended up solving this one. Here's how I did it.

The problem was with my wxWidgets, specifically I did not have wxGTK properly installed. All that was necessary was to use Synaptic to get the appropriate gtk+-2.0 libraries: I got a number of them, but I think "libgtk2.0-0" and "libgtkgl2.0-1" were the ones that did it. Once Synaptic installed these, I just retried the "./configure --with-gtk --with-opengl --enable-unicode" step, and then proceeded to "make" and "sudo make install."

Hope this helps others out there.

Furthermore, if you're trying to use wxMacMolPlt with the GAMESS computational chemistry software package, I'll also recommend "ghemical," a separate but similar tool.

---


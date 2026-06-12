---
title: "X-Plane 9 Linux Updater not finding libesd.so.0 in lib32"
date: 2010-05-23
forum: Gaming &amp; Leisure
---

### Post by Geistjaeger on 2010-05-23
I've looked quite a few places for the answer to this with no luck...one spot looked promising, but it essentially suggested copying libesd.so.0 and accompanying file to the usr/lib32 directory...but that also did not work.  

Here's what I get when I run the updater:
'/home/michael/Desktop/X-Plane Updater Linux' 

/home/michael/Desktop/X-Plane Updater Linux: error while loading shared libraries: libesd.so.0: wrong ELF class: ELFCLASS64

So, I ran an LDD query on the updater:
ldd '/home/michael/Desktop/X-Plane Updater Linux' 
	linux-gate.so.1 =>  (0xf7726000)
	libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf764d000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf75dc000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf75cb000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf74ae000)
	libopenal.so.0 => /usr/lib32/libopenal.so.0 (0xf740e000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf73f5000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf73f1000)
	libm.so.6 => /lib32/libm.so.6 (0xf73cb000)
	libc.so.6 => /lib32/libc.so.6 (0xf7270000)
	libatiuki.so.1 => /usr/lib32/fglrx/libatiuki.so.1 (0xf7268000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7249000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7153000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7139000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7070000)
	libartsc.so.0 => /usr/lib32/libartsc.so.0 (0xf706a000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7065000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf705f000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6f95000)
	[COLOR="Red"]libesd.so.0 => not found[/COLOR]
	libaudiofile.so.0 => /usr/lib32/libaudiofile.so.0 (0xf6f6f000)
	libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf6ee1000)
	libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0xf6eb8000)
	libvorbisfile.so.3 => /usr/lib32/libvorbisfile.so.3 (0xf6eaf000)
	libsmpeg-0.4.so.0 => /usr/lib32/libsmpeg-0.4.so.0 (0xf6e55000)
	/lib/ld-linux.so.2 (0xf7727000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6e51000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6e4b000)
	librt.so.1 => /lib32/librt.so.1 (0xf6e42000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6e11000)
	libdirectfb-1.2.so.0 => /usr/lib32/libdirectfb-1.2.so.0 (0xf6d99000)
	libfusion-1.2.so.0 => /usr/lib32/libfusion-1.2.so.0 (0xf6d8f000)
	libdirect-1.2.so.0 => /usr/lib32/libdirect-1.2.so.0 (0xf6d79000)
	libogg.so.0 => /usr/lib32/libogg.so.0 (0xf6d72000)

I've tried a couple of things, but to no avail.  I'm still pretty much a LINUX neophyte, so please make any solutions as step-by-step as possible.

Thank you!

---

### Post by dummy910 on 2010-05-23
type the following into a terminal to install **libesd.so.0** ```
sudo apt-get install libesd* 
``` then you should get a response similar to this one: > The following extra packages will be installed:   libaudiofile-dev libescape-ruby libesd-java libesd0-dev libesmtp-dev   libesmtp5 libespeak-dev libestools1.2 libestools1.2-dev libestraier-dev   libestraier-java libestraier-ruby1.8 libestraier8 libjorbis-java libqdbm14   libruby1.8 ruby ruby1.8   Suggested packages:    speech-tools-doc hyperestraier ruby1.8-examples rdoc1.8 ri1.8 The following NEW packages will be installed:    libaudiofile-dev libescape-ruby libesd-java libesd0-dev libesmtp-dev   libesmtp5 libespeak-dev libestools1.2 libestools1.2-dev libestraier-dev   libestraier-java libestraier-ruby1.8 libestraier8 libjorbis-java libqdbm14   libruby1.8 ruby ruby1.8   0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.  Need to get 6,176kB of archives.  After this operation, 25.0MB of additional disk space will be used. Do you want to continue [Y/n]? of course, if you want to install, just type **y** as your response, if not, type n to cancel the request.

---

### Post by Perfect Storm on 2010-05-23
libesd.so.0 is part of the esound libraries (or more specific Enlightened Sound Daemon). As X-plane runs as a 32-bit applications it should be enough to install libesd on a 32-bit system. 

As for 64-bit this may need a bit trickier but should be easy enough. Just note you can't mix 32 and 64 libs they go in different path. 64 bit libs : /usr/lib and 32 bit /usr/lib32 on Ubuntu.

That's why it says: **error while loading shared libraries: libesd.so.0: wrong ELF class: ELFCLASS64**
Remove the 64-bit version of libesd from /usr/lib32

First get and install getlibs;
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg i getlibs-all.deb

```

Now using getlibs to install the 32-bit .so of esd automatically;
```
sudo getlibs "/home/michael/Desktop/X-Plane Updater Linux"
```
This might fail if the "X-Plane Updater Linux is not a dynamic binary" or the missing library does not exist in the ubuntu repositories or the library have a difference in its name (like ending on .so.1 instead of .so.0)


More info about getlibs
```
getlibs -h
```

---

### Post by Geistjaeger on 2010-05-23
Artificial Intelligence, thank you for the ideas.  Did not work exactly as you said--I think the X-Plane updater is not a binary as you said might be a problem; however, you got me thinking about getlibs and I visited the info that Cappy has posted about the script... which led me to use:

```
sudo getlibs -64 libesd.so.0
```

and 

```
sudo getlibs -32 libesd.so.0
```

I used the second because for whatever reason the -64 did not populate the /usr/lib32 directory with the right library...but -32 did.

Now, the problem is different...

First, I tried (and failed):
```
michael@michael-hplaptop:~$ '/home/michael/Desktop/X-Plane Updater Linux' 
X-Plane Updater Linux: ../../src/xcb_io.c:452: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted
```

Thinking the problem was not using superuser permissions, I tried (and failed):
```
michael@michael-hplaptop:~$ sudo '/home/michael/Desktop/X-Plane Updater Linux' 
Floating point exception
```

Any thoughts?

---

### Post by Geistjaeger on 2010-05-30
Well,that escapade is over.  Turns out that updating to the latest ATI video driver fixed a majority of the incompatibility problems.  Of course, I caused myself a week of trouble and pain in getting that done, but all is finally well.

My wife asked me today though..."why do you want to have Linux set up on your computer...it only causes you problems."  What can I say, I like a challenge.

Thanks for everyone's help.

---


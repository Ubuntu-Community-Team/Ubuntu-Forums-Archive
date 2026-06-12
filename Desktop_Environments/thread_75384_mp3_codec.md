---
title: "mp3 codec"
date: 2005-10-13
forum: Desktop Environments
---

### Post by elementary on 2005-10-13
apologies if this has been covered...couldn't find relevant info on it...

I'm wanting to get mp3s going on rythmbox (or something else). I have edited the source folder, but the backports.mirrormax server doesnt seem to work. I get some updates (using apt-get update command) but not the mp3 codecs.

Is it just a matter of time before the server starts working or should I try something else? Other programs?

Cheers

---

### Post by Karasu Tengu on 2005-10-13
you could use a simpler way,

apt-get install totem-xine OR
apt-get install gstreamer*

these have mp3 codec...

---

### Post by taurus on 2005-10-13
I assume you are talking about a program to play your mp3s!!!  Xmms works just fine for me and I had it playing my mp3s collection but needed to stop it because I had to go to work!  Should have called in sick early this afternoon!!! ;)

---

### Post by luckyaba on 2005-10-13
I had a similar problem with amarok that required me to get gstreamer0.8-plugins.  Might wanna make sure you have that package..

---

### Post by invalid on 2005-10-13
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by doclivingston on 2005-10-13
To install most of the codecs that aren't installed by default (for Rhythmbox, totem and other gstreamer-based apps), install the "gstreamer0.8-plugins" package with synaptic or apt-get. If you just want mp3 playback, the package is called "gstreamer0.8-mad", but it gets pulled in as a dependency of the main plugins package.

---

### Post by RAOF on 2005-10-13
And if you want nearly every codec under the sun, and have the multiverse repository enabled, install gstreamer0.8-plugins-multiverse as well.

---

### Post by LinkRJH on 2005-10-13
My apt get wont let me do it...why is this?

linkrjh@gigahertzog:~$ sudo apt-get install gstreamer*
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer-0.9.3.tar.gz
linkrjh@gigahertzog:~$

---

### Post by AvixK7 on 2005-10-13
where do you go to change the repositories? it slipped my mind :rolleyes:

---

### Post by nix4me on 2005-10-13
gstreamer sux.  we need a w32 codec pack for totem-xine.

gstreamer has always sucked and it still does.

No clue why they keep using it.  We need a foolproof way to get mp3 in rythmbox and video in totem-xine with all the codecs!

nix

---

### Post by RAOF on 2005-10-14
[QUOTE=LinkRJH]My apt get wont let me do it...why is this?

linkrjh@gigahertzog:~$ sudo apt-get install gstreamer*
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer-0.9.3.tar.gz
linkrjh@gigahertzog:~$[/QUOTE]
That's a cool error.  The problem here is that there is a file which matches gstreamer* (ie: gstreamer-0.9.3.tar.gz) in the directory you're running that command in.  Bash, being the helpful shell that it is, expands that wildcard into the matching filename **before** apt-get can see it.  So, from the perspective of apt-get, you've run "apt-get install gstreamer-0.9.3.tar.gz".  Cool, eh :rolleyes: 

> gstreamer sux. we need a w32 codec pack for totem-xine.

gstreamer has always sucked and it still does.

No clue why they keep using it. We need a foolproof way to get mp3 in rythmbox and video in totem-xine with all the codecs!

nix
Gstreamer works very well for me, and works very well for ubuntu development.  The plugin-nature of it means that the ubuntu devs can include all of the free codecs in main, and easily put all the non-free stuff in universe & multiverse.  And the universal way to get (practically) all codecs to work is with gstreamer-plugins-multiverse :)

---

### Post by doclivingston on 2005-10-14
As ROAF pointed out, the problem is bash doing expansion. Using ```
apt-get install 'gstreamer*'
``` shoudl work, becuse using single quotes stops it doing any expansion.

---

### Post by doclivingston on 2005-10-14
[QUOTE=nix4me]gstreamer sux.  we need a w32 codec pack for totem-xine.

gstreamer has always sucked and it still does.

No clue why they keep using it.  We need a foolproof way to get mp3 in rythmbox and video in totem-xine with all the codecs![/QUOTE]

I haven't had any real problems with using gstreamer for audio playback since the 0.6 days.

Sure it does have some problems with video playback, mostly A/V sync issues with some of the non-free codecs (particularly WMV and quicktime). Most of those issues will be fixed in gstreamer 0.10 (which will be in Dapper), because they have made the necessary design changes.


There are several problems with replacing gstreamer with xine:
* It's more difficult for the developers to seperate the free and non-free codecs, which has to be done because Ubuntu wouldn't ship with mp3/mpeg/wmv/etc support even if it switched to Xine
*Although you have problems with gstreamer and xine works for you, that isn't always the case. For example gstreamer work okay for me, and I've had bad problems with xine - it refuses to play dvds and wmvs work even worse than with gstreamer


Also Rhythmbox uses gstreamer exclusively now, Xine was deprecated in the 0.8 series and has been completely removed from 0.9. Getting Xine support back would require someone stepping up and
1) updating it to work again,
2) offer to maintain it, and
3) port all the new features (DAAP music sharing, audio cd playback, etc) over to be able to use it, which would be considerable work.

---

### Post by LinkRJH on 2005-10-14
So I got gstreamer* and it still doesn't play mp3's...what gives?

---

### Post by doclivingston on 2005-10-15
[QUOTE=LinkRJH]So I got gstreamer* and it still doesn't play mp3's...what gives?[/QUOTE]

1) check that the "gstreamer0.8-mad" package is installed.

2) try running "gst-inspect-0.8 mad" from a terminal.

3a) If you get lots of output, it's installed and should work. If it's not working, then something odd is happening.

3b) If it says "No such element or plugin 'mad'" then try running "sudo gst-register-0.8", "gst-register-0.8"  and then "gst-inspect-0.8 mad" again.

4) If you get to this point, and you're sure that the package is installed, then something is seriously broken.

---

### Post by krcm on 2005-10-20
apt-get install gstreamer*

when i do this i get the message that the package can't be found, i do have the pckage though but what map does it have to be in for it to be found.

grtz

---

### Post by doclivingston on 2005-10-20
If you want to install all the gstreamer packages, you need to use "apt-get install 'gstreamer*'", otherwise bash expands the "*" and it won't work.

---

### Post by missmoondog on 2005-12-29
well, here we go again. sure seems that the more often you install ubuntu, the more difficult it is to get audio/video working. just installed it on another machine (#6), have all the gstreamer things, win32codecs, ffmpeg, all 800 lib things and still can't get audio or video to play in this thing. been searching all over for the last day and a half to get this sytem working correctly and nothing. what's weird is if i hover the mouse over an mp3 file, it plays. as soon as i double click to open totem or rhythymbox,  it quits. what kind of sense is that?

we REALLY need a centralized place/way to enable these things. half the reason right there, linux is not mainstream.

---

### Post by vrkanaka on 2006-04-20
i got gstreamer-0.10.4.tar.gz
i need to install it but unable,
iam getting error as
kvr@kvr:~/gstreamer-0.10.4$ ./configure
configure: configuring gstreamer for release
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for VALGRIND... no
configure: Using GStreamer source release as package name
configure: Using Unknown package origin as package origin
configure: Using /usr/local/var/cache/gstreamer-0.10 as registry cache dir
configure: WARNING: Sissy ! By asking to not build the tests known to fail, you hereby waive your right to customer support.  If you do not agree with this EULA, please press Ctrl-C before the next line is printed.  By allowing the next line to be printed, you expressly acknowledge your acceptance of this EULA.
checking whether byte ordering is bigendian... no
checking if unaligned memory access works correctly... (whitelisted) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gawk... (cached) mawk
checking for bison... no
configure: error: Could not find bison
 

can any one  help me

---

### Post by Mr Egg on 2006-04-20
Install Automatix, then in Automatix install the "AUD-DVD" option, this will install some necessary codecs. Then open Synaptic Package Manager and search for "gstreamer" and install "gstreamer-mad".

Worked for me.:)

---

### Post by oberoc on 2006-04-20
Have you check out this page: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) ?

-Tino

---


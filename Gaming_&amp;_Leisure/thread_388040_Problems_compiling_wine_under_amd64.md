---
title: "Problems compiling wine under amd64"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by KamiCrazy on 2007-03-19
I am having problems compiling wine.

To preface everything, I am running a totally fresh installation, barely an hour old. I have been trying to compile wine because I want guild wars to work.

The problem I am facing is that I seem to be missing a bunch of files in /usr/lib32 before I can compile wine.

Most wine compiling guides have steps which involve making symbolic links to these files. Obviously because they aren't there I have broken links.

For instance, I have installed freetype6-dev. Under /usrlib /usr/lib64 libfreetype exists. However in /usr/lib32 it doens't. Should installing freetype6 also give me the 32 bit libraries or is this not the case? If not how do I got about finding the 32 bit library.

Another example is libGLU. I have libGL but no libGLU in lib32. (I'm sure both files are supposed to be from the nvidia 32 bit compatibility installation) However this file does exist in /usr/lib64.

I'm pretty sure I can't just symbolic link to the /usr/lib64 files though, since using the file command in the /usr/lib64 ones says that its specifically 64 bit while doing the same for the /usr/lib32 files says its 32 bit.

Can anyone tell me what packages I need to install to get the missing files for wine?

I need

libX11
libXext
libGLU
libz
libfreetype

Thanks

---

### Post by KamiCrazy on 2007-03-19
Fixed -_-! sudo apt-get install -u ia32-libs!

---

### Post by KamiCrazy on 2007-03-19
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls'
make: *** [dlls] Error 2

Getting this error now, been googling for an answer, haven't come up with anything.

---

### Post by Jason_25 on 2007-03-19
Are you using this guide?
[http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a](http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a)

.9.33 is out as a deb since yesterday anyway.  But I understand wanting to compile it.  I successfully built it yesterday but I couldn't get alsa support.  I wish the config.log was a little easier to understand.  As it is now, it's basically useless.  You just have to guess what libraries you need.  Make sure you have all the ia32-libs and build-essential installed, of course.

BTW, if you figure out how to include ALSA support let us know.

---


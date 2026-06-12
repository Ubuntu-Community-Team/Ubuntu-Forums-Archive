---
title: "Update transcode"
date: 2005-11-07
forum: Desktop Environments
---

### Post by cazz on 2005-11-07
I have right now 1.0.1 install but  I try to install 1.0.2 with source tarballs.

But I have a problem with lame and ffmpeg??
They are already install but what I have found I need to install lame-dev to work but that is not in the list of synaptic?.

Where can I download lame-dev for Breezy?

The problem the transcode say is 

```
ERROR: requirement failed: cannot compile ffmpeg/avcodec.h
ffmpeg/avcodec.h can be found in the following packages:
  FFMpeg  http://www.ffmpeg.org/

ERROR: option '--enable-lame' failed: cannot compile lame.h
lame.h can be found in the following packages:
  lame  http://www.mp3dev.org/

ERROR: option '--enable-lame' failed: cannot compile and run a test program
lame.h can be found in the following packages:
  lame  http://www.mp3dev.org/
```

I dont now yet what the ffmpeg problem is but I hope to first fix the lame problem and then ffmpeg?

Any idea?

---

### Post by tomski on 2005-11-07
i think this problem maybe because when you install ffmpeg through synaptic it does not create 'shared libaries' so if you uninstall ffmpeg and get the soucre code and compile with the swithces mentioned you should be ok 




Steps: 1. Remove ffmpeg and libavcodec through Synaptec

2. Download the source for the latest ffmpeg and transcode from their respective sites

ffmpeg:
[http://ffmpeg.sourceforge.net/index.php](http://ffmpeg.sourceforge.net/index.php)

transcode:
[http://www.transcoding.org/cgi-bin/transcode](http://www.transcoding.org/cgi-bin/transcode)

3. Unpack the source someplace convenient

tar -zxvf ffmpeg-insert-version-here.tar.gz
tar -zxvf transcode-insert-version.tar.gz

4. Configure and compile ffmpeg

./configure --enable-mp3lame --enable-vorbis --enable-a52 --enable-gpl --enable-shared
make
sudo make install

5. Configure and compile transcode

./configure --enable-v4l --enable-lame --enable-ogg --enable-vorbis --enable-theora --enable-libquicktime --enable-a52 --enable-gtk --enable-mjpegtools
make
sudo make install

6. If there are any dependency problems with this method, the best way to handle it that I know of is to go into Synaptec an
install 'dependency-dev' package from there.  Or, you can crawl all over the internet finding the source packages and installing them.  (your choice ;) )

7. Enjoy transcode:)

HOW-TO courtesy of GLUG101

---

### Post by cazz on 2005-11-07
Thanks
I did change a little ffmpeg config
./configure --enable-mp3lame --enable-vorbis --enable-a52 --enable-gpl --enable-shared --enable-libogg

because he say "libogg must be enabled to enable Vorbis."
the configure dont say anything bad but when I try to "make" it say that he cant find -lvorbis

---

### Post by cazz on 2005-11-07
Hmm I try too find information about the problem but that is not so easy

---

### Post by cazz on 2005-11-10
Anyone have any idea how to fix that?

---

### Post by Harleen on 2005-11-10
It seems, the configure script hasn't checked well enough all dependencies.
The command "-lvorbis" tells the linker to bind against the file libvorbis.so, which is contained in the package libvorbis-dev. Installing that package might already solve your problem.

---

### Post by cazz on 2005-11-10
Thanks that did the trick :)

But now it say that is wrong in mp3lameaudio.o like "implicit declaration of function &#226;lame_set_bWriteVbr" and other function.

I maybe have forgot some xxx-dev maybe??

---

### Post by Harleen on 2005-11-10
Isn't there another error message before? A missing header file maybe?
And yes, it sounds like another missing dev-package.

---

### Post by cazz on 2005-11-10
I find the problem, I did not install liblame-dev pack

But it say many "warning..........."

And when I do "sudo make install" and then run ffmpeg it say 

ffmpeg: error while loading shared libraries: libavformat.so: cannot open shared object file: No such file or directory

is not correct install

---

### Post by Harleen on 2005-11-10
If you just installed that library (libavformat.so), it is not yet contained in the linker cache and so not known by the system. Running "sudo ldconfig" should solve this.
If it's not on your system (probably under /usr/local/lib) I'm out of ideas.

---

### Post by cazz on 2005-11-10
Thank you

That was a library that I dont have install yet so I do that now.

---

### Post by cazz on 2005-11-10
I get many "varning: pointer targets in assignment differ in signedness" and some other similar, is that normal?

I going soon to try to "sudo make install"

EDIT
Strange he say "ffmpeg: error while loading shared libraries: libavformat.so: cannot open shared object file: No such file or directory" but I have install libavformat-dev??


EDIT AGAIN
Sorry I forgot "sudo ldconfig"
But he say "
motion_est.c:178: varning: &#226;uvdxy&#226; may be used uninitialized in this function" many time?

No same as before "ffmpeg: error while loading shared libraries: libavformat.so: cannot open shared object file: No such file or directory"
Very very strange

---

### Post by Harleen on 2005-11-10
Forget about the warnings. They shouldn't cause any problems. 

Calling ldconfig is only important after installing self compiled libraries. Those installed via synaptic should already do it when automatically configuring the package. But one more call surely won't hurt...

The package libavformat-dev seems to contain only a static library. But the dynamic library has to be already on your hard disk. Otherwise you wouldn't have been able to compile the program. The linker would have complained about "-lavformat not found" or something like that.
Maybe that file can be found somewhere below the directory, where you built ffmpeg and was built together with it, but not installed. If you find that file, copy it to /usr/local/lib and call ldconfig.

And another hint: instead of "make install" you should use "checkinstall". That will first create a .deb-package, so your application can be removed later via synaptic.

---

### Post by cazz on 2005-11-12
Hmm that only one libavformat.so and I have is in 
/usr/local/lib

---

### Post by Harleen on 2005-11-12
That  path doesn't seem to be included in your library search path. Is it listed in your /etc/ld.so.conf? If not, append that directory and run ldconf. I remember to have to edit that file manually - though I don't know exactly anymore, if that was in hoary or breezy...

This is my ld.so.conf:

> /usr/X11R6/lib
/usr/local/lib
/usr/openwin/lib
/usr/local/lib


Edit: That double entry of course isn't necessary. Wonder, how I managed to get that in twice...

---

### Post by cazz on 2005-11-12
I dont have /etc/ld.so.conf ????

I have search but not find any ld.so.conf (locate ld.so.conf)

can I create a ld.so.conf in a editor???

---

### Post by Harleen on 2005-11-12
It's part of the base system - at least I thought so. 
I don't know if creating that file will work.

---

### Post by cazz on 2005-11-12
hmm very strange.

I have to think about it :???:

---


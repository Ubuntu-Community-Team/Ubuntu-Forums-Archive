---
title: "MPlayer compiling error"
date: 2006-01-05
forum: Desktop Environments
---

### Post by no1pointguard on 2006-01-05
hey out there! i'm an ab absolute newbie with linux and ubuntu so i apologise for my lack of knowlege. been trying to install Mplayer didnt work through synaptic so was trying through terminal using instructions from ([http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)) 
problem is when i get to 
./configure --enable-gui

i get 
Error: X11 support required for GUI compilation
can anyone help me fix this 
many thanks!

---

### Post by bjourne on 2006-01-05
install libx11-dev

---

### Post by no1pointguard on 2006-01-05
libx11-dev is installed still same problem :confused:

---

### Post by bored2k on 2006-01-05
```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot
```With all that I manage to compile mplayer **every** time.

I made a howto on this here: [http://www.ubuntuforums.org/showthread.php?t=85190](http://www.ubuntuforums.org/showthread.php?t=85190) [CVS Mplayer (the  pretty one)].

Good luck.

---

### Post by bored2k on 2006-01-05
That guide uses libx11 because it was made for Warty/Hoary, which use X11. Breezy uses Xorg, so libxv-dev is what you'd want.

---

### Post by no1pointguard on 2006-01-05
thanks but libxv-dev is also installed :confused:

---

### Post by no1pointguard on 2006-01-05
hey been using ur guide run itno more probs ie

eddie@stuED8F:~$ cvs -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg login
Logging in to :pserver:anonymous@mplayerhq.hu:2401/cvsroot/ffmpeg
CVS password:
eddie@stuED8F:~$ cvs -z3 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co -P ffmpeg
cvs checkout: Updating ffmpeg
U ffmpeg/.cvsignore
U ffmpeg/COPYING
(etc etc................)
cvs checkout: Updating ffmpeg/tests
cvs checkout: Updating ffmpeg/vhook
eddie@stuED8F:~$ cp ffmpeg/libav* main -rf
cp: `main': specified destination directory does not exist
Try `cp --help' for more information.

what to do?
thanks

---

### Post by hw-tph on 2006-01-06
[QUOTE=no1pointguard]eddie@stuED8F:~$ cp ffmpeg/libav* main -rf
cp: `main': specified destination directory does not exist[/QUOTE]

Where do you have the checked out mplayer source tree? I usually create a directory for building mplayer - ~/build/mplayer - and from there I check out the CVS sources so in ~/build/mplayer I have the "main" directory (created when checking out mplayer) and an "ffmpeg" directory with the ffmpeg/libavcodec sources. You need to copy the ffmpeg subdirectories named libav* (libavcodec, libavformat, etc) to the "main" (mplayer) directory.


Håkan

---

### Post by no1pointguard on 2006-01-06
i'm afraid i do not know how to do that please help me out from the top thanks

---


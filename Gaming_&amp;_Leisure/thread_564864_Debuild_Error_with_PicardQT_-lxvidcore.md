---
title: "Debuild Error with PicardQT -lxvidcore"
date: 2007-10-01
forum: Gaming &amp; Leisure
---

### Post by crux19 on 2007-10-01
Hello, 
Following the steps from the Musicbrainz site on building Picard on Feisty.  Having some trouble in finding lxvidcore.  Thanks for any help!  Couldn't find anything from searching.

running build_py
running build_ext
building 'picard.musicdns.avcodec' extension
gcc -pthread -shared -Wl,-O1 /root/picard-0.9.0~alpha14/./build/temp.linux-i686-2.5/picard/musicdns/avcodec.o -o /root/picard-0.9.0~alpha14/./build/lib.linux-i686-2.5/picard/musicdns/avcodec.so -lavformat -lavcodec -lz -la52 -ldts -lgsm -lmp3lame -lxvidcore -lx264_pic -ldc1394_control -lfaac -lfaad -ldl -lvorbisenc -lraw1394 -lavutil -lvorbis -lm -logg
/usr/bin/ld: cannot find -lxvidcore
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1
make: *** [python-build-stamp-2.5] Error 1
debuild: fatal error at line 1204:
couldn't exec debian/rules: 
root@holmes:~/picard-0.9.0~alpha14#

---


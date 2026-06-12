---
title: "Installing Duke Nukem Atomic Edition on Ubuntu..."
date: 2010-03-30
forum: Gaming &amp; Leisure
---

### Post by Mountain Dew Overdose on 2010-03-30
I recently got a copy of Duke Nukem Atomic Edition, I have got it to work in Windows 7, I dual boot, but not in Ubuntu...I use Ubuntu a lot more and would prefer to not have to reboot just to play it, any suggestions?

---

### Post by Lukeaxx on 2010-03-30
[http://icculus.org/~ravage/duke3d/](http://icculus.org/~ravage/duke3d/)

I just downloaded the .run file from that site... easy as eating a cake.

---

### Post by ShadowTek on 2010-03-30
I used eduke32.
[http://www.eduke32.com/](http://www.eduke32.com/)

Also, the high-res pack is a very nice addition.
[http://hrp.duke4.net/](http://hrp.duke4.net/)

---

### Post by Mountain Dew Overdose on 2010-03-30
I went with Lukeaxx's suggestion, downloaded it, ran it, and I got this...

```
tyler@lintmagnet:~/Downloads$ sudo sh duke3d_atomic_edition-x86.run
[sudo] password for tyler: 
Verifying archive integrity... All good.
Uncompressing Duke Nukem 3D: Atomic Edition for Linux.........................................................
/home/tyler/.setup12954: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

Did I do something wrong?

---

### Post by ShadowTek on 2010-03-30
> **Mountain Dew Overdose said:**
> Did I do something wrong?

Yeah, you didn't try *my* suggestion. 8)

> libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Are you using 64bit Ubuntu?

If so, you may be missing a 32bit lib.

---

### Post by TerminX on 2010-03-31
Use EDuke32; we even have an apt repo which frankly makes it easy as hell to set up.

Install package, copy duke3d.grp to /usr/share/games/eduke32, run eduke32 binary.

Disclaimer: I have spent 6 years of my life programming EDuke32, so I think it rules. :p

---

### Post by Mountain Dew Overdose on 2010-03-31
I gave up on the weird little .run installer and tried eduke32, since eduke32 is what I used to use on Windows to run it, I did everything up to the make command, and it got tons of errors...

```
tyler@lintmagnet:~/eduke32/polymer/eduke32$ make
Build started using "gcc -fomit-frame-pointer -funswitch-loops -O2 -W -Wall -Wimplicit -Werror-implicit-function-declaration -funsigned-char -fno-strict-aliasing -DNO_GCC_BUILTINS -Isource -Ibuild/include -Isource/jmact -Isource/jaudiolib/include -Isource/enet/include -D_FORTIFY_SOURCE=2 -fjump-tables -fno-stack-protector -fno-pic -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DHAVE_GTK2 -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -DHAVE_INTTYPES -DRENDERTYPESDL=1 -DSUPERBUILD -DPOLYMOST -DUSE_OPENGL -DPOLYMER"
Built object obj/sdlmusic.o 
Changing dir to /home/tyler/eduke32/polymer/eduke32/build 
Built object ../eobj/a.o 
Built object ../eobj/a-c.o 
Built object ../eobj/baselayer.o 
src/cache1d.c: In function &#8216;initgroupfile&#8217;:
src/cache1d.c:456: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
src/cache1d.c:476: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
src/cache1d.c:493: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
src/cache1d.c: In function &#8216;kdfwrite&#8217;:
src/cache1d.c:1194: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/cache1d.c:1194: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/cache1d.c:1204: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/cache1d.c:1204: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/cache1d.c:1211: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/cache1d.c:1211: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
Built object ../eobj/cache1d.o 
Built object ../eobj/compat.o 
Built object ../eobj/crc32.o 
Built object ../eobj/defs.o 
src/engine.c: In function &#8216;saveboard&#8217;:
src/engine.c:7559: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7561: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7562: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7563: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7564: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7565: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7567: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7596: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7600: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7625: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7628: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/engine.c:7662: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
Built object ../eobj/engine.o 
src/polymost.c: In function &#8216;dxtfilter&#8217;:
src/polymost.c:6199: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/polymost.c:6200: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/polymost.c:6230: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/polymost.c:6231: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/polymost.c:6266: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
src/polymost.c:6267: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
Built object ../eobj/polymost.o 
Built object ../eobj/hightile.o 
Built object ../eobj/textfont.o 
Built object ../eobj/smalltextfont.o 
src/kplib.c: In function &#8216;suckbitsnextblock&#8217;:
src/kplib.c:363: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c: In function &#8216;kzaddstack&#8217;:
src/kplib.c:2679: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2683: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2697: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2706: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2710: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2732: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:2739: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c: In function &#8216;kzopen&#8217;:
src/kplib.c:2807: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c: In function &#8216;kzread&#8217;:
src/kplib.c:3037: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
src/kplib.c:3058: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
Built object ../eobj/kplib.o 
Built object ../eobj/quicklz.o 
Built object ../eobj/md4.o 
Built object ../eobj/osd.o 
Built object ../eobj/pragmas.o 
Built object ../eobj/scriptfile.o 
src/nedmalloc.c: In function &#8216;nedblksize&#8217;:
src/nedmalloc.c:514: warning: unused variable &#8216;mspace&#8217;
src/nedmalloc.c: In function &#8216;RemoveCacheEntries&#8217;:
src/nedmalloc.c:676: warning: unused parameter &#8216;p&#8217;
src/nedmalloc.c: In function &#8216;threadcache_malloc&#8217;:
src/nedmalloc.c:778: warning: unused parameter &#8216;p&#8217;
src/nedmalloc.c: In function &#8216;ReleaseFreeInCache&#8217;:
src/nedmalloc.c:865: warning: unused parameter &#8216;mymspace&#8217;
src/nedmalloc.c: In function &#8216;threadcache_free&#8217;:
src/nedmalloc.c:901: warning: suggest parentheses around &#8216;+&#8217; inside &#8216;<<&#8217;
src/nedmalloc.c: In function &#8216;nedpmallinfo&#8217;:
src/nedmalloc.c:1444: warning: missing initializer
src/nedmalloc.c:1444: warning: (near initialization for &#8216;ret.ordblks&#8217;)
src/nedmalloc.c: In function &#8216;nedpmallopt&#8217;:
src/nedmalloc.c:1461: warning: unused parameter &#8216;p&#8217;
Built object ../eobj/nedmalloc.o 
Built object ../eobj/mdsprite.o 
Built object ../eobj/glbuild.o 
Built object ../eobj/polymer.o 
src/sdlayer.c: In function &#8216;sighandler&#8217;:
src/sdlayer.c:231: warning: unused parameter &#8216;signum&#8217;
Built object ../eobj/sdlayer.o 
Built object ../eobj/gtkbits.o 
Built object ../eobj/dynamicgtk.o 
Changing dir to /home/tyler/eduke32/polymer/eduke32 
Changing dir to /home/tyler/eduke32/polymer/eduke32/source/jaudiolib 
Built object obj/drivers.o 
Built object obj/fx_man.o 
src/multivoc.c: In function &#8216;MV_PlayLoopedWAV&#8217;:
src/multivoc.c:2198: warning: unused parameter &#8216;ptrlength&#8217;
src/multivoc.c:2200: warning: unused parameter &#8216;loopend&#8217;
src/multivoc.c: In function &#8216;MV_PlayLoopedVOC&#8217;:
src/multivoc.c:2413: warning: unused parameter &#8216;ptrlength&#8217;
Built object obj/multivoc.o 
Built object obj/mix.o 
Built object obj/mixst.o 
Built object obj/pitch.o 
src/vorbis.c: In function &#8216;close_vorbis&#8217;:
src/vorbis.c:116: warning: unused parameter &#8216;datasource&#8217;
src/vorbis.c: In function &#8216;MV_PlayLoopedVorbis&#8217;:
src/vorbis.c:305: warning: unused parameter &#8216;loopend&#8217;
Built object obj/vorbis.o 
src/driver_nosound.c: In function &#8216;NoSoundDrv_ErrorString&#8217;:
src/driver_nosound.c:32: warning: unused parameter &#8216;ErrorNumber&#8217;
src/driver_nosound.c: In function &#8216;NoSoundDrv_PCM_Init&#8217;:
src/driver_nosound.c:37: warning: unused parameter &#8216;mixrate&#8217;
src/driver_nosound.c:37: warning: unused parameter &#8216;numchannels&#8217;
src/driver_nosound.c:37: warning: unused parameter &#8216;samplebits&#8217;
src/driver_nosound.c:37: warning: unused parameter &#8216;initdata&#8217;
src/driver_nosound.c: In function &#8216;NoSoundDrv_PCM_BeginPlayback&#8217;:
src/driver_nosound.c:46: warning: unused parameter &#8216;BufferStart&#8217;
src/driver_nosound.c:46: warning: unused parameter &#8216;BufferSize&#8217;
src/driver_nosound.c:47: warning: unused parameter &#8216;NumDivisions&#8217;
src/driver_nosound.c:47: warning: unused parameter &#8216;CallBackFunc&#8217;
Built object obj/driver_nosound.o 
Built object obj/driver_sdl.o 
Changing dir to /home/tyler/eduke32/polymer/eduke32 
Changing dir to /home/tyler/eduke32/polymer/eduke32/source/enet 
Built object obj/callbacks.o 
Built object obj/host.o 
Built object obj/list.o 
Built object obj/packet.o 
Built object obj/peer.o 
src/protocol.c: In function &#8216;enet_protocol_dispatch_incoming_commands&#8217;:
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_DISCONNECTED&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTING&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_ACKNOWLEDGING_CONNECT&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTED&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_DISCONNECT_LATER&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_DISCONNECTING&#8217; not handled in switch
src/protocol.c:47: warning: enumeration value &#8216;ENET_PEER_STATE_ACKNOWLEDGING_DISCONNECT&#8217; not handled in switch
src/protocol.c: In function &#8216;enet_protocol_handle_connect&#8217;:
src/protocol.c:236: warning: unused parameter &#8216;header&#8217;
src/protocol.c: In function &#8216;enet_protocol_handle_ping&#8217;:
src/protocol.c:593: warning: unused parameter &#8216;host&#8217;
src/protocol.c:593: warning: unused parameter &#8216;peer&#8217;
src/protocol.c:593: warning: unused parameter &#8216;command&#8217;
src/protocol.c: In function &#8216;enet_protocol_handle_throttle_configure&#8217;:
src/protocol.c:620: warning: unused parameter &#8216;host&#8217;
src/protocol.c: In function &#8216;enet_protocol_handle_acknowledge&#8217;:
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_DISCONNECTED&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTING&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTION_PENDING&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTION_SUCCEEDED&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_CONNECTED&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_ACKNOWLEDGING_DISCONNECT&#8217; not handled in switch
src/protocol.c:712: warning: enumeration value &#8216;ENET_PEER_STATE_ZOMBIE&#8217; not handled in switch
Built object obj/protocol.o 
Built object obj/unix.o 
Changing dir to /home/tyler/eduke32/polymer/eduke32 
/usr/bin/ld: cannot open output file eduke32: Is a directory
collect2: ld returned 1 exit status
Failed linking executable eduke32!
make: *** [eduke32] Error 1
tyler@lintmagnet:~/eduke32/polymer/eduke32$
```
Update: Okay I eventually found out that I could apt-get install eduke32...I did that, and now I have eduke32 working and running on Linux with Duke3D. But now is another problem...the audio sounds...weird, I'm not sure how to explain it, it sounds more high pitched than it should, I tried changing all the settings and nothing helped.

Update: And now the HRP polymer is causing my computer to freeze up...

---

### Post by MrMACHOMAN84 on 2010-04-01
I have a problem, I have these .exe files but I can't install them how do I install them.

---

### Post by ShadowTek on 2010-04-01
> **MrMACHOMAN84 said:**
> I have a problem, I have these .exe files but I can't install them how do I install them.
[http://wiki.eduke32.com/wiki/Installation_and_configuration](http://wiki.eduke32.com/wiki/Installation_and_configuration)

---

### Post by MrMACHOMAN84 on 2010-04-02
thank you good sir

---

### Post by Rustybolts on 2010-04-02
> **ShadowTek said:**
> I used eduke32.
[http://www.eduke32.com/](http://www.eduke32.com/)

Also, the high-res pack is a very nice addition.
[http://hrp.duke4.net/](http://hrp.duke4.net/)

Regarding eduke could you get polymer pack working? when i run it my start menu is blank. In game most of the level is blank apart from shading old 2d sprites are now in 3d and look correct. Maybe just graphics card issues iunno.

---

### Post by ShadowTek on 2010-04-02
I've only played it to the second level, but everything worked fine that I could see.

Just make sure you have everything in the proper directory. Here's where my stuff is:
```
:~/.eduke32$ find -iname "*"
.
./grpfiles.cache
./duke3d.grp
./autoload
./autoload/duke3d.grp
./autoload/duke3d.grp/maphacks.zip
./autoload/duke3d.grp/duke3d_hrp.zip
./autoload/duke3d.grp/eduke32_mus.zip
./autoload/duke3d.grp/hrp_update.zip
./textures
./egam0.sav
./eduke32.cfg
./hrp_art_license.txt
./eduke32_binds.cfg
./textures.cache
./hrp_readme.txt

```

---

### Post by Rustybolts on 2010-04-02
> **ShadowTek said:**
> I've only played it to the second level, but everything worked fine that I could see.

Just make sure you have everything in the proper directory. Here's where my stuff is:
```
:~/.eduke32$ find -iname "*"
.
./grpfiles.cache
./duke3d.grp
./autoload
./autoload/duke3d.grp
./autoload/duke3d.grp/maphacks.zip
./autoload/duke3d.grp/duke3d_hrp.zip
./autoload/duke3d.grp/eduke32_mus.zip
./autoload/duke3d.grp/hrp_update.zip
./textures
./egam0.sav
./eduke32.cfg
./hrp_art_license.txt
./eduke32_binds.cfg
./textures.cache
./hrp_readme.txt

```
Thanks for reply !
Same file setup as above. With high resolution enabled everything apears blank except enemy sprites which are in 3d. If i slide the detail of high res texture quality slider (up or down) in video settings some more of the textures appear but not all. 
If i disable high res textures altogether everything runs fine with 3d enemies. Which is better than running original duke3d but i am disappointed not to be able to run fully high res.

---

### Post by ShadowTek on 2010-04-02
You might want to try their wiki and forum.
[http://hrp.duke4.net/wiki/doku.php](http://hrp.duke4.net/wiki/doku.php)
[http://forums.duke4.net/index.php?showforum=26](http://forums.duke4.net/index.php?showforum=26)

---


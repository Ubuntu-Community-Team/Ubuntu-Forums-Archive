---
title: "unable to run songbird"
date: 2009-02-22
forum: General Help
---

### Post by KhaaL on 2009-02-22
I've downloaded songbird 1.0 and I tried to run it without success. When I run the command
khaal@Xeraphim:~$ songbird 

I get the following output:

```

*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb25ef7a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d10454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d124b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb1c5a141]
/usr/lib/libvisual-0.4.so.0[0xb1c51407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb1c515e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb1c60ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb1cf51f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40412c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb4041b79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb404c7ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb404c993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffca44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffcf30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffd589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffdb44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b1d7e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3ffbd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3ffbe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3eedcf3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef48e1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3efb252]
/usr/share/Songbird/xulrunner/libxul.so[0xb75e5449]
/usr/share/Songbird/xulrunner/libxul.so[0xb75e490b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef82ef]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef8319]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef7ac5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef33a5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3ef3b5c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ef4841]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3efb252]
/usr/share/Songbird/xulrunner/libxul.so[0xb75e5449]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fb70f9]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fb7126]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fb69c1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4fa38b5]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4fa11e7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fa1564]
/usr/share/Songbird/xulrunner/libxul.so[0xb75c221f]
/usr/share/Songbird/xulrunner/libxul.so[0xb75c27c4]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e57a98]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6e557b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cb7685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:21 24732      /usr/share/Songbird/songbird-bin
0804e000-0804f000 rwxp 00006000 08:21 24732      /usr/share/Songbird/songbird-bin
084c7000-084e8000 rwxp 084c7000 00:00 0          [heap]
b1c40000-b1c7c000 r-xp 00000000 08:21 2725380    /usr/lib/libvisual-0.4.so.0.0.0
b1c7c000-b1c7d000 r-xp 0003b000 08:21 2725380    /usr/lib/libvisual-0.4.so.0.0.0
b1c7d000-b1c7e000 rwxp 0003c000 08:21 2725380    /usr/lib/libvisual-0.4.so.0.0.0
b1c83000-b1c99000 rwxp b1c83000 00:00 0 
b1c99000-b1cc6000 r-xp 00000000 08:21 1856030    /lib/libncurses.so.5.6
b1cc6000-b1cc9000 rwxp 0002c000 08:21 1856030    /lib/libncurses.so.5.6
b1cc9000-b1ce1000 r-xp 00000000 08:21 2725199    /usr/lib/libaa.so.1.0.4
b1ce1000-b1ce2000 r-xp 00018000 08:21 2725199    /usr/lib/libaa.so.1.0.4
b1ce2000-b1ce3000 rwxp 00019000 08:21 2725199    /usr/lib/libaa.so.1.0.4
b1ce3000-b1ce5000 rwxp b1ce3000 00:00 0 
b1ce6000-b1cee000 rwxp b1ce6000 00:00 0 
b1cf3000-b1cf9000 r-xp 00000000 08:21 2740060    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cf9000-b1cfa000 r-xp 00005000 08:21 2740060    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cfa000-b1cfb000 rwxp 00006000 08:21 2740060    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cfb000-b1cfd000 r-xp 00000000 08:21 2740111    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b1cfd000-b1cfe000 ---p 00002000 08:21 2740111    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b1cfe000-b1cff000 r-xp 00002000 08:21 2740111    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b1cff000-b1d00000 rwxp 00003000 08:21 2740111    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b1d00000-b1e00000 rwxp b1d00000 00:00 0 
b1e02000-b1e0c000 r-xp 00000000 08:21 2739470    /usr/lib/gstreamer-0.10/libgstdvdread.so
b1e0c000-b1e0d000 r-xp 00009000 08:21 2739470    /usr/lib/gstreamer-0.10/libgstdvdread.so
b1e0d000-b1e0e000 rwxp 0000a000 08:21 2739470    /usr/lib/gstreamer-0.10/libgstdvdread.so
b1e0e000-b1e16000 r-xp 00000000 08:21 2740113    /usr/lib/gstreamer-0.10/libgstpng.so
b1e16000-b1e17000 r-xp 00007000 08:21 2740113    /usr/lib/gstreamer-0.10/libgstpng.so
b1e17000-b1e18000 rwxp 00008000 08:21 2740113    /usr/lib/gstreamer-0.10/libgstpng.so
b1e18000-b1e31000 r-xp 00000000 08:21 2724467    /usr/lib/libdv.so.4.0.3
b1e31000-b1e32000 r-xp 00018000 08:21 2724467    /usr/lib/libdv.so.4.0.3
b1e32000-b1e34000 rwxp 00019000 08:21 2724467    /usr/lib/libdv.so.4.0.3
b1e34000-b1e40000 rwxp b1e34000 00:00 0 
b1e40000-b1e6a000 r-xp 00000000 08:21 2726035    /usr/lib/libmusicbrainz.so.4.0.3
b1e6a000-b1e6b000 r-xp 00029000 08:21 2726035    /usr/lib/libmusicbrainz.so.4.0.3
b1e6b000-b1e6c000 rwxp 0002a000 08:21 2726035    /usr/lib/libmusicbrainz.so.4.0.3
b1e6e000-b1e73000 r-xp 00000000 08:21 2739995    /usr/lib/gstreamer-0.10/libgsth264parse.so
b1e73000-b1e74000 r-xp 00004000 08:21 2739995    /usr/lib/gstreamer-0.10/libgsth264parse.so
b1e74000-b1e75000 rwxp 00005000 08:21 2739995    /usr/lib/gstreamer-0.10/libgsth264parse.so
b1e75000-b1e79000 r-xp 00000000 08:21 2740026    /usr/lib/gstreamer-0.10/libgstvideosignal.so
b1e79000-b1e7a000 r-xp 00003000 08:21 2740026    /usr/lib/gstreamer-0.10/libgstvideosignal.so
b1e7a000-b1e7b000 rwxp 00004000 08:21 2740026    /usr/lib/gstreamer-0.10/libgstvideosignal.so
b1e7b000-b1e80000 r-xp 00000000 08:21 2725516    /usr/lib/libgpm.so.2.0.0
b1e80000-b1e81000 r-xp 00004000 08:21 2725516    /usr/lib/libgpm.so.2.0.0
b1e81000-b1e82000 rwxp 00005000 08:21 2725516    /usr/lib/libgpm.so.2.0.0
b1e82000-b1e85000 r-xp 00000000 08:21 2740075    /usr/lib/gstreamer-0.10/libgstaasink.so
b1e85000-b1e86000 r-xp 00003000 08:21 2740075    /usr/lib/gstreamer-0.10/libgstaasink.so
b1e86000-b1e87000 rwxp 00004000 08:21 2740075    /usr/lib/gstreamer-0.10/libgstaasink.so
b1e87000-b1ef4000 r-xp 00000000 08:21 2726731    /usr/lib/libschroedinger-1.0.so.0.1.0
b1ef4000-b1ef5000 r-xp 0006d000 08:21 2726731    /usr/lib/libschroedinger-1.0.so.0.1.0
b1ef5000-b1ef6000 rwxp 0006e000 08:21 2726731    /usr/lib/libschroedinger-1.0.so.0.1.0
b1ef6000-b1ef7000 rwxp b1ef6000 00:00 0 
b1ef8000-b1f03000 r-xp 00000000 08:21 2740089    /usr/lib/gstreamer-0.10/libgstdv.so
b1f03000-b1f04000 r-xp 0000a000 08:21 2740089    /usr/lib/gstreamer-0.10/libgstdv.so
b1f04000-b1f05000 rwxp 0000b000 08:21 2740089    /usr/lib/gstreamer-0.10/libgstdv.so
b1f05000-b1f10000 r-xp 00000000 08:21 2740088    /usr/lib/gstreamer-0.10/libgstdebug.so
b1f10000-b1f11000 r-xp 0000a000 08:21 2740088    /usr/lib/gstreamer-0.10/libgstdebug.so
b1f11000-b1f12000 rwxp 0000b000 08:21 2740088    /usr/lib/gstreamer-0.10/libgstdebug.so
b1f12000-b2362000 r-xp 00000000 08:21 2756322    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2362000-b2363000 r-xp 0044f000 08:21 2756322    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2363000-b2369000 rwxp 00450000 08:21 2756322    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2369000-b245f000 rwxp b2369000 00:00 0 
b245f000-b24fc000 r-xp 00000000 08:21 2756324    /usr/lib/i686/cmov/libavformat.so.52.7.0
b24fc000-b24fd000 r-xp 0009c000 08:21 2756324    /usr/lib/i686/cmov/libavformat.so.52.7.0
b24fd000-b2500000 rwxp 0009d000 08:21 2756324    /usr/lib/i686/cmov/libavformat.so.52.7.0
b2500000-b2600000 rwxp b2500000 00:00 0 
b2604000-b2607000 r-xp 00000000 08:21 2740024    /usr/lib/gstreamer-0.10/libgsttrm.so
b2607000-b2608000 r-xp 00002000 08:21 2740024    /usr/lib/gstreamer-0.10/libgsttrm.so
b2608000-b2609000 rwxp 00003000 08:21 2740024    /usr/lib/gstreamer-0.10/libgsttrm.so
b2609000-b2615000 r-xp 00000000 08:21 2739991    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b2615000-b2616000 r-xp 0000b000 08:21 2739991    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b2616000-b2617000 rwxp 0000c000 08:21 2739991    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b2617000-b262e000 r-xp 00000000 08:21 572322     /usr/lib/gstreamer-0.10/libgstschro.so
b262e000-b262f000 r-xp 00016000 08:21 572322     /usr/lib/gstreamer-0.10/libgstschro.so
b262f000-b2630000 rwxp 00017000 08:21 572322     /usr/lib/gstreamer-0.10/libgstschro.so
b2630000-b2631000 rwxp b2630000 00:00 0 
b2631000-b265f000 r-xp 00000000 08:21 2739973    /usr/lib/gstreamer-0.10/libgstf

```

Also the process songbird-bin stays running on my system and cannot be terminated, i have to use sigkill to end it. I also trieed the beta 1.1 and 1.2 nighties with similiar results, but running songbird-bin directly gives me this error:

```
error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
```

i got xulrunner-1.9 version 1.9.0.6+nobinonly-0ubuntu0.8.10.1 installed. What could be wrong here?

---

### Post by kmac on 2009-02-22
Google for the *.deb package, someone put one together under "other builds" on their site... check it out!

---

### Post by KhaaL on 2009-02-22
this *is* the .deb package. also, my ~/.songbird folder has been removed to wipe out any eventual faulty settings

---

### Post by kmac on 2009-02-22
Ouch... already tried removing and reinstalling? 

This is what gets me: 

> ./songbird-bin: double free or corruption (out): 

Try purging and redownload the package and reinstall.

Judging by your post count, I'm assuming you've probably tried this already, but it doesn't hurt to check.

---

### Post by KhaaL on 2009-02-22
Indeed, i've tried with that already. and since i've tried with 3 different packages (1.0 stable, 1.1 beta and 1.2 nightly) i'm convinced that the error lies elsewhere. but i dont know where... Firefox shiretoko is running fine with me and i think it runs from the same base as songbird?

Sorry if i sounded harsh in my earlier reply :)

---

### Post by kmac on 2009-02-22
Are you able to locate libjemalloc.so manually on your FS? 

I looked it up and it seems to be a part of the same library as Firefox. Have you had any issues or special modifications to Firefox? Or are you even using an older version? I'm under the impression that the *.deb package used some of firefox as a dependancy and assumed that it would be present in a debian-based OS

---

### Post by KhaaL on 2009-02-22
yes, libjemalloc is present in the following folders:

khaal@Xeraphim:~/Desktop$ locate libjemalloc
/home/khaal/.local/share/Trash/files/Songbird/libjemalloc.so
/home/khaal/.local/share/Trash/files/Songbird/xulrunner/libjemalloc.so
/home/khaal/.local/share/Trash/files/Songbird.2/libjemalloc.so
/home/khaal/.local/share/Trash/files/Songbird.2/xulrunner/libjemalloc.so
/usr/lib/xulrunner-1.9.0.6/libjemalloc.so


So in this case i think that the problem is not in libjemalloc, because i have it on my system, and the one in my trash folder indicates that the earlier version i tried has its own libjemalloc with it.

hmm, the plot thickens...

---

### Post by niko7865 on 2009-03-05
I've been getting the same problem ever since i reinstalled Ubuntu 8.10.
Songbird 0.7 and before work fine however.

---

### Post by jurialmunkey on 2009-03-08
EDIT: I figured out a better, and safer, way to fix this problem... see post on next page.

---

### Post by hyperdude111 on 2009-03-08
delete every folder in your system with the word songbird sometimes synaptic does not clean the system as it should. Get a new copy of the .deb for the getdeb website and see if it works. Maybee try a different user or install see if that works.

---

### Post by Yashiro on 2009-03-08
Unless you really like the way Songbird catalogues tunes you'd be better using something else. I'm not sure why but the audio playback from Songbird is poor. 
It should be using the underlying framework but I can hear issues and artefacts on Songbird that simply do not happen on other players.
Sorry not to be able to advise on your problem but in my experience despite Songbird looking cool it's not a very good player. Something like Rhythmbox or Audacious is much better.

---

### Post by jurialmunkey on 2009-03-09
Okay, don't do what I did before.

I found out that the problem lies with the NVIDIA 180 drivers (the beta ones). The problem lies with the libvisual-0.4-plugins package. Just sudo apt-get remove it. 
```
sudo apt-get remove libvisual-0.4-plugins
```
then run songbird, set everything up in songbird (the first time run start-up config). Then close songbird. You can then apt-get install libvisual-0.4-plugins. Songbird should run fine now.

Grrr.. what a nightmare, but it is working fine now, and everything has been put back in place.

---

### Post by Marinus777 on 2009-08-30
Thanks,

that fixed it for me too!

How did you find this resolution?

I was not able to reinstall the libvisual plugin as that reintroduced the problem.

---

### Post by wodenickel on 2009-12-22
I also was not able to reinstall libvisuals as the problem returned.

I'm not sure what's now broken without libvisuals...

FYI - I use Songbird on Windows and love it. Since it can work with my IPOD I removed itunes!

Mark

---

### Post by JDorfler on 2009-12-22
Anybody know a good PPA that has the latest stable build of Songbird?

---


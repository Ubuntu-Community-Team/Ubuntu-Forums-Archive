---
title: "Google earth crashes since installing 10.10"
date: 2010-10-12
forum: Desktop Environments
---

### Post by ratcheer on 2010-10-12
After installing 10.10, yesterday, Google Earth now crashes every time I try to run it. It gives me a stack trace, but I have no idea how to read it. It seems that some of the system libraries it wants to use are messed up. I suppose I need to open a case with Google support instead of asking about it here, but there are a lot of very smart people here.

```

Major Version 5
Minor Version 2
Build Number 0001
Build Date Jul 30 2010
Build Time 02:09:03
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 11
Crash Time 1286839119
Up Time 5.29654

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0x1e090b]
[0xd88400]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_from_pixdata+0x13f)[0x6e30baf]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_new_from_inline+0x63)[0x6e30e73]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4d395)[0xa5ba2395]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4bdee)[0xa5ba0dee]
/usr/lib/flashplugin-installer/libflashplayer.so(NP_Initialize+0x1ae)[0xa5ba528e]
./libQtWebKit.so.4(+0x747b22)[0x3491b22]
./libQtWebKit.so.4(+0x747c0c)[0x3491c0c]
./libQtWebKit.so.4(+0x6062ff)[0x33502ff]
./libQtWebKit.so.4(+0x604516)[0x334e516]
./libQtWebKit.so.4(+0x60476a)[0x334e76a]
./libQtWebKit.so.4(+0x712beb)[0x345cbeb]
./libQtWebKit.so.4(+0x5b1595)[0x32fb595]
./libQtWebKit.so.4(+0x5a185c)[0x32eb85c]
./libQtWebKit.so.4(+0x5b1981)[0x32fb981]
./libQtWebKit.so.4(+0x5b199a)[0x32fb99a]
./libQtWebKit.so.4(+0xaa2c4b)[0x37ecc4b]
./libQtWebKit.so.4(+0x16ad57)[0x2eb4d57]
./libQtWebKit.so.4(+0x1749d5)[0x2ebe9d5]
./libQtWebKit.so.4(+0x183282)[0x2ecd282]
./libQtWebKit.so.4(+0x1bc22d)[0x2f0622d]
./libQtWebKit.so.4(+0x29ac5d)[0x2fe4c5d]
./libQtWebKit.so.4(+0x2a9410)[0x2ff3410]
./libQtWebKit.so.4(+0x2a9f72)[0x2ff3f72]
./libQtWebKit.so.4(+0x2b7fea)[0x3001fea]
./libQtWebKit.so.4(+0x4be45a)[0x320845a]
./libQtWebKit.so.4(+0x4bf243)[0x3209243]
./libQtWebKit.so.4(+0x4c0449)[0x320a449]
./libQtWebKit.so.4(+0x4c2a75)[0x320ca75]
./libQtWebKit.so.4(+0x4c36b8)[0x320d6b8]
./libQtWebKit.so.4(+0x4c6773)[0x3210773]
./libQtWebKit.so.4(+0x501706)[0x324b706]
./libQtWebKit.so.4(+0x5017fb)[0x324b7fb]
./libQtWebKit.so.4(+0x539f0b)[0x3283f0b]
./libQtWebKit.so.4(+0x54c290)[0x3296290]
./libQtWebKit.so.4(+0x547cc3)[0x3291cc3]
./libQtWebKit.so.4(+0x6fd155)[0x3447155]
./libQtWebKit.so.4(+0x6fd83e)[0x344783e]
./libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0x5e55a7]
./libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0x5ed5ec]
./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0x5ee03d]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0xec7e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0xed1962]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0x5dfd50]
./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0x5e0989]
./libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0x60594b]
./libQtGui.so.4(+0x1d3ca4)[0xf5cca4]
./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0x5defbf]
./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0x5df223]
./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0x5e0c05]
./libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0xec77a1]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0x1ebb0c]
./libgoogleearth_free.so(earthmain+0x27d)[0x1dfd3d]
./googleearth-bin(_init+0x12e)[0x80486d2]
/lib/libc.so.6(__libc_start_main+0xe7)[0x723ce7]
./googleearth-bin(_init+0x9d)[0x8048641]


```Any ideas would be appreciated.

Tim

---

### Post by ratcheer on 2010-10-12
Sorry, I should have posted this in General Help....

Tim

---

### Post by ratcheer on 2010-10-12
A fix is posted in the Linux support forum at Google Earth Help.

Edited ~/.config/Google/GoogleEarthPlus.conf changing "enableTips=false". maybe one day they will fix it so Tips will work.

Tim

---

### Post by Th3Alchemist on 2010-10-15
I disconnected from the internet, and opened Google Earth which showed an error since there's no internet connection, then I turned off the Tips at the options which fixed the problem the next time i Google Earth (with internet connection of course)

---

### Post by grajea on 2011-06-17
Same solution here (disconnect from internet and disable tooltips in Tools > Options > General) but have to change permisions of ~/.config/Google/GoogleEarthPlus.conf. It was owned by root and changes made through GUI did'nt persist after stop and start google-earth

---

### Post by rcjhawk on 2012-07-21
Well, I'm happy to report that after two years of waiting and upgrading to 64-bit Precise Pangolin, and adding "enableTips=false"

Google-Earth still crashes.

Wonderful, Wonderful.

---

### Post by wildmanne39 on 2012-07-21
Old thread closed.

---


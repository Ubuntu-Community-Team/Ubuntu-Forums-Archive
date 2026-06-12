---
title: "Qt(?) problem when starting mixxx software"
date: 2010-12-06
forum: Desktop Environments
---

### Post by Wim De Winter on 2010-12-06
Hi

I'm running Ubuntu 10.10 and was looking for software to mix mp3's. I want to try mixxx (found [here]("http://www.mixxx.org/")) I installed the most recent package by using the ppa of the project (as described [here]("http://www.mixxx.org/download.php")) Install seems to be ok (no error messages)

But when I try to run mixxx from the menu nothing happens. Nothing. Running it from the terminal with the command```
mixxx
```I get this error message:> mixxx: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN16QIODevicePrivate4peekEPcxCan anyone explain to me what seems to be the problem? How can this problem be solved? What more information do you need to solve it? Can you help?

I've also posted on the mixxx bug tracker in launchpad ([here)]("https://answers.launchpad.net/mixxx/+question/136031")

Thanks!

---

### Post by Wim De Winter on 2010-12-16
Some more information after a couple of hours googleing and filtering forums:

```
ldd /usr/bin/mixxx
``` results in:

> linux-gate.so.1 =>  (0x00945000)
libid3tag.so.0 => /usr/lib/libid3tag.so.0 (0x009e7000)
libmad.so.0 => /usr/lib/libmad.so.0 (0x00f32000)
libsndfile.so.1 => /usr/lib/libsndfile.so.1 (0x00e20000)
libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0x00250000)
libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x004df000)
libogg.so.0 => /usr/lib/libogg.so.0 (0x00d50000)
libGL.so.1 => /usr/lib/mesa/libGL.so.1 (0x00110000)
libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00163000)
libporttime.so.0 => /usr/lib/libporttime.so.0 (0x00dfb000)
libportmidi.so.0 => /usr/lib/libportmidi.so.0 (0x0045b000)
libQtOpenGL.so.4 => /usr/lib/libQtOpenGL.so.4 (0x00259000)
libQt3Support.so.4 => /usr/lib/libQt3Support.so.4 (0x00507000)
libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x001d3000)
libQtSvg.so.4 => /usr/lib/libQtSvg.so.4 (0x0033d000)
libQtSql.so.4 => /usr/lib/libQtSql.so.4 (0x00db7000)
libQtScript.so.4 => /usr/lib/libQtScript.so.4 (0x009f7000)
libQtXmlPatterns.so.4 => /usr/lib/libQtXmlPatterns.so.4 (0x00f49000)
libQtWebKit.so.4 => /usr/lib/libQtWebKit.so.4 (0x19ab4000)
libQtGui.so.4 => /usr/local/lib/beidqt/libQtGui.so.4 (0x0f66a000)
libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0x00806000)
libQtCore.so.4 => /usr/local/lib/beidqt/libQtCore.so.4 (0x0da63000)
libportaudio.so.2 => /usr/lib/libportaudio.so.2 (0x00216000)
libasound.so.2 => /usr/lib/libasound.so.2 (0x00395000)
libpthread.so.0 => /lib/libpthread.so.0 (0x00464000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x0159d000)
libm.so.6 => /lib/libm.so.6 (0x0047e000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x004a4000)
libc.so.6 => /lib/libc.so.6 (0x19416000)
libz.so.1 => /lib/libz.so.1 (0x004c0000)
libFLAC.so.8 => /usr/lib/libFLAC.so.8 (0x0097a000)
libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x1f89b000)
libX11.so.6 => /usr/lib/libX11.so.6 (0x0f094000)
libXext.so.6 => /usr/lib/libXext.so.6 (0x0023f000)
libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x004d5000)
libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x004d9000)
libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x007e4000)
libdrm.so.2 => /lib/libdrm.so.2 (0x007ea000)
libdl.so.2 => /lib/libdl.so.2 (0x007f4000)
libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00c82000)
libXrender.so.1 => /usr/lib/libXrender.so.1 (0x007f8000)
libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00e88000)
libphonon.so.4 => /usr/lib/libphonon.so.4 (0x00d57000)
libaudio.so.2 => /usr/lib/libaudio.so.2 (0x0092e000)
libpng12.so.0 => /lib/libpng12.so.0 (0x00cf9000)
libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x15736000)
libSM.so.6 => /usr/lib/libSM.so.6 (0x00946000)
libICE.so.6 => /usr/lib/libICE.so.6 (0x009c6000)
libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x10d14000)
libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00d1e000)
libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x0094f000)
librt.so.1 => /lib/librt.so.1 (0x00dfe000)
libjack.so.0 => /usr/lib/libjack.so.0 (0x04332000)
/lib/ld-linux.so.2 (0x0095c000)
libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00f12000)
libpulse.so.0 => /usr/lib/libpulse.so.0 (0x14c2a000)
libpulse-mainloop-glib.so.0 => /usr/lib/libpulse-mainloop-glib.so.0 (0x00954000)
libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x0aa3c000)
libXt.so.6 => /usr/lib/libXt.so.6 (0x020b7000)
libXau.so.6 => /usr/lib/libXau.so.6 (0x00802000)
libpcre.so.3 => /lib/libpcre.so.3 (0x1ca7e000)
libuuid.so.1 => /lib/libuuid.so.1 (0x009df000)
libexpat.so.1 => /lib/libexpat.so.1 (0x06998000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00e07000)
libX11-xcb.so.1 => /usr/lib/libX11-xcb.so.1 (0x00959000)
libXtst.so.6 => /usr/lib/libXtst.so.6 (0x00e0d000)
libxcb-atom.so.1 => /usr/lib/libxcb-atom.so.1 (0x00df6000)
libpulsecommon-0.9.21.so => /usr/lib/libpulsecommon-0.9.21.so (0x0b3f5000)
libXi.so.6 => /usr/lib/libXi.so.6 (0x0137a000)
libwrap.so.0 => /lib/libwrap.so.0 (0x00e13000)
libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x1d0cd000)
libnsl.so.1 => /lib/libnsl.so.1 (0x01388000)

and ```
ldd -r /usr/lib/libQtNetwork.so.4
``` results in

> linux-gate.so.1 =>  (0x00cb7000)
libQtCore.so.4 => /usr/local/lib/beidqt/libQtCore.so.4 (0x00110000)
libpthread.so.0 => /lib/libpthread.so.0 (0x004cb000)
libz.so.1 => /lib/libz.so.1 (0x0081c000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00343000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00c0f000)
libc.so.6 => /lib/libc.so.6 (0x004e5000)
libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x006fd000)
librt.so.1 => /lib/librt.so.1 (0x00bfe000)
libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00702000)
libdl.so.2 => /lib/libdl.so.2 (0x0085a000)
libm.so.6 => /lib/libm.so.6 (0x0042e000)
/lib/ld-linux.so.2 (0x00e65000)
libpcre.so.3 => /lib/libpcre.so.3 (0x00454000)
undefined symbol: _ZN16QIODevicePrivate4peekEPcx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN16QIODevicePrivate4peekEx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qDecodeDataUrlRK4QUrl	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer7elapsedEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZNK13QElapsedTimer10hasExpiredEx	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData14detach_helper2EPFvPNS_4NodeEPvEPFvS1_Eii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData7append2ERKS_	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData12allocateNodeEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData6detachEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData10createDataEi	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN13QElapsedTimer5startEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN24QNonContiguousByteDevice12disableResetEv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP9QIODevice	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory6createEP11QRingBuffer	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData4freeEPS_i	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN7QStringC1EiN2Qt14InitializationE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z9qBadAllocv	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QVariantC1EiPKvj	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN8QMapData11node_createEPPNS_4NodeEii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QHashData11free_helperEPFvPNS_4NodeEE	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData8allocateEii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _Z14qt_safe_selectiP6fd_setS0_S0_PK7timeval	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN31QNonContiguousByteDeviceFactory4wrapEP24QNonContiguousByteDevice	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN9QListData11detach_growEPii	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN15QtSharedPointer20ExternalRefCountData9getAndRefEPK7QObject	(/usr/lib/libQtNetwork.so.4)
undefined symbol: _ZN11QVectorData10reallocateEPS_iii	(/usr/lib/libQtNetwork.so.4)

Hope this helps.

---

### Post by Wim De Winter on 2010-12-17
problem solved: [http://ubuntuforums.org/showthread.php?t=1469364]("http://ubuntuforums.org/showthread.php?t=1469364")

---


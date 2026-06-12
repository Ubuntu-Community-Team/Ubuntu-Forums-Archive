---
title: "Firefox/Swiftfox crash with fullscreen"
date: 2009-02-07
forum: General Help
---

### Post by Bofur on 2009-02-07
If I try to view any time of flash content on the web with either firefox or swiftfox it works fine. However when I try to maximize the video it always crashes. Anyone have any ideas? Here is the output: ```
justin@ubuntu:~$ swiftfox
*** glibc detected *** /usr/lib/swiftfox/swiftfox-bin: munmap_chunk(): invalid pointer: 0xacf9e620 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb651a3f4]
/usr/lib/libGL.so.1[0xab39bfc5]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:01 43020      /usr/lib/swiftfox/swiftfox-bin
0804a000-0804b000 rw-p 00001000 08:01 43020      /usr/lib/swiftfox/swiftfox-bin
a3669000-a4231000 r-xp 00000000 08:01 5587068    /usr/lib/libGLcore.so.177.82
a4231000-a43d5000 rwxp 00bc8000 08:01 5587068    /usr/lib/libGLcore.so.177.82
a43d5000-a43e0000 rwxp a43d5000 00:00 0 
a43e0000-a467f000 r-xp a43e0000 00:00 0 
a467f000-a70d4000 rw-p a467f000 00:00 0 
a70d4000-a7127000 r-xp a70d4000 00:00 0 
a7127000-a745e000 rw-p a7127000 00:00 0 
a745e000-a7468000 r-xp a745e000 00:00 0 
a7468000-a966d000 rw-p a7468000 00:00 0 
a97fd000-a97fe000 ---p a97fd000 00:00 0 
a97fe000-a9ffe000 rwxp a97fe000 00:00 0 
a9ffe000-a9fff000 ---p a9ffe000 00:00 0 
a9fff000-aa7ff000 rwxp a9fff000 00:00 0 
aa7ff000-aa800000 ---p aa7ff000 00:00 0 
aa800000-ab000000 rwxp aa800000 00:00 0 
ab34b000-ab3d2000 r-xp 00000000 08:01 5587067    /usr/lib/libGL.so.177.82
ab3d2000-ab3ec000 rwxp 00087000 08:01 5587067    /usr/lib/libGL.so.177.82
ab3ec000-ab3ee000 rwxp ab3ec000 00:00 0 
ab400000-ac500000 rw-p ab400000 00:00 0 
ac56b000-ac600000 r--p 00000000 08:01 5711569    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ac600000-ac700000 rw-p ac600000 00:00 0 
ac70f000-ac798000 r--p 00000000 08:01 5711570    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
ac798000-ac7bb000 r--p 00000000 08:01 4382821    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ac7bb000-ac7dd000 r--p 00000000 08:01 4382789    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
ac7dd000-ac800000 r--p 00000000 08:01 4382810    /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf
ac800000-acb00000 rw-p ac800000 00:00 0 
acb11000-acb34000 r--p 00000000 08:01 4382821    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
acb34000-acb4d000 r--p 00000000 08:01 5709881    /usr/share/fonts/type1/gsfonts/n021003l.pfb
acb4d000-acb98000 r--p 00000000 08:01 5711573    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
acb98000-acbba000 r--p 00000000 08:01 4382789    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
acbba000-acbdd000 r--p 00000000 08:01 4382810    /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf
acbdd000-acc00000 r--p 00000000 08:01 4382812    /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf
acc00000-ace00000 rw-p acc00000 00:00 0 
ace12000-ace34000 r--p 00000000 08:01 4382789    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
ace34000-ace37000 r-xp ace34000 00:00 0 
ace37000-ad400000 rw-p ace37000 00:00 0 
ad414000-ad437000 r--p 00000000 08:01 4382821    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ad476000-ad4ba000 r--p 00000000 08:01 4382805    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
ad4ba000-ad500000 r--p 00000000 08:01 4382803    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
ad500000-ad600000 rw-p ad500000 00:00 0 
ad61a000-ad74c000 r-xp 00000000 08:01 5603337    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ad74c000-ad74d000 ---p 00132000 08:01 5603337    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ad74d000-ad755000 r--p 00132000 08:01 5603337    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ad755000-ad762000 rw-p 0013a000 08:01 5603337    /usr/lib/i686/cmov/libcrypto.so.0.9.8
ad762000-ad766000 rw-p ad762000 00:00 0 
ad766000-ad7a8000 r-xp 00000000 08:01 5603338    /usr/lib/i686/cmov/libssl.so.0.9.8
ad7a8000-ad7a9000 r--p 00041000 08:01 5603338    /usr/lib/i686/cmov/libssl.so.0.9.8
ad7a9000-ad7ac000 rw-p 00042000 08:01 5603338    /usr/lib/i686/cmov/libssl.so.0.9.8
ad7ac000-ad83b000 r-xp 00000000 08:01 5571109    /usr/lib/libkrb5.so.3.3
ad83b000-ad83d000 r--p 0008e000 08:01 5571109    /usr/lib/libkrb5.so.3.3
ad83d000-ad83e000 rw-p 00090000 08:01 5571109    /usr/lib/libkrb5.so.3.3
ad83e000-ad87a000 r-xp 00000000 08:01 5571681    /usr/lib/libcurl.so.4.1.0
ad87a000-ad87b000 r--p 0003c000 08:01 5571681    /usr/lib/libcurl.so.4.1.0
ad87b000-ad87c000 rw-p 0003d000 08:01 5571681    /usr/lib/libcurl.so.4.1.0
ad88e000-ad88f000 ---p ad88e000 00:00 0 
ad88f000-ae08f000 rwxp ad88f000 00:00 0 
ae08f000-ae090000 ---p ae08f000 00:00 0 
ae090000-ae890000 rwxp ae090000 00:00 0 
ae890000-af890000 rw-p ae890000 00:00 0 
af890000-b01e2000 r-xp 00000000 08:01 58394      /usr/lib/flashplugin-nonfree/libflashplayer.so
b01e2000-b0216000 rw-p 00951000 08:01 58394      /usr/lib/flashplugin-nonfree/libflashplayer.so
b0216000-b0900000 rw-p b0216000 00:00 0 
b090d000-b090e000 r-xp b090d000 00:00 0 
b090e000-b0912000 rw-p b090e000 00:00 0 
b0912000-b0915000 rw-s 00000000 00:09 17301534   /SYSV00000000 (deleted)
b0915000-b0918000 rw-s 00000000 00:09 17268765   /SYSV00000000 (deleted)
b0918000-b091b000 rw-s 00000000 00:09 17235996   /SYSV00000000 (deleted)
b0940000-b0968000 r-xp 00000000 08:01 5571037    /usr/lib/libgssapi_krb5.so.2.2
b0968000-b0969000 r--p 00028000 08:01 5571037    /usr/lib/libgssapi_krb5.so.2.2
b0969000-b096a000 rw-p 00029000 08:01 5571037    /usr/lib/libgssapi_krb5.so.2.2
b096a000-b096b000 ---p b096a000 00:00 0 
b096b000-b116b000 rwxp b096b000 00:00 0 
b116b000-b1200000 r--p 00000000 08:01 5711569    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b1200000-b1700000 rw-p b1200000 00:00 0 
b1702000-b1705000 rw-s 00000000 00:09 17203227   /SYSV00000000 (deleted)
b1705000-b1707000 r-xp 00000000 08:01 1687599    /lib/libkeyutils-1.2.so
b1707000-b1709000 rw-p 00001000 08:01 1687599    /lib/libkeyutils-1.2.so
b1709000-b171f000 r-xp 00000000 08:01 5574299    /usr/lib/libsasl2.so.2.0.22
b171f000-b1720000 r--p 00015000 08:01 5574299    /usr/lib/libsasl2.so.2.0.22
b1720000-b1721000 rw-p 00016000 08:01 5574299    /usr/lib/libsasl2.so.2.0.22
b1721000-b1743000 r-xp 00000000 08:01 5571074    /usr/lib/libk5crypto.so.3.1
b1743000-b1744000 r--p 00022000 08:01 5571074    /usr/lib/libk5crypto.so.3.1
b1744000-b1745000 rw-p 00023000 08:01 5571074    /usr/lib/libk5crypto.so.3.1
b1745000-b1784000 r-xp 00000000 08:01 5571270    /usr/lib/libldap_r-2.4.so.2.1.0
b1784000-b1785000 r--p 0003e000 08:01 5571270    /usr/lib/libldap_r-2.4.so.2.1.0
b1785000-b1786000 rw-p 0003f000 08:01 5571270    /usr/lib/libldap_r-2.4.so.2.1.0
b1786000-b1787000 rw-p b1786000 00:00 0 
b1787000-b17b7000 r-xp 00000000 08:01 5587045    /usr/lib/libidn.so.11.5.37
b17b7000-b17b8000 r--p 00030000 08:01 5587045    /usr/lib/libidn.so.11.5.37
b17b8000-b17b9000 rw-p 00031000 08:01 5587045    /usr/lib/libidn.so.11.5.37
b17b9000-b17fd000 r--p 00000000 08:01 4382805    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b17fd000-b17fe000 ---p b17fd000 00:00 0 
b17fe000-b1ffe000 rwxp b17fe000 00:00 0 
b1ffe000-b1fff000 ---p b1ffe000 00:00 0 
b1fff000-b27ff000 rwxp b1fff000 00:00 0 
b27ff000-b2800000 ---p b27ff000 00:00 0 
b2800000-b3000000 rwxp b2800000 00:00 0 
b3000000-b3700000 rw-p b3000000 00:00 0 
b3700000-b3703000 rw-s 00000000 00:09 17170458   /SYSV00000000 (deleted)
b3703000-b370a000 r-xp 00000000 08:01 5571120    /usr/lib/libkrb5support.so.0.1
b370a000-b370b000 r--p 00006000 08:01 5571120    /usr/lib/libkrb5support.so.0.1
b370b000-b370c000 rw-p 00007000 08:01 5571120    /usr/lib/libkrb5support.so.0.1
b370c000-b3718000 r-xp 00000000 08:01 5571269    /usr/lib/liblber-2.4.so.2.1.0
b3718000-b3719000 r--p 0000b000 08:01 5571269    /usr/lib/liblber-2.4.so.2.1.0
b3719000-b371a000 rw-p 0000c000 08:01 5571269    /usr/lib/liblber-2.4.so.2.1.0
b371a000-b3760000 r--p 00000000 08:01 4382803    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b3760000-b3769000 r-xp 00000000 08:01 148342     /usr/lib/swiftfox/components/libmozgnome.so
b3769000-b376a000 rw-p 00008000 08:01 148342     /usr/lib/swiftfox/components/libmozgnome.so
b376a000-b37ff000 r--p 00000000 08:01 5711569    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b37ff000-b3800000 ---p b37ff000 00:00 0 
b3800000-b4000000 rwxp b3800000 00:00 0 
b4000000-b4100000 rw-p b4000000 00:00 0 
b4100000-b4102000 r-xp 00000000 08:01 1687702    /lib/libcom_err.so.2.1
b4102000-b4103000 r--p 00001000 08:01 1687702    /lib/libcom_err.so.2.1
b4103000-b4104000 rw-p 00002000 08:01 1687702    /lib/libcom_err.so.2.1
b4104000-b4144000 r-xp 00000000 08:01 43015      /usr/lib/swiftfox/libnssckbi.so
b4144000-b414f000 rw-p 00040000 08:01 43Aborted
justin@ubuntu:~$ 

```

---

### Post by matsuguest on 2009-05-12
try this which i found on swiftfox...maybe it helps  :)
[http://forums.getswiftfox.com/viewtopic.php?t=401&sid=f29b392e0b11de4b8e73a8717d3e388d]("http://forums.getswiftfox.com/viewtopic.php?t=401&sid=f29b392e0b11de4b8e73a8717d3e388d")

---

### Post by Newshot on 2009-05-14
I read what they said, but I am new to linux.
Can you walk me through what I have to do?

---


---
title: "Browsers crashing...  Opera and Firefox.   Flash seems to be the problem."
date: 2008-12-05
forum: General Help
---

### Post by ender1598 on 2008-12-05
Okay this problem seems to be going on since I upgraded to 8.10.  It seems to be centered around Flash but I'm not 100% certain.  Sometimes Firefox will just go poof when using flash at various sites like hulu.com or youtube.com.  Strangely enough it will also just abrubtly close on sites that don't seem to have flash.  Then again, sometimes it will just freeze up and go nonresponsibe.  Now the crazy thing is that Opera is doing the same thing with seemingly random sites even though I do not have plugins enabled and am not using flash with it.  For some reason flash is still really buggy with Opera so I don't even try to use it there.  

So far I've tried completely removing Firefox and completely removing flash and reinstalling them.  There's a few threads I've found which have given directions on reinstalling these two and I've done it several ways.  I've installed the linux version of flash from Adobe and it still crashes.  What's odd is even though I install the newest version from Adobe the update manager says there's a newer version available.  I install this version and it still crashes.  This is becoming VERY annoying and any help would be nice.  I'm also not using any plugins with Firefox except for the basic Ubuntu one that comes automatically.  I have tried disabing that and the browser still crashes.

I did run Firefox from the command line and here's what comes out with one of the crashes while watching something with flash.

*** glibc detected *** /usr/lib/firefox-3.0.4/firefox: double free or corruption (fasttop): 0xb304eec0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cef3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7cf1456]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb1792503]
/lib/libnss_wins.so.2[0xb19ba289]
/usr/lib/libtalloc.so.1(talloc_free+0x271)[0xb1792621]
/lib/libnss_wins.so.2(alloc_sub_basic+0xa87)[0xb19e57a8]
/lib/libnss_wins.so.2(talloc_sub_basic+0x33)[0xb19e5d8f]
/lib/libnss_wins.so.2[0xb1925281]
/lib/libnss_wins.so.2(lp_lockdir+0x27)[0xb19263f2]
/lib/libnss_wins.so.2(lock_path+0x17)[0xb19dfac5]
/lib/libnss_wins.so.2(receive_unexpected+0x21)[0xb197e767]
/lib/libnss_wins.so.2(receive_nmb_packet+0x65)[0xb1981375]
/lib/libnss_wins.so.2(name_query+0x32e)[0xb1983e4d]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x38a)[0xb1921555]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x4f)[0xb1921853]
/lib/tls/i686/cmov/libc.so.6[0xb7d45666]
/lib/tls/i686/cmov/libc.so.6(getaddrinfo+0x1c9)[0xb7d47039]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x129)[0xb7bc06b9]
/usr/lib/xulrunner-1.9.0.4/libxul.so[0xb71a1818]
/usr/lib/libnspr4.so.0d[0xb7bce1e1]
/lib/tls/i686/cmov/libpthread.so.0[0xb7f0d50f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7d617ee]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
0804f000-08050000 r--p 00006000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
08050000-08051000 rw-p 00007000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
08a94000-0ab96000 rw-p 08a94000 00:00 0          [heap]
9f1f7000-a21f8000 rw-p 9f1f7000 00:00 0 
a29f9000-a29fa000 ---p a29f9000 00:00 0 
a29fa000-a31fa000 rwxp a29fa000 00:00 0 
a3dfd000-a3dfe000 ---p a3dfd000 00:00 0 
a3dfe000-a45fe000 rwxp a3dfe000 00:00 0 
a5800000-a58e4000 rw-p a5800000 00:00 0 
a58e4000-a5900000 ---p a58e4000 00:00 0 
a6200000-a62fe000 rw-p a6200000 00:00 0 
a62fe000-a6300000 ---p a62fe000 00:00 0 
a6359000-a7299000 ---p a6359000 00:00 0 
a7299000-a7359000 rw-p a7299000 00:00 0 
a7359000-a7b02000 ---p a7359000 00:00 0 
a7b02000-a8283000 rw-p a7b02000 00:00 0 
a8283000-a8284000 ---p a8283000 00:00 0 
a8284000-a8359000 rw-p a8284000 00:00 0 
a8359000-a8c8a000 ---p a8359000 00:00 0 
a8c8a000-a8e44000 rw-p a8c8a000 00:00 0 
a8e44000-a932e000 ---p a8e44000 00:00 0 
a932e000-a9359000 rw-p a932e000 00:00 0 
a9359000-aa2d9000 ---p a9359000 00:00 0 
aa2d9000-aa359000 rw-p aa2d9000 00:00 0 
abd00000-abe00000 rw-p abd00000 00:00 0 
ac651000-ac652000 ---p ac651000 00:00 0 
ac652000-ace52000 rwxp ac652000 00:00 0 
ace52000-ace53000 ---p ace52000 00:00 0 
ace53000-ad653000 rwxp ace53000 00:00 0 
ad854000-ad8a2000 r-xp 00000000 08:01 4820319    /usr/lib/libpulse.so.0.4.1
ad8a2000-ad8a3000 r--p 0004d000 08:01 4820319    /usr/lib/libpulse.so.0.4.1
ad8a3000-ad8a4000 rw-p 0004e000 08:01 4820319    /usr/lib/libpulse.so.0.4.1
ae8b5000-ae8d8000 r--p 00000000 08:01 4153447    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ae9f4000-aeb26000 r-xp 00000000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb26000-aeb2e000 r--p 00132000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb2e000-aeb3b000 rw-p 0013a000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeb3b000-aeb3f000 rw-p aeb3b000 00:00 0 
aeb3f000-aeb81000 r-xp 00000000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb81000-aeb82000 r--p 00041000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb82000-aeb85000 rw-p 00042000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb85000-aeb86000 ---p aeb85000 00:00 0 
aeb86000-af386000 rwxp aeb86000 00:00 0 
af386000-af387000 ---p af386000 00:00 0 
af387000-afb87000 rwxp af387000 00:00 0 
afb87000-afb99000 r-xp 00000000 08:01 4907142    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
afb99000-afb9a000 r--p 00011000 08:01 4907142    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
afb9a000-afb9b000 rw-p 00012000 08:01 4907142    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
afb9b000-afbab000 r-xp 00000000 08:01 4907141    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
afbab000-afbac000 r--p 0000f000 08:01 4907141    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
afbac000-afbad000 rw-p 00010000 08:01 4907141    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
afbad000-afbc5000 r-xp 00000000 08:01 4907140    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
afbc5000-afbc6000 r--p 00018000 08:01 4907140    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
afbc6000-afbc7000 rw-p 00019000 08:01 4907140    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
afbc7000-afbd7000 r-xp 00000000 08:01 4907137    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
afbd7000-afbd8000 r--p 0000f000 08:01 4907137    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
afbd8000-afbd9000 rw-p 00010000 08:01 4907137    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
afbd9000-afbf8000 rw-p afbd9000 00:00 0 
afbf8000-b02ff000 ---p afbf8000 00:00 0 
b02ff000-b045a000 rw-p b02ff000 00:00 0 
b045a000-b0bd9000 ---p b045a000 00:00 0 
b0bda000-b0bdc000 r-xp 00000000 08:01 4818297    /usr/lib/libtotem-plparser-mini.so.12.0.3
b0bdc000-b0bdd000 r--p 00001000 08:01 4818297    /usr/lib/libtotem-plparser-mini.so.12.0.3
b0bdd000-b0bde000 rw-p 00002000 08:01 4818297    /usr/lib/libtotem-plparser-mini.so.12.0.3
b0bde000-b0be0000 r-xp 00000000 08:01 4907341    /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
b0be0000-b0be1000 r--p 00001000 08:01 4907341    /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
b0be1000-b0be2000 rw-p 00002000 08:01 4907341    /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
b0be2000-b0be6000 r-xp 00000000 08:01 4907342    /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b0be6000-b0be7000 r--p 00003000 08:01 4907342    /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b0be7000-b0be8000 rw-p 00004000 08:01 4907342    /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b0be8000-b1539000 r-xp 00000000 08:01 295853     /usr/lib/flashplugin-nonfree/libflashplayer.so
b1539000-b156c000 rw-p 00950000 08:01 295853     /usr/lib/flashplugin-nonfree/libflashplayer.so
b156c000-b1657000 rw-p b156c000 00:00 0 
b1673000-b1685000 r--p 00000000 08:01 18230      /usr/share/fonts/type1/gsfonts/n019004l.pfb
b1685000-b1699000 r--p 00000000 08:01 18227      /usr/share/fonts/type1/gsfonts/n019003l.pfb
b1699000-b16c9000 r-xp 00000000 08:01 4820109    /usr/lib/libidn.so.11.5.37
b16c9000-b16ca000 r--p 00030000 08:01 4820109    /usr/lib/libidn.so.11.5.37
b16ca000-b16cb000 rw-p 00031000 08:01 4820109    /usr/lib/libidn.so.11.5.37
b16cb000-b1707000 r-xp 00000000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
b1707000-b1708000 r--p 0003c000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
b1708000-b1709000 rw-p 0003d000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
b1709000-b170c000 r-xp 00000000 08:01 3088426    /lib/libcap.so.1.10
b170c000-b170d000 rw-p 00002000 08:01 3088426    /lib/libcap.so.1.10
b170d000-b1712000 r-xp 00000000 08:01 4833921    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b1712000-b1713000 r--p 00004000 08:01 4833921    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b1713000-b1714000 rw-p 00005000 08:01 4833921    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
b1718000-b1728000 r--s 00000000 08:01 4908428    /usr/share/samba/valid.dat
b1728000-b1748000 r--s 00000000 08:01 4908420    /usr/share/samba/lowcase.dat
b1748000-b1768000 r--s 00000000 08:01 4908427    /usr/share/samba/upcase.dat
b1768000-b176a000 r-xp 00000000 08:01 3088455    /lib/libkeyutils-1.2.so
b176a000-b176c000 rw-p 00001000 08:01 3088455    /lib/libkeyutils-1.2.so
b176c000-b1773000 r-xp 00000000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b1773000-b1774000 r--p 00006000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b1774000-b1775000 rw-p 00007000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b1775000-b178b000 r-xp 00000000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b178b000-b178c000 r--p 00015000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b178c000-b178d000 rw-p 00016000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b178d000-b1794000 r-xp 00000000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b1794000-b1795000 r--p 00006000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b1795000-b1796000 rw-p 00007000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b1796000-b179f000 r-xp 00000000 08:01 3106141    /lib/tls/i686/cmov/libcrypt-Aborted

---

### Post by ender1598 on 2008-12-05
This is what the command line shows when Firefox just freezes and I have to force it to quit.  I'll try to get a command line output from Opera next.

*** glibc detected *** /usr/lib/firefox-3.0.4/firefox: double free or corruption (fasttop): 0x09606e90 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7df63f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7df8456]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb1894503]
/lib/libnss_wins.so.2[0xb1ac6289]
/usr/lib/libtalloc.so.1(talloc_free+0x271)[0xb1894621]
/lib/libnss_wins.so.2(alloc_sub_basic+0xa87)[0xb1af17a8]
/lib/libnss_wins.so.2(talloc_sub_basic+0x33)[0xb1af1d8f]
/lib/libnss_wins.so.2[0xb1a31281]
/lib/libnss_wins.so.2(lp_lockdir+0x27)[0xb1a323f2]
/lib/libnss_wins.so.2(lock_path+0x17)[0xb1aebac5]
/lib/libnss_wins.so.2(receive_unexpected+0x21)[0xb1a8a767]
/lib/libnss_wins.so.2(receive_nmb_packet+0x65)[0xb1a8d375]
/lib/libnss_wins.so.2(name_query+0x32e)[0xb1a8fe4d]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x38a)[0xb1a2d555]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x4f)[0xb1a2d853]
/lib/tls/i686/cmov/libc.so.6[0xb7e4c666]
/lib/tls/i686/cmov/libc.so.6(getaddrinfo+0x1c9)[0xb7e4e039]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x129)[0xb7cc76b9]
/usr/lib/xulrunner-1.9.0.4/libxul.so[0xb72a8818]
/usr/lib/libnspr4.so.0d[0xb7cd51e1]
/lib/tls/i686/cmov/libpthread.so.0[0xb801450f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7e687ee]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
0804f000-08050000 r--p 00006000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
08050000-08051000 rw-p 00007000 08:01 116952     /usr/lib/firefox-3.0.4/firefox
0853d000-0b04e000 rw-p 0853d000 00:00 0          [heap]
ac953000-ac954000 ---p ac953000 00:00 0 
ac954000-ad154000 rwxp ac954000 00:00 0 
adc00000-adcdc000 rw-p adc00000 00:00 0 
adcdc000-add00000 ---p adcdc000 00:00 0 
add00000-adde2000 rw-p add00000 00:00 0 
adde2000-ade00000 ---p adde2000 00:00 0 
ade00000-adf00000 rw-p ade00000 00:00 0 
adf6c000-adfb6000 rw-s 00000000 00:09 16416829   /SYSV00000000 (deleted)
adfb6000-ae000000 rw-s 00000000 00:09 16384060   /SYSV00000000 (deleted)
ae000000-ae100000 rw-p ae000000 00:00 0 
ae105000-ae196000 rw-s 00000000 00:09 16318522   /SYSV00000000 (deleted)
ae196000-ae197000 ---p ae196000 00:00 0 
ae197000-ae997000 rwxp ae197000 00:00 0 
ae997000-aeac9000 r-xp 00000000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeac9000-aead1000 r--p 00132000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aead1000-aeade000 rw-p 0013a000 08:01 4843063    /usr/lib/i686/cmov/libcrypto.so.0.9.8
aeade000-aeae2000 rw-p aeade000 00:00 0 
aeae2000-aeb24000 r-xp 00000000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb24000-aeb25000 r--p 00041000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb25000-aeb28000 rw-p 00042000 08:01 4843064    /usr/lib/i686/cmov/libssl.so.0.9.8
aeb28000-aeb58000 r-xp 00000000 08:01 4820109    /usr/lib/libidn.so.11.5.37
aeb58000-aeb59000 r--p 00030000 08:01 4820109    /usr/lib/libidn.so.11.5.37
aeb59000-aeb5a000 rw-p 00031000 08:01 4820109    /usr/lib/libidn.so.11.5.37
aeb5a000-aeb96000 r-xp 00000000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
aeb96000-aeb97000 r--p 0003c000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
aeb97000-aeb98000 rw-p 0003d000 08:01 4819726    /usr/lib/libcurl.so.4.1.0
aeb98000-aebdc000 r--p 00000000 08:01 4153431    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
aebec000-aec36000 rw-s 00000000 00:09 16351291   /SYSV00000000 (deleted)
aec36000-aec58000 r--p 00000000 08:01 4153415    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
aec58000-aec59000 ---p aec58000 00:00 0 
aec59000-af459000 rwxp aec59000 00:00 0 
af459000-af470000 r--s 00000000 08:01 4907165    /usr/share/mime/mime.cache
af470000-af477000 r-xp 00000000 08:01 4819806    /usr/lib/libfam.so.0.0.0
af477000-af478000 rw-p 00006000 08:01 4819806    /usr/lib/libfam.so.0.0.0
af478000-af47e000 r-xp 00000000 08:01 3088409    /lib/libacl.so.1.1.0
af47e000-af480000 rw-p 00005000 08:01 3088409    /lib/libacl.so.1.1.0
af48f000-af49b000 r-xp 00000000 08:01 4842916    /usr/lib/gnome-vfs-2.0/modules/libfile.so
af49b000-af49c000 r--p 0000b000 08:01 4842916    /usr/lib/gnome-vfs-2.0/modules/libfile.so
af49c000-af49d000 rw-p 0000c000 08:01 4842916    /usr/lib/gnome-vfs-2.0/modules/libfile.so
af49d000-af4af000 r-xp 00000000 08:01 4907142    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
af4af000-af4b0000 r--p 00011000 08:01 4907142    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
af4b0000-af4b1000 rw-p 00012000 08:01 4907142    /usr/lib/totem/gstreamer/libKilled

---

### Post by hackapelite on 2008-12-05
Almost certainly Flash *is* the problem. Also, almost certainly you can do nothing about it. Flash is proprietary and developed by Adobe so it's up to them to release updates & whatnot, but they're slow with their development on Linux and the newest version is known to be even more buggy than some of the older ones (and they generally are rather buggy). All you can do is wait, unless there are open source Flash plugins (which I doubt, but you never know...maybe someone more experienced can tell us?)...

---

### Post by ender1598 on 2008-12-05
That still doesn't explain why my Opera is crashing randomly in a similar fashion to Firefox and I do not have plugins enabled.  Of course now that I'm trying to get a command line output from the crash it doesn't want to crash on me......

---

### Post by ender1598 on 2008-12-06
Here's the output from Opera when it crashes and goes poof.  I do not have plugins enabled so I'm not sure how flash could still be the problem.

*** glibc detected *** /usr/lib/opera/9.62/opera: double free or corruption (fasttop): 0x0b9f9e58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74ea3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb74ec456]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb52a6503]
/lib/libnss_wins.so.2(alloc_sub_basic+0xa87)[0xb54337a8]
/lib/libnss_wins.so.2(talloc_sub_basic+0x33)[0xb5433d8f]
/lib/libnss_wins.so.2[0xb5373281]
/lib/libnss_wins.so.2(lp_lockdir+0x27)[0xb53743f2]
/lib/libnss_wins.so.2(lock_path+0x17)[0xb542dac5]
/lib/libnss_wins.so.2(receive_unexpected+0x21)[0xb53cc767]
/lib/libnss_wins.so.2(receive_nmb_packet+0x65)[0xb53cf375]
/lib/libnss_wins.so.2(name_query+0x32e)[0xb53d1e4d]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x38a)[0xb536f555]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x4f)[0xb536f853]
/lib/tls/i686/cmov/libc.so.6(gethostbyname2_r+0x1b2)[0xb75767e2]
/usr/lib/opera/9.62/opera[0x8933a3a]
/usr/lib/opera/9.62/opera[0x89343e9]
/usr/lib/opera/9.62/opera[0x8934769]
/lib/tls/i686/cmov/libpthread.so.0[0xb771e50f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb755c7ee]
======= Memory map: ========
06000000-0642a000 r-xp 00000000 08:01 237652     /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/libjvm.so
0642a000-06444000 rw-p 0042a000 08:01 237652     /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/client/libjvm.so
06444000-06864000 rw-p 06444000 00:00 0 
08048000-08aef000 r-xp 00000000 08:01 229900     /usr/lib/opera/9.62/opera
08aef000-08b44000 rw-p 00aa6000 08:01 229900     /usr/lib/opera/9.62/opera
08b44000-08b48000 rw-p 08b44000 00:00 0 
0a7a1000-0c011000 rw-p 0a7a1000 00:00 0          [heap]
a75fd000-a75fe000 ---p a75fd000 00:00 0 
a75fe000-a7dfe000 rwxp a75fe000 00:00 0 
a8e00000-a8ef1000 rw-p a8e00000 00:00 0 
a8ef1000-a8f00000 ---p a8ef1000 00:00 0 
a8ffd000-a8ffe000 ---p a8ffd000 00:00 0 
a8ffe000-a97fe000 rwxp a8ffe000 00:00 0 
a9fff000-aa000000 ---p a9fff000 00:00 0 
aa000000-aa800000 rwxp aa000000 00:00 0 
aa800000-aa8f7000 rw-p aa800000 00:00 0 
aa8f7000-aa900000 ---p aa8f7000 00:00 0 
aaa00000-aaae4000 rw-p aaa00000 00:00 0 
aaae4000-aab00000 ---p aaae4000 00:00 0 
aab00000-aac00000 rw-p aab00000 00:00 0 
aac00000-aace6000 rw-p aac00000 00:00 0 
aace6000-aad00000 ---p aace6000 00:00 0 
ab600000-ab6fd000 rw-p ab600000 00:00 0 
ab6fd000-ab700000 ---p ab6fd000 00:00 0 
ac000000-ac0f7000 rw-p ac000000 00:00 0 
ac0f7000-ac100000 ---p ac0f7000 00:00 0 
ac700000-ac7fe000 rw-p ac700000 00:00 0 
ac7fe000-ac800000 ---p ac7fe000 00:00 0 
ac900000-aca00000 rw-p ac900000 00:00 0 
ad300000-ad3fd000 rw-p ad300000 00:00 0 
ad3fd000-ad400000 ---p ad3fd000 00:00 0 
ad47a000-ad4fc000 rw-p ad47a000 00:00 0 
ad4fc000-ad4fd000 ---p ad4fc000 00:00 0 
ad4fd000-adcfd000 rwxp ad4fd000 00:00 0 
adcfd000-adcfe000 ---p adcfd000 00:00 0 
adcfe000-ae4fe000 rwxp adcfe000 00:00 0 
af500000-af5fe000 rw-p af500000 00:00 0 
af5fe000-af600000 ---p af5fe000 00:00 0 
afe73000-affff000 rw-p afe73000 00:00 0 
b0800000-b08f3000 rw-p b0800000 00:00 0 
b08f3000-b0900000 ---p b08f3000 00:00 0 
b0939000-b09ff000 rw-p b0939000 00:00 0 
b1200000-b1300000 rw-p b1200000 00:00 0 
b1317000-b1339000 r--p 00000000 08:01 4153415    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
b1339000-b13ff000 rw-p b1339000 00:00 0 
b1c00000-b1c01000 ---p b1c00000 00:00 0 
b1c01000-b2401000 rwxp b1c01000 00:00 0 
b2401000-b2402000 ---p b2401000 00:00 0 
b2402000-b2c02000 rwxp b2402000 00:00 0 
b2c02000-b2c03000 ---p b2c02000 00:00 0 
b2c03000-b3403000 rwxp b2c03000 00:00 0 
b3403000-b3404000 ---p b3403000 00:00 0 
b3404000-b3c04000 rwxp b3404000 00:00 0 
b3c04000-b3c05000 ---p b3c04000 00:00 0 
b3c05000-b4405000 rwxp b3c05000 00:00 0 
b4405000-b450d000 rw-p b4405000 00:00 0 
b450f000-b4532000 r--p 00000000 08:01 4153447    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b4538000-b455e000 r--p 00000000 08:01 4153445    /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
b457d000-b459c000 r--p 00000000 08:01 4153413    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b459c000-b45ac000 r--s 00000000 08:01 4908428    /usr/share/samba/valid.dat
b45ac000-b45cc000 r--s 00000000 08:01 4908420    /usr/share/samba/lowcase.dat
b45cc000-b45ec000 r--s 00000000 08:01 4908427    /usr/share/samba/upcase.dat
b45ec000-b45ee000 r-xp 00000000 08:01 3088475    /lib/libnss_mdns4.so.2
b45ee000-b45ef000 rw-p 00001000 08:01 3088475    /lib/libnss_mdns4.so.2
b4800000-b48f4000 rw-p b4800000 00:00 0 
b48f4000-b4900000 ---p b48f4000 00:00 0 
b4900000-b4941000 rw-p b4900000 00:00 0 
b4941000-b4a00000 ---p b4941000 00:00 0 
b4a00000-b4ae9000 rw-p b4a00000 00:00 0 
b4ae9000-b4b00000 ---p b4ae9000 00:00 0 
b4b08000-b4b70000 rw-p b4b08000 00:00 0 
b4b70000-b4b7e000 r--p 00000000 08:01 18158      /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMoBI.ttf
b4b7e000-b4b8a000 r--p 00000000 08:01 18159      /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMoBd.ttf
b4b8a000-b4c00000 rw-p b4b8a000 00:00 0 
b4c00000-b4cf4000 rw-p b4c00000 00:00 0 
b4cf4000-b4d00000 ---p b4cf4000 00:00 0 
b4d00000-b4dd8000 rw-p b4d00000 00:00 0 
b4dd8000-b4e00000 ---p b4dd8000 00:00 0 
b4e00000-b4fed000 rw-p b4e00000 00:00 0 
b4fed000-b5000000 ---p b4fed000 00:00 0 
b5000000-b50f1000 rw-p b5000000 00:00 0 
b50f1000-b5100000 ---p b50f1000 00:00 0 
b510e000-b514f000 rw-p b510e000 00:00 0 
b515a000-b515e000 r-xp 00000000 08:01 3106152    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b515e000-b515f000 r--p 00003000 08:01 3106152    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b515f000-b5160000 rw-p 00004000 08:01 3106152    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b5160000-b5163000 r-xp 00000000 08:01 3088450    /lib/libgpg-error.so.0.3.0
b5163000-b5164000 rw-p 00002000 08:01 3088450    /lib/libgpg-error.so.0.3.0
b5164000-b5166000 r-xp 00000000 08:01 3088455    /lib/libkeyutils-1.2.so
b5166000-b5168000 rw-p 00001000 08:01 3088455    /lib/libkeyutils-1.2.so
b5168000-b516f000 r-xp 00000000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b516f000-b5170000 r--p 00006000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b5170000-b5171000 rw-p 00007000 08:01 4820135    /usr/lib/libkrb5support.so.0.1
b5171000-b51d7000 r-xp 00000000 08:01 3088448    /lib/libgcrypt.so.11.4.4
b51d7000-b51d8000 r--p 00065000 08:01 3088448    /lib/libgcrypt.so.11.4.4
b51d8000-b51da000 rw-p 00066000 08:01 3088448    /lib/libgcrypt.so.11.4.4
b51da000-b51ea000 r-xp 00000000 08:01 4820415    /usr/lib/libtasn1.so.3.0.15
b51ea000-b51ec000 rw-p 0000f000 08:01 4820415    /usr/lib/libtasn1.so.3.0.15
b51ec000-b5283000 r-xp 00000000 08:01 4817673    /usr/lib/libgnutls.so.26.4.5
b5283000-b5288000 r--p 00096000 08:01 4817673    /usr/lib/libgnutls.so.26.4.5
b5288000-b5289000 rw-p 0009b000 08:01 4817673    /usr/lib/libgnutls.so.26.4.5
b5289000-b529f000 r-xp 00000000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b529f000-b52a0000 r--p 00015000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b52a0000-b52a1000 rw-p 00016000 08:01 4820355    /usr/lib/libsasl2.so.2.0.22
b52a1000-b52a8000 r-xp 00000000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b52a8000-b52a9000 r--p 00006000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b52a9000-b52aa000 rw-p 00007000 08:01 4820413    /usr/lib/libtalloc.so.1.2.0
b52aa000-b5339000 r-xp 00000000 08:01 4820133    /usr/lib/libkrb5.so.3.3
b5339000-b533b000 r--p 0008e000 08:01 4820133    /usr/lib/libkrb5.so.3.3
b533b000-b533c000 rw-p 00090000 08:01 4820133    /usr/lib/libkrb5.so.3.3
b533c000-b54f6000 r-xp 00000000 08:01 3088699    /lib/libnss_wins.so.2
b54f6000-b54fa000 r--p 001b9000 08:01 3088699    /lib/libnss_wins.so.2
b54fa000-b54ff000 rw-p 001bd000 08:01 3088699    /lib/libnss_wins.so.2
b54ff000-b5500000 rw-p b54ff000 00:00 0 
b5500000-b5600000 rw-p b5500000 00:00 0 
b5601000-b5611000 r-xp 00000000 08:01 3106165    /lib/tls/i686/cmov/libresolv-2.8.90.so
b5611000-b5612000 r--p 0000f000 08:01 3106165    /lib/tls/i686/cmov/libresolv-2.8.90.so
b5612000-b5613000 rw-p 00010000 08:01 3106165    /lib/tls/i686/cmov/libresolv-2.8.90.so
b5613000-b5615000 rw-p b5613000 00:00 0 
b5615000-b561e000 r-xp 00000000 08:01 3106141    /lib/tls/i686/cmov/libcrypt-2.8.90.so
b561e000-b561f000 r--p 00008000 08:01 3106141    /lib/tls/i686/cmov/libcrypt-2.8.90.so
b561f000-b5620000 rw-p 00009000 08:01 3106141    /Aborted

---

### Post by ameno on 2009-01-01
i have a similar issue.. though i dont get any output from the browsers but "aborted". first i thought its just opera... but then i tried ff and exactly the same.
i dont have plugins enabled either in opera.
do i have to enable backtraces somehow? install the debug symbols?
/me == xserver n00b
my guts tell me, its not flash. it happens ALL the time, absolutely randomly.
the only thing i noticed: there has to be some (network) activity.. it happens most often, when i follow a link. i cant remember any other circumstances at all.
what are your specs?
im on plain gnome and xorg intel drivers (g45 chipset).



EDIT:
my question about how to get the backtraces remains.. but im quite sure everyone interested in this topic wants to read:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286119](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286119)
[http://ubuntuforums.org/showpost.php?p=6404606&postcount=39](http://ubuntuforums.org/showpost.php?p=6404606&postcount=39)

---

### Post by dazzlindonna on 2009-01-02
Same issue here.  Poof! goes Firefox at any old random time since I upgraded to 8.10 yesterday.  Doesn't seem to be Flash related to me, but it does seem to be random

---

### Post by ameno on 2009-01-02
its a bug in winbind, see the bug report i posted

---

### Post by jg1395 on 2009-01-02
sweet...  :popcorn:  for the tragedy

so to understand this correctly:

if you have 8.04 or 8.10, web browser, flash, and windows networking you are screwed and it's a known bug since Oct?

Is it Samba? Can you avoid the bug by just using NFS?  Any Easy work arounds?

---


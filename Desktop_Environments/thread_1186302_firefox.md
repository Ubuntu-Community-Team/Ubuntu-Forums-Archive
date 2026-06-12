---
title: "firefox"
date: 2009-06-13
forum: Desktop Environments
---

### Post by Mosaab on 2009-06-13
hi 

I have a problem with browsers in general here... they crash unexpectedly!!
they crash SOMETIMES while loading a page from the net. and when I say crashes I mean just disapears! like if something killed the process.. with no error messages and it doesnt hang before it disappears.

is there any log file that I can check?

---

### Post by Mosaab on 2009-06-13
By the way .. the same thing happens with firefox, Opera and epiphany!

---

### Post by NilsE on 2009-06-13
I have seen that happen with a certain version of Flash and one of the Flash clones but I can't remember which one..  It has stopped happening with the latest version so make sure you for one have the real flash installed and it is the latest version.

The one you want is adobe-flashplugin 10.0.22.87-2 from the repos.  Make sure none of the other flashes are installed like swf.  If you use Synaptic and do a "quick search" for "flash" it is the only one that should be installed

---

### Post by Mosaab on 2009-06-13
I found adobe flash and non free flash....I removed the non free..
but I wanna say here that i dont think its about flash .. because some times it happens when I access pages that dont include flash .. like google.com!

anyway I will try it now ... I may need some time
thanks

---

### Post by NilsE on 2009-06-13
I suspected flash since it was not browser specific for you and that is the one common thing between browsers.

Flash is active all the time even if there is no flash on the page.  Flash isn't always videos either so any flash content can trigger the problem. 

On the other hand the basic google page does not have flash on  it that I can find unless you use iGoogle which has a lot of flash.

Let us know how it goes.

---

### Post by Mosaab on 2009-06-13
I know .. google.com does nohave flash ... thats what i was saying .. firefox turns off when i try to access google though there is no flash content.

---

### Post by Mosaab on 2009-06-13
it crashed once after i uninstalled that non free flash ... still no luck

---

### Post by asmoore82 on 2009-06-14
run it from a terminal for a while - then when it dies you will see its "last breath."

The one I've seen before in this situation is "System Bus Error" which is most likely
either dust contamination or bad memory modules.

---

### Post by Mosaab on 2009-06-14
actually its funny... I tried to do this ... but when I run it from a terminal it never crashes !!! that what drove me crazy... I have been doing this since yesterday.

---

### Post by NilsE on 2009-06-14
> **Mosaab said:**
> actually its funny... I tried to do this ... but when I run it from a terminal it never crashes !!! that what drove me crazy... I have been doing this since yesterday.
When you run it from a terminal are you running  a root terminal or starting it with root permission?  If so then that is a different profile for the browser.  If that is the case try removing and creating a new profile for your normal startup.

---

### Post by Mosaab on 2009-06-14
No .. I never change the user... I just start the terminal and type firefox

I will try to start it with the terminal for some time .. until it crashes ... I am hoping it will give me some error .. because its good to know the reason :)

---

### Post by Mosaab on 2009-06-14
it crashed .. but not in the same way ... it went gray .... I got this in the terminal :

```

*** glibc detected *** /usr/lib/firefox-3.0.10/firefox: double free or corruption (fasttop): 0x0a765978 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7db4454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7db64b6]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb58b1503]
/lib/libnss_wins.so.2[0xb5ad6289]
/usr/lib/libtalloc.so.1(talloc_free+0x271)[0xb58b1621]
/lib/libnss_wins.so.2(alloc_sub_basic+0xa87)[0xb5b017a8]
/lib/libnss_wins.so.2(talloc_sub_basic+0x33)[0xb5b01d8f]
/lib/libnss_wins.so.2[0xb5a41281]
/lib/libnss_wins.so.2(lp_lockdir+0x27)[0xb5a423f2]
/lib/libnss_wins.so.2(lock_path+0x17)[0xb5afbac5]
/lib/libnss_wins.so.2(receive_unexpected+0x21)[0xb5a9a767]
/lib/libnss_wins.so.2(receive_nmb_packet+0x65)[0xb5a9d375]
/lib/libnss_wins.so.2(name_query+0x32e)[0xb5a9fe4d]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x38a)[0xb5a3d555]
/lib/tls/i686/cmov/libc.so.6(gethostbyname_r+0x1a3)[0xb7e40c93]
/usr/lib/libnspr4.so.0d(PR_GetHostByName+0xb4)[0xb7c7e1e4]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0xb0)[0xb7c7e640]
/usr/lib/xulrunner-1.9.0.10/libxul.so[0xb7259778]
/usr/lib/libnspr4.so.0d[0xb7c8c1e1]
/lib/tls/i686/cmov/libpthread.so.0[0xb7fd150f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7e26a0e]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:07 8238       /usr/lib/firefox-3.0.10/firefox
0804f000-08050000 r--p 00006000 08:07 8238       /usr/lib/firefox-3.0.10/firefox
08050000-08051000 rw-p 00007000 08:07 8238       /usr/lib/firefox-3.0.10/firefox
09083000-0c413000 rw-p 09083000 00:00 0          [heap]
ab67a000-ab67b000 ---p ab67a000 00:00 0 
ab67b000-abe7b000 rwxp ab67b000 00:00 0 
abe7b000-abe7c000 ---p abe7b000 00:00 0 
abe7c000-ac67c000 rwxp abe7c000 00:00 0 
ac67c000-ac67d000 ---p ac67c000 00:00 0 
ac67d000-ace7d000 rwxp ac67d000 00:00 0 
ace7d000-ace7e000 ---p ace7d000 00:00 0 
ace7e000-ad67e000 rwxp ace7e000 00:00 0 
ae6de000-ae73c000 rw-p ae6de000 00:00 0 
ae73c000-ae86f000 r-xp 00000000 08:07 55         /usr/lib/i686/cmov/libcrypto.so.0.9.8
ae86f000-ae877000 r--p 00132000 08:07 55         /usr/lib/i686/cmov/libcrypto.so.0.9.8
ae877000-ae884000 rw-p 0013a000 08:07 55         /usr/lib/i686/cmov/libcrypto.so.0.9.8
ae884000-ae888000 rw-p ae884000 00:00 0 
ae888000-ae8ca000 r-xp 00000000 08:07 56         /usr/lib/i686/cmov/libssl.so.0.9.8
ae8ca000-ae8cb000 r--p 00041000 08:07 56         /usr/lib/i686/cmov/libssl.so.0.9.8
ae8cb000-ae8ce000 rw-p 00042000 08:07 56         /usr/lib/i686/cmov/libssl.so.0.9.8
ae8ce000-ae8fe000 r-xp 00000000 08:07 7376163    /usr/lib/libidn.so.11.5.37
ae8fe000-ae8ff000 r--p 00030000 08:07 7376163    /usr/lib/libidn.so.11.5.37
ae8ff000-ae900000 rw-p 00031000 08:07 7376163    /usr/lib/libidn.so.11.5.37
ae900000-ae9fe000 rw-p ae900000 00:00 0 
ae9fe000-aea00000 ---p ae9fe000 00:00 0 
aea13000-aea4f000 r-xp 00000000 08:07 5505055    /usr/lib/libcurl.so.4.1.0
aea4f000-aea50000 r--p 0003c000 08:07 5505055    /usr/lib/libcurl.so.4.1.0
aea50000-aea51000 rw-p 0003d000 08:07 5505055    /usr/lib/libcurl.so.4.1.0
aea51000-aea9d000 r--p 00000000 08:07 124893     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
aea9d000-aeaa1000 r-xp 00000000 08:07 1049612    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
aeaa1000-aeaa2000 r--p 00003000 08:07 1049612    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
aeaa2000-aeaa3000 rw-p 00004000 08:07 1049612    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
aeaa3000-aeaa4000 ---p aeaa3000 00:00 0 
aeaa4000-af2a4000 rwxp aeaa4000 00:00 0 
af2a4000-af2b3000 r-xp 00000000 08:07 7375570    /usr/lib/libXpm.so.4.11.0
af2b3000-af2b4000 rw-p 0000f000 08:07 7375570    /usr/lib/libXpm.so.4.11.0
af2b4000-af2c9000 r-xp 00000000 08:07 7375564    /usr/lib/libXmu.so.6.2.0
af2c9000-af2ca000 rw-p 00015000 08:07 7375564    /usr/lib/libXmu.so.6.2.0
af2ca000-af320000 r-xp 00000000 08:07 7375540    /usr/lib/libXaw7.so.7.0.0
af320000-af327000 rw-p 00055000 08:07 7375540    /usr/lib/libXaw7.so.7.0.0
af327000-af36d000 r-xp 00000000 08:07 32883      /usr/lib/mozilla/plugins/mplayerplug-in.so
af36d000-af36e000 r--p 00046000 08:07 32883      /usr/lib/mozilla/plugins/mplayerplug-in.so
af36e000-af36f000 rw-p 00047000 08:07 32883      /usr/lib/mozilla/plugins/mplayerplug-in.so
af36f000-af3b5000 r-xp 00000000 08:07 32881      /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af3b5000-af3b6000 r--p 00045000 08:07 32881      /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af3b6000-af3b7000 rw-p 00046000 08:07 32881      /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
af3b7000-af3fd000 r-xp 00000000 08:07 32879      /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af3fd000-af3fe000 r--p 00045000 08:07 32879      /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af3fe000-af3ff000 rw-p 00046000 08:07 32879      /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
af3ff000-af445000 r-xp 00000000 08:07 32877      /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af445000-af446000 r--p 00045000 08:07 32877      /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af446000-af447000 rw-p 00046000 08:07 32877      /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
af447000-af48d000 r-xp 00000000 08:07 32875      /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af48d000-af48e000 r--p 00045000 08:07 32875      /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af48e000-af48f000 rw-p 00046000 08:07 32875      /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
af48f000-af4ae000 rw-p af48f000 00:00 0 
af4ae000-af4e1000 ---p af4ae000 00:00 0 
af4e1000-af5c0000 rw-p af4e1000 00:00 0 
af5c0000-af5fe000 ---p af5c0000 00:00 0 
af5fe000-af61d000 rw-p af5fe000 00:00 0 
af61d000-af623000 ---p af61d000 00:00 0 
af623000-af63e000 rw-p af623000 00:00 0 
af63e000-af68e000 ---p af63e000 00:00 0 
af68e000-af69e000 rw-p af68e000 00:00 0 
af69e000-af6ad000 ---p af69e000 00:00 0 
af6ad000-af6be000 rw-p af6ad000 00:00 0 
af6be000-af6c5000 ---p af6be000 00:00 0 
af6c5000-af6de000 rw-p af6c5000 00:00 0 
af6de000-af6ea000 ---p af6de000 00:00 0 
af6ea000-af6fd000 rw-p af6ea000 00:00 0 
af6fd000-af701000 ---p af6fd000 00:00 0 
af701000-af711000 rw-p af701000 00:00 0 
af711000-af715000 ---p af711000 00:00 0 
af715000-af71f000 rw-p af715000 00:00 0 
af71f000-af727000 ---p af71f000 00:00 0 
af727000-b048f000 rw-p af727000 00:00 0 
b04a5000-b0e12000 r-xp 00000000 08:07 148681     /usr/lib/adobe-flashplugin/libflashplayer.so
b0e12000-b0e45000 rw-p 0096c000 08:07 148681     /usr/lib/adobe-flashplugin/libflashplayer.so
b0e45000-b0f30000 rw-p b0e45000 00:00 0 
b0f30000-b0f5d000 r-xp 00000000 08:07 49787      /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386/libjavaplugin_nscp.so
b0f5d000-b0f63000 rw-p 0002d000 08:07 49787      /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/i386/libjavaplugin_nscp.so
b0f63000-b0f79000 r-xp 00000000 08:07 49890      /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0f79000-b0f7d000 rw-p 00015000 08:07 49890      /usr/lib/jvm/java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0f7d000-b0f7e000 r-xp 00000000 08:07 83023      /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
b0f7e000-b0f7f000 r--p 00000000 08:07 83023      /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
b0f7f000-b0f80000 rw-p 00001000 08:07 83023      /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
b0f9f000-b0ffd000 rw-p b0f9f000 00:00 0 
b0ffd000-b0ffe000 ---p b0ffd000 00:00 0 
b0ffe000-b17fe000 rwxp b0ffe000 00:00 0 
b201e000-b203d000 r--p 00000000 08:07 5677157    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b203d000-b2083000 r--p 00000000 08:07 5677173    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b20a5000-b20cb000 r--p 00000000 08:07 5677189    /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
b210f000-b2132000 r--p 00000000 08:07 5677191    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b2132000-b2133000 ---p b2132000 00:00 0 
b2133000-b2933000 rwxp b2133000 00:00 0 
b2933000-b2978000 r-xp 00000000 08:07 7389671    /usr/lib/nss/libnssckbi.so
b2978000-b297f000 r--p 00045000 08:07 7389671    /usr/lib/nss/libnssckbi.so
b297f000-b2983000 rw-p 0004c000 08:07 7389671    /usr/lib/nss/libnssckbi.so
b2983000-b29c7000 r-xp 00000000 08:07 7389668    /usr/lib/nss/libfreebl3.so
b29c7000-b29c8000 r--p 00043000 08:07 7389668    /usr/lib/nss/libfreebl3.so
b29c8000-b29c9000 rw-p 00044000 08:07 7389668    /usr/lib/nss/libfreebl3.so
b29c9000-b29fd000 r-xp 00000000 08:07 7389669    /usr/lib/nss/libsoftokn3.so
b29fd000-b29fe000 r--p 00034000 08:07 7389669    /usr/lib/nss/libsoftokn3.so
b29fe000-b29ff000 rw-p 00035000 08:07 7389669    /usr/lib/nss/libsoftokn3.so
b29ff000-b2a00000 ---p b29ff000 00:00 0 
b2a00000-b3200000 rwxp b2a00000 00:00 0 
b3200000-b3300000 rw-p b3200000 00:00 0 
b3302000-b3324000 r-xp 00000000 08:07 7389670    /usr/lib/nss/libnssdbm3.so
b3324000-b3325000 r--p 00022000 08:07 7389670    /usr/lib/nss/libnssdbm3.so
b3325000-b3326000 rw-p 00023000 08:07 7389670    /usr/lib/nss/libnssdbm3.so
b3540000-b354f000 r-xp 00000000 08:07 1032230    /lib/libbz2.so.1.0.4
b354f000-b3550000 r--p 0000f000 08:07 1032230    /lib/libbz2.so.1.0.4
b3550000-b3551000 rw-p 00010000 08:07 1032230    /lib/libbz2.so.1.0.4
b3551000-b3582000 r-xp 00000000 08:07 7375716    /usr/lib/libcroco-0.6.so.3.0.1
b3582000-b3585000 rw-p 00030000 08:07 7375716    /usr/lib/libcroco-0.6.so.3.0.1
b3585000-b35b5000 r-xp 00000000 08:07 7376032    /usr/lib/libgsf-1.so.114.0.8
b35b50


```

---

### Post by asmoore82 on 2009-06-15
I would run the memory test from the GRUB menu.

---

### Post by Mosaab on 2009-06-15
this is what I get from the terminal when the browser crashes:
```
Aborted
```

Thats all !!!

---

### Post by Mosaab on 2009-06-15
I created a new user profile .. and tried it ... the same thing happened, the firefox window just disappears ..

I ran a memory test ... and there were no errors ... 

help me please before i install a fresh ubuntu

---


---
title: "Firefox crashes when closing gmail tab"
date: 2008-06-08
forum: Desktop Environments
---

### Post by davosmith on 2008-06-08
Ubuntu Hardy
Using Firefox 3 beta 5

If I have multiple tabs open, including gmail then firefox instantly crashes with a segmentation fault if I middle-click on the gmail tab (to close it).

Any ideas?

---

### Post by pdah on 2008-06-08
What firefox extensions had you install ? 
Try to disable all and check if you still have problem.

---

### Post by davosmith on 2008-06-08
Thanks for the reply. I've disabled all extensions and still getting the crashes.

It *was* working fine, but I notice that gmail has been messing around with their javascript recently and appear to have changed something.

Any other ideas?

---

### Post by jessald on 2008-06-18
Same problem.  Is annoying.
Edit: Oh, and I'm not using the beta.  I'm using the released 3.0 version.

---

### Post by medigerati on 2008-06-20
i can confirm this issue. I have FF3, ubuntu 8.04 on a 64 bit system. Happens when I close gmail and sometimes google reader.

---

### Post by t_ras on 2008-06-20
Same here but with many sites, specialy flash related I think.
AMD64,Kubuntu 8.04, KDE 3.5.9, firefox 3 beta 5

---

### Post by t_ras on 2008-06-21
OK I got a hint to install libflashsupport, I hope it will help.

---

### Post by starscalling on 2008-06-21
run it in a terminal and paste the spam

---

### Post by rudihawk on 2008-06-21
I had the same problems with FF3b5.

---

### Post by jessald on 2008-06-21
I ran it in a terminal but all I got was "Segmentation Fault" when it crashed.

---

### Post by the_spaz on 2008-06-22
here is terminal output from running Fx and closing a gmail tab (crash!).  It should be noted that I can navigate away from gmail, but not close its tab.

```

spaz@minas:~$ firefox
*** glibc detected *** /usr/lib/firefox-3.0/firefox: double free or corruption (!prev): 0xae4a5a40 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cc8a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7ccc4f0]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7e93b11]
/usr/lib/xulrunner-1.9/libxul.so[0xb77e0744]
/usr/lib/xulrunner-1.9/libxul.so[0xb77dff35]
/usr/lib/xulrunner-1.9/libxul.so[0xb77e0495]
/usr/lib/xulrunner-1.9/libxul.so[0xb77e6f65]
/usr/lib/xulrunner-1.9/libxul.so[0xb77e3b82]
/usr/lib/xulrunner-1.9/libxul.so[0xb78729ab]
/usr/lib/xulrunner-1.9/libxul.so[0xb7872f63]
/usr/lib/xulrunner-1.9/libxul.so[0xb7870496]
/usr/lib/xulrunner-1.9/libxul.so[0xb783fa83]
/usr/lib/xulrunner-1.9/libxul.so[0xb77c0efe]
/usr/lib/xulrunner-1.9/libxul.so[0xb7650946]
/usr/lib/xulrunner-1.9/libxul.so(XRE_main+0x2036)[0xb70a5688]
/usr/lib/firefox-3.0/firefox[0x8049033]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c73450]
/usr/lib/firefox-3.0/firefox[0x8048cc1]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:05 2744800    /usr/lib/firefox-3.0/firefox
0804f000-08050000 rw-p 00006000 08:05 2744800    /usr/lib/firefox-3.0/firefox
08050000-09fb1000 rw-p 08050000 00:00 0          [heap]
ad400000-ad453000 rw-p ad400000 00:00 0 
ad453000-ad500000 ---p ad453000 00:00 0 
ad50e000-ad50f000 ---p ad50e000 00:00 0 
ad50f000-add0f000 rwxp ad50f000 00:00 0 
add0f000-adffe000 rw-p add0f000 00:00 0 
adffe000-ae000000 ---p adffe000 00:00 0 
ae06f000-ae200000 rw-p ae06f000 00:00 0 
ae206000-ae285000 rw-p ae206000 00:00 0 
ae285000-ae300000 r--p 00000000 08:05 2555927    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-BoldOblique.ttf
ae300000-ae4fd000 rw-p ae300000 00:00 0 
ae4fd000-ae500000 ---p ae4fd000 00:00 0 
ae500000-ae700000 rw-p ae500000 00:00 0 
ae700000-ae800000 rw-p ae700000 00:00 0 
ae84e000-ae8cf000 rw-p ae84e000 00:00 0 
ae8cf000-aea62000 r-xp 00000000 08:05 2413249    /usr/lib/libvlc.so.0.0.0
aea62000-aea69000 rw-p 00192000 08:05 2413249    /usr/lib/libvlc.so.0.0.0
aea69000-aeb6d000 rw-p aea69000 00:00 0 
aeb6d000-afa6d000 ---p aeb6d000 00:00 0 
afa6d000-b01e5000 r-xp 00000000 08:05 2695473    /usr/lib/flashplugin-nonfree/libflashplayer.so
b01e5000-b0229000 rw-p 00777000 08:05 2695473    /usr/lib/flashplugin-nonfree/libflashplayer.so
b0229000-b03ef000 rw-p b0229000 00:00 0 
b03ef000-b0400000 ---p b03ef000 00:00 0 
b0470000-b049d000 r-xp 00000000 08:05 2917245    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp.so
b049d000-b04a3000 rw-p 0002d000 08:05 2917245    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_nscp.so
b0500000-b05fb000 rw-p b0500000 00:00 0 
b05fb000-b0600000 ---p b05fb000 00:00 0 
b060b000-b0631000 r--p 00000000 08:05 1278064    /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
b0631000-b0677000 r--p 00000000 08:05 1278048    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b0677000-b06bb000 r--p 00000000 08:05 1278050    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b06bb000-b06dd000 r--p 00000000 08:05 1278034    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
b06dd000-b0700000 r--p 00000000 08:05 1278066    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b0700000-b07f5000 rw-p b0700000 00:00 0 
b07f5000-b0800000 ---p b07f5000 00:00 0 
b0800000-b0900000 rw-p b0800000 00:00 0 
b0900000-b09fb000 rw-p b0900000 00:00 0 
b09fb000-b0a00000 ---p b09fb000 00:00 0 
b0a03000-b0a19000 r-xp 00000000 08:05 2924548    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0a19000-b0a1d000 rw-p 00015000 08:05 2924548    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0a1d000-b0a64000 r-xp 00000000 08:05 2410843    /usr/lib/libtheora.so.0.3.2
b0a64000-b0a66000 rw-p 00046000 08:05 2410843    /usr/lib/libtheora.so.0.3.2
b0a66000-b0a70000 r-xp 00000000 08:05 2411326    /usr/lib/libdvbpsi.so.4.0.0
b0a70000-b0a71000 rw-p 00009000 08:05 2411326    /usr/lib/libdvbpsi.so.4.0.0
b0a71000-b0a80000 r-xp 00000000 08:05 2410287    /usr/lib/libhal.so.1.0.0
b0a80000-b0a81000 rw-p 0000e000 08:05 2410287    /usr/lib/libhal.so.1.0.0
b0a8e000-b0aa6000 r-xp 00000000 08:05 2449939    /usr/lib/mozilla/plugins/libvlcplugin.so
b0aa6000-b0aa8000 rw-p 00017000 08:05 2449939    /usr/lib/mozilla/plugins/libvlcplugin.so
b0aa8000-b0aac000 r-xp 00000000 08:05 2506829    /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b0aac000-b0aad000 rw-p 00003000 08:05 2506829    /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b0acf000-b0aee000 r--p 00000000 08:05 1278032    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b0aee000-b0af2000 r-xp 00000000 08:05 550217     /lib/tls/i686/cmov/libnss_dns-2.7.so
b0af2000-b0af4000 rw-p 00003000 08:05 550217     /lib/tls/i686/cmov/libnss_dns-2.7.so
b0af9000-b0afd000 r-xp 00000000 08:05 2410674    /usr/lib/libogg.so.0.5.3
b0afd000-b0afe000 rw-p 00003000 08:05 2410674    /usr/lib/libogg.so.0.5.3
b0afe000-b0b00000 r-xp 00000000 08:05 2506828    /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
b0b00000-b0b01000 rw-p 00001000 08:05 2506828    /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
b0b01000-b0b08000 r-xp 00000000 08:05 2744330    /usr/lib/xulrunner-1.9/components/libmozgnome.so
b0b08000-b0b09000 rw-p 00007000 08:05 2744330    /usr/lib/xulrunner-1.9/components/libmozgnome.so
b0b09000-b0b0a000 ---p b0b09000 00:00 0 
b0b0a000-b130a000 rwxp b0b0a000 00:00 0 
b130a000-b130b000 ---p b130a000 00:00 0 
b130b000-b1b0b000 rwxp b130b000 00:00 0 
b1b0b000-b1b0c000 ---p b1b0b000 00:00 0 
b1b0c000-b230c000 rwxp b1b0c000 00:00 0 
b230c000-b234f000 r-xp 00000000 08:05 2410825    /usr/lib/libspi.so.0.10.11
b234f000-b2359000 rw-p 00043000 08:05 2410825    /usr/lib/libspi.so.0.10.11
b2359000-b245d000 rw-p b2359000 00:00 0 
b245d000-b24ee000 r--p 00000000 08:05 2557464    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b24ee000-b25f2000 rw-p b24ee000 00:00 0 
b25f2000-b2679000 r--p 00000000 08:05 2557463    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b2679000-b26ab000 r-xp 00000000 08:05 2410204    /usr/lib/libcroco-0.6.so.3.0.1
b26ab000-b26ae000 rw-p 00031000 08:05 2410204    /usr/lib/libcroco-0.6.so.3.0.1
b26ae000-b26de000 r-xp 00000000 08:05 2410458    /usr/lib/libgsf-1.so.114.0.7
b26de000-b26e1000 rw-p 0002f000 08:05 2410458    /usr/lib/libgsf-1.so.114.0.7
b26e1000-b26e2000 rw-p b26e1000 00:00 0 
b26e2000-b2712000 r-xp 00000000 08:05 2410781    /usr/lib/librsvg-2.so.2.22.2
b2712000-b2713000 rw-p 00030000 08:05 2410781    /usr/lib/librsvg-2.so.2.22.2
b2713000-b27be000 r--p 00000000 08:05 2648423    /usr/share/icons/Tangerine/icon-theme.cache
b27be000-b27ff000 rw-p b27be000 00:00 0 
b27ff000-b2800000 ---p b27ff000 00:00 0 
b2800000-b3000000 rwxp b2800000 00:00 0 
b3000000-b3100000 rw-p b3000000 00:00 0 
b3100000-b3101000 r-xp 00000000 08:05 2506947    /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
b3101000-b3102000 rw-p 00000000 08:05 2506947    /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
b3102000-b3104000 r-xp 00000000 08:05 532575     /lib/libnss_mdns4_minimal.so.2
b3104000-b3105000 rw-p 00001000 08:05 532575     /lib/libnss_mdns4_minimal.so.2
b3105000-b310d000 r-xp 00000000 08:05 2744994    /usr/lib/xulrunner-1.9/components/libnkgnomevfs.so
b310d000-b310e000 rw-p 00007000 08:05 2744994    /usr/lib/xulrunner-1.9/components/libnkgnomevfs.so
b310e000-b311d000 r-xp 00000000 08:05 532518     /lib/libbz2.so.1.0.4
b311d000-b311e000 rw-p 0000f000 08:05 532518     /lib/libbz2.so.1.0.4
b311f000-b3123000 r-xp 00000000 08:05 2410100    /usr/lib/libXtst.so.6.1.0
b3123000-b3124000 rw-p 00003000 08:05 2410100    /usr/lib/libXtst.so.6.1.0
b3124000-b312a000 r-xp 00000000 08:05 2434600    /usr/lib/gtk-2.0/modules/libatk-bridge.so
b312a000-b312b000 rw-p 00005000 08:05 2434600    /usr/lib/gtk-2.0/modules/libatk-bridge.so
b312b000-b312c000 r-xp 00000000 08:05 2434595    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b312c000-b312d000 rw-p 00000000 08:05 2434595    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b312d000-b316e000 rw-p b312d000 00:00 0 
b316e000-b31b9000 r--p 00000000 08:05 2557468    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b31b9000-b31de000 r-xp 00000000 08:05 2744797    /usr/lib/firefox-3.0/components/libbrowsercomps.so
b31de000-b31e0000 rw-p 00025000 08:05 2744797    /usr/lib/firefox-3.0/components/libbrowsercomps.so
b31e0000-b3224000 r-xp 00000000 08:05 2413052    /usr/lib/nss/libnssckbi.so
b3224000-b322f000 rw-p 00044000 08:05 2413052    /usr/lib/nss/libnssckbi.so
b322f000-b3269000 r-xp 00000000 08:05 2408853    /usr/lib/nss/libfreebl3.so
b3269000-b326a000 rw-p 0003a000 08:05 2408853    /usr/lib/nss/libfreebl3.so
b326a000-b328a000 r-xp 00000000 08:05 2413051    /usr/lib/nss/libnssdbm3.so
b328a000-b328b000 rw-p 0001f000 08:05 2413051    /usr/lib/nss/libnssdbm3.so
b328b000-b32ee000 r-xp 00000000 08:05 2410829    /usr/lib/libsqlite3.so.0.8.6
b32ee000-b32f0000 rw-p 00062000 08:05 2410829    /usr/lib/libsqlite3.so.0.8.6
b32f0000-b3320000 r-xp 00000000 08:05 2409689    /usr/lib/nss/libsoftokn3.so
b3320000-b3321000 rw-p 00030000 08:05 2409689    /usr/lib/nss/libsoftAborted

```

---

### Post by the_spaz on 2008-06-22
this bug has been reported @ launchpad [[#240786]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/240786")]

---

### Post by Achirio on 2008-06-24
This issue is not only with firefox 3. I have the same issue with firefox 2, on both Ubuntu (on two separate machines) AND Windows xp professional.

---

### Post by andrewski on 2008-06-28
> **the_spaz said:**
> this bug has been reported @ launchpad [[#240786]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/240786")]
Original bug is [209372]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/209372"). What an annoying bug, eh? :shock:

---

### Post by tornado89 on 2008-06-28
I'm Having This Issue Too...
It's So Annoying..... Ubuntu Hardy With FF3 B5

---

### Post by andrewski on 2008-06-29
> **tornado89 said:**
> I'm Having This Issue Too...
It's So Annoying..... Ubuntu Hardy With FF3 B5
It would be a good idea to enable your hardy-updates repository, which now has Firefox 3.0 (i.e. the final release, not the betas or RCs). Not that it would necessarily help with this problem, but it has some other fixes.

Note, however, that hardy-updates has a lot of updates. Generally, I'd say this is a good thing, just something to keep in mind in case you want/need to have Hardy itself.

---

### Post by Primefalcon on 2008-06-29
I'm getting the same problem myself, really annoying

---

### Post by GeigerRulesBig on 2008-06-30
I have not checked the terminal output, but I get the same error when using FF3, Opera, and even Kazehakase (and I thought nothing could phase that browser.) It is an extremely irritating bug for someone who uses Google so much. I think I have also gotten the same crash closing other tabs, but only when Gmail is open.


-Geiger

---

### Post by indyhill on 2008-07-16
This seems to be fixed as of Firefox 3.0.1. Not listed in the release notes, but it's not crashing when I close the tab now. Yippee, it was driving me nuts.

---

### Post by esemns on 2008-07-23
Same problem here, hope for a fix for it...

---

### Post by andrewski on 2008-07-23
> **esemns said:**
> Same problem here, hope for a fix for it...
> **indyhill said:**
> This seems to be fixed as of Firefox 3.0.1. Not listed in the release notes, but it's not crashing when I close the tab now. Yippee, it was driving me nuts.

Should be fixed now. It's available in the hardy-proposed repository, which isn't enabled by default. General info here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). Post back if you have any questions (especially as that how-to is a bit outdated).

---

### Post by medigerati on 2008-07-24
Downloaded FF3.1 from the proposed repositories. I can now freely close the gmail tab with no fear of closing firefox. Awesome!

---


---
title: "[SOLVED] Nautilus Crashes on startup"
date: 2008-11-05
forum: Desktop Environments
---

### Post by kamasheto on 2008-11-05
Hey

I just upgraded ubuntu from 8.04 to 8.10 and nautilus seems to not work anymore.

At startup, I could see desktop icons (including folders, and shortcuts to windows partitions). When I click on a folder (local: /home/kamasheto/Desktop/myFolder/) the file browser triggers and I see the contents for a second and it disappears again very quickly -- all in less than a second. :\

When I click on a shortcut to any of my windows partitions the file browser triggers and works flawlessly, until I decide to act clever and browse into a local file, then nautilus simply shuts down, again.

When I run:

$ nautilus ./ 

my desktop icons disappear. When I then run:

$ nautilus ./ 

(for the second time), my desktop icons remain hidden and get this message on my terminal:

```
seahorse nautilus module initialized     
Initializing nautilus-share extension    

** (nautilus:13120): WARNING **: Unable to add monitor: Not supported
*** glibc detected *** nautilus: malloc(): memory corruption (fast): 0x0874e910 ***
======= Backtrace: =========                                                       
/lib/tls/i686/cmov/libc.so.6[0xb72133f4]                                           
/lib/tls/i686/cmov/libc.so.6[0xb7216456]                                           
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7217865]                       
/usr/lib/libglib-2.0.so.0(g_malloc+0x34)[0xb756ad64]                               
/usr/lib/libglib-2.0.so.0(g_strdup+0x39)[0xb75838d9]                               
/usr/lib/libgio-2.0.so.0(g_content_type_guess+0x157)[0xb7639ca7]                   
/usr/lib/libgio-2.0.so.0[0xb76704de]                                               
/usr/lib/libgio-2.0.so.0[0xb767195f]                                               
/usr/lib/libgio-2.0.so.0[0xb766e48d]                                               
/usr/lib/libgio-2.0.so.0[0xb7649c62]                                               
/usr/lib/libgio-2.0.so.0[0xb765bdb9]                                               
/usr/lib/libgio-2.0.so.0[0xb7655384]                                               
/usr/lib/libglib-2.0.so.0[0xb758e6c6]                                              
/usr/lib/libglib-2.0.so.0[0xb758d02f]                                              
/lib/tls/i686/cmov/libpthread.so.0[0xb730850f]                                     
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb72857ee]                               
======= Memory map: ========                                                       
08048000-08188000 r-xp 00000000 08:07 324181     /usr/bin/nautilus                 
08188000-0818a000 r--p 0013f000 08:07 324181     /usr/bin/nautilus                 
0818a000-0818d000 rw-p 00141000 08:07 324181     /usr/bin/nautilus                 
0818d000-0876b000 rw-p 0818d000 00:00 0          [heap]                            
b3998000-b3a9c000 rw-p b3998000 00:00 0                                            
b3a9c000-b3b25000 r--p 00000000 08:07 469875     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3b25000-b3b48000 r--p 00000000 08:07 469941     /usr/share/fonts/truetype/freefont/FreeMonoBold.ttf     
b3b48000-b40c7000 rw-p b3b48000 00:00 0                                                                  
b40c7000-b40e6000 r-xp 00000000 08:07 326206     /usr/lib/libjpeg.so.62.0.0                              
b40e6000-b40e7000 rw-p 0001e000 08:07 326206     /usr/lib/libjpeg.so.62.0.0                              
b40fd000-b40fe000 ---p b40fd000 00:00 0
b40fe000-b494d000 rw-p b40fe000 00:00 0
b494d000-b4951000 r-xp 00000000 08:07 387904     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4951000-b4952000 r--p 00003000 08:07 387904     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4952000-b4953000 rw-p 00004000 08:07 387904     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4954000-b4a58000 rw-p b4954000 00:00 0
b4a58000-b4aed000 r--p 00000000 08:07 469874     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4aed000-b4aef000 r-xp 00000000 08:07 371817     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4aef000-b4af0000 r--p 00001000 08:07 371817     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4af0000-b4af1000 rw-p 00002000 08:07 371817     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4af1000-b4af7000 r--s 00000000 08:07 632482     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4af7000-b4afa000 r--s 00000000 08:07 632480     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b4afa000-b4afb000 r--s 00000000 08:07 632479     /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b4afb000-b4aff000 r--s 00000000 08:07 632484     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4aff000-b4b01000 r--s 00000000 08:07 632477     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b4b01000-b4b04000 r--s 00000000 08:07 632476     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b4b04000-b4b05000 r--s 00000000 08:07 632475     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4b05000-b4b08000 r--s 00000000 08:07 632474     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b4b08000-b4b0f000 r--s 00000000 08:07 632473     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4b0f000-b4b12000 r--s 00000000 08:07 632472     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4b12000-b4b1a000 r--s 00000000 08:07 632471     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4b1a000-b4b25000 r--s 00000000 08:07 631910     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4b25000-b4b26000 r--s 00000000 08:07 632469     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4b26000-b4b29000 r--s 00000000 08:07 632486     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4b29000-b4b30000 r--s 00000000 08:07 6319Aborted

```

However, when I run:

$ nautilus

my desktop icons show up again, and I get this message on my terminal:

```
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:13023): WARNING **: Unable to add monitor: Not supported
```

Any help would be greatly appreciated. Thanks!

---

### Post by kamasheto on 2008-11-05
I think it's worth mentioning that when I run:

$ sudo nautilus

nautilus does start up normally and I can browse the entire filesystem just fine until, yet again, I reach my own /home/kamasheto/ directory! :\ (That is very weird!)

---

### Post by jwdresser on 2008-11-05
Im having the exact same problem. Like kamasheto if I run nautilus as root I can browse the filesystem until I navigate to my home folder. Is there a solution?

---

### Post by jwdresser on 2008-11-05
It turns out that I had a file in my home folder that wasn't sitting right with nautilus for some reason. Luckily it was named "??", as soon as I removed it nautilus worked fine.

---

### Post by kamasheto on 2008-11-06
Thanks! Strangely enough, that did solve the problem! I too had a ? file in my home directory that once removed fixed everything.

That is weird.

Thanks again!

---

### Post by Arkenklo on 2009-03-11
I had the exact problem, and the cause was a file created by TrueCrypt named .hidden. On removal, all was back to normal.

---


---
title: "How to run kde applications under gnome"
date: 2009-07-09
forum: Desktop Environments
---

### Post by Pablo W on 2009-07-09
Hi there!

Background: I found what seems to be a nice application to handle recipes (krecipes), so I installed it from synaptic but I cannot see it anywhere.
After searching the web for answers, I've found that krecipes is a kde application.

Question: Can I run a kde application (krecipes) under gnome? How?

Thank you.

---

### Post by csabo2 on 2009-07-09
I've had some luck just using apt to install the KDE app, and it will grab the required files, IE KDE. I do recall it being a little buggy though, GUI wise.

---

### Post by cariboo on 2009-07-09
The menu structure in KDE is different from gnome, so the program may not have been put in the right place. Press Alt-F2 and type:

```
krecipes
```

The program should work as expected. You can add it to Applications-->Accessories, by right-clicking Applications and adding it to the menu.

---

### Post by Pablo W on 2009-07-09
> **cariboo907 said:**
> The menu structure in KDE is different from gnome, so the program may not have been put in the right place. Press Alt-F2 and type:

```
krecipes
```

The program should work as expected. You can add it to Applications-->Accessories, by right-clicking Applications and adding it to the menu.

Thank you for your answers. I'm afraid I cannot make it work yet.

Here's what I did: Since nothing happenned after pressing Alt-F2, I went to Applications-->Accessories, opened the terminal and typed krecipes there. Krecipes started, asked me some basic questions and then it shutted itself down.
I was not able to add it to Applications-->Accessories as suggested by cariboo907, since I cannot see it.
Now, when I go back to the terminal and type krecipes, the application does not start and the terminal shows the following:

> pablo@hem:~$ krecipes
kbuildsycoca running...
*** glibc detected *** krecipes: free(): invalid pointer: 0x09139cf0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb63a0604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb63a25b6]
krecipes[0x80dcc14]
krecipes[0x80da43c]
/usr/lib/libqt-mt.so.3(_ZN9QSqlQuery4execERK7QString+0x265)[0xb6db6245]
/usr/lib/libqt-mt.so.3(_ZN9QSqlQuery4initERK7QStringP12QSqlDatabase+0x9a)[0xb6db5b9a]
/usr/lib/libqt-mt.so.3(_ZN9QSqlQueryC1ERK7QStringP12QSqlDatabase+0x36)[0xb6db5ca6]
krecipes[0x80e8748]
krecipes[0x810d4ee]
krecipes[0x8086dbf]
krecipes[0x80872d1]
krecipes[0x80801ea]
krecipes(_ZN9KHTMLPart5beginERK4KURLii+0x483)[0x807ea0f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6347775]
krecipes(_ZN9KHTMLPart5beginERK4KURLii+0x45)[0x807e5d1]
======= Memory map: ========
08048000-08282000 r-xp 00000000 08:01 4603960    /usr/bin/krecipes
08282000-0829b000 r--p 0023a000 08:01 4603960    /usr/bin/krecipes
0829b000-082a0000 rw-p 00253000 08:01 4603960    /usr/bin/krecipes
082a0000-082a2000 rw-p 082a0000 00:00 0 
09086000-0914a000 rw-p 09086000 00:00 0          [heap]
b5600000-b5621000 rw-p b5600000 00:00 0 
b5621000-b5700000 ---p b5621000 00:00 0 
b5708000-b5709000 ---p b5708000 00:00 0 
b5709000-b5f09000 rw-p b5709000 00:00 0 
b5f09000-b5f39000 r-xp 00000000 08:01 4604076    /usr/lib/liblcms.so.1.0.18
b5f39000-b5f3a000 r--p 00030000 08:01 4604076    /usr/lib/liblcms.so.1.0.18
b5f3a000-b5f3b000 rw-p 00031000 08:01 4604076    /usr/lib/liblcms.so.1.0.18
b5f3b000-b5f3d000 rw-p b5f3b000 00:00 0 
b5f3d000-b5fa8000 r-xp 00000000 08:01 4606122    /usr/lib/libmng.so.1.1.0.9
b5fa8000-b5fab000 rw-p 0006a000 08:01 4606122    /usr/lib/libmng.so.1.1.0.9
b5fbd000-b5fc1000 r-xp 00000000 08:01 149610     /usr/lib/qt3/plugins/imageformats/libqmng.so
b5fc1000-b5fc2000 rw-p 00003000 08:01 149610     /usr/lib/qt3/plugins/imageformats/libqmng.so
b5fc2000-b5fe0000 r-xp 00000000 08:01 688488     /usr/lib/kde3/plugins/styles/plastik.so
b5fe0000-b5fe1000 r--p 0001d000 08:01 688488     /usr/lib/kde3/plugins/styles/plastik.so
b5fe1000-b5fe2000 rw-p 0001e000 08:01 688488     /usr/lib/kde3/plugins/styles/plastik.so
b5fe2000-b5ff0000 r--p 00000000 08:01 41724      /usr/share/locale/es/LC_MESSAGES/krecipes.mo
b5ff0000-b6021000 r--p 00000000 08:01 319637     /usr/share/locale-langpack/es/LC_MESSAGES/kdelibs.mo
b6021000-b6027000 r--s 00000000 08:01 4317885    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6027000-b602a000 r--s 00000000 08:01 4317854    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b602a000-b602e000 r--s 00000000 08:01 4328124    /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b602e000-b6031000 r--s 00000000 08:01 4318080    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b6031000-b6032000 r--s 00000000 08:01 4317900    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6032000-b6035000 r--s 00000000 08:01 4317849    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6035000-b603c000 r--s 00000000 08:01 4317846    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b603c000-b603f000 r--s 00000000 08:01 4317848    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b603f000-b6047000 r--s 00000000 08:01 4317864    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6047000-b6052000 r--s 00000000 08:01 4317903    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6052000-b6054000 r--s 00000000 08:01 4318039    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b6054000-b6055000 r--s 00000000 08:01 4317856    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6055000-b6077000 r--s 00000000 08:01 4317855    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6077000-b607a000 r--s 00000000 08:01 4318081    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b607a000-b6081000 r--s 00000000 08:01 4317852    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6081000-b6087000 r--s 00000000 08:01 4318070    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6087000-b6094000 r--s 00000000 08:01 4317948    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6094000-b6096000 r--s 00000000 08:01 4317845    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b6096000-b60a4000 r--s 00000000 08:01 4318212    /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b60a4000-b60e3000 r--p 00000000 08:01 2031706    /usr/lib/locale/es_AR.utf8/LC_CTYPE
b60e3000-b60e4000 r--p 00000000 08:01 4637423    /usr/lib/locale/es_AR.utf8/LC_NUMERIC
b60e4000-b60e5000 r--p 00000000 08:01 4637466    /usr/lib/locale/es_AR.utf8/LC_TIME
b60e5000-b61d0000 r--p 00000000 08:01 4637468    /usr/lib/locale/es_AR.utf8/LC_COLLATE
b61d0000-b62d9000 r--p 00000000 08:01 1982468    /usr/lib/locale/locale-archive
b62d9000-b62dc000 rw-p b62d9000 00:00 0 
b62dc000-b62e0000 r-xp 00000000 08:01 4605506    /usr/lib/libXdmcp.so.6.0.0
b62e0000-b62e1000 rw-p 00003000 08:01 4605506    /usr/lib/libXdmcp.so.6.0.0
b62e1000-b62f9000 r-xp 00000000 08:01 4605494    /usr/lib/libxcb.so.1.1.0
b62f9000-b62fa000 r--p 00017000 08:01 4605494    /usr/lib/libxcb.so.1.1.0
b62fa000-b62fb000 rw-p 00018000 08:01 4605494    /usr/lib/libxcb.so.1.1.0
b62fb000-b62fe000 r-xp 00000000 08:01 213036     /lib/libuuid.so.1.2
b62fe000-b62ff000 r--p 00002000 08:01 213036     /lib/libuuid.so.1.2
b62ff000-b6300000 rw-p 00003000 08:01 213036     /lib/libuuid.so.1.2
b6300000-b6302000 r-xp 00000000 08:01 4605837    /usr/lib/libXau.so.6.0.0
b6302000-b6303000 r--p 00001000 08:01 4605837    /usr/lib/libXau.so.6.0.0
b6303000-b6304000 rw-p 00002000 08:01 4605837    /usr/lib/libXau.so.6.0.0
b6304000-b6305000 rw-p b6304000 00:00 0 
b6305000-b6329000 r-xp 00000000 08:01 4605748    /usr/lib/libexpat.so.1.5.2
b6329000-b632b000 r--p 00023000 08:01 4605748    /usr/lib/libexpat.so.1.5.2
b632b000-b632c000 rw-p 00025000 08:01 4605748    /usr/lib/libexpat.so.1.5.2
b632c000-b6330000 r-xp 00000000 08:01 4605512    /usr/lib/libXfixes.so.3.1.0
b6330000-b6331000 rw-p 00003000 08:01 4605512    /usr/lib/libXfixes.so.3.1.0
b6331000-b648d000 r-xp 00000000 08:01 229521     /lib/tls/i686/cmov/libc-2.9.so
b648d000-b648e000 ---p 0015c000 08:01 229521     /lib/tls/i686/cmov/libc-2.9.so
b648e000-b6490000 r--p 0015c000 08:01 229521     /lib/tls/i686/cmov/libc-2.9.so
b6490000-b6491000 rw-p 0015e000 08:01 229521     /lib/tls/i686/cmov/libc-2.9.so
b6491000-b6495000 rw-p b6491000 00:00 0 
b6495000-b64a2000 r-xp 00000000 08:01 2134497    /lib/libgcc_s.so.1
b64a2000-b64a3000 r--p 0000c000 08:01 2134497    /lib/libgcc_s.so.1
b64a3000-b64a4000 rw-p 0000d000 08:01 2134497    /lib/libgcc_s.so.1
b64a4000-b64c8000 r-xp 00000000 08:01 229883     /lib/tls/i686/cmov/libm-2.9.so
b64c8000-b64c9000 r--p 00023000 08:01 229883     /lib/tls/i686/cmov/libm-2.9.so
b64c9000-b64ca000 rw-p 00024000 08:01 229883     /lib/tls/i686/cmov/libm-2.9.so
b64ca000-b65ae000 r-xp 00000000 08:01 4604271    /usr/lib/libstdc++.so.6.0.10
b65ae000-b65b2000 r--p 000e3000 08:01 4604271    /usr/lib/libstdc++.so.6.0.10
b65b2000-b65b3000 rw-p 000e7000 08:01 4604271    /usr/lib/libstdc++.so.6.0.10
b65b3000-b65b9000 rw-p b65b3000 00:00 0 
b65b9000-b65ba000 r-xp 00000000 08:01 4605728    /usr/lib/libkspell.so.4.2.0
b65ba000-b65bb000 r--p 00000000 08:01 4605728    /usr/lib/libkspell.so.4.2.0
b65bb000-b65bc000 rw-p 00001000 08:01 4605728    /usr/lib/libkspell.so.4.2.0
b65bc000-b66a6000 r-xp 00000000 08:01 4606388    /usr/lib/libX11.so.6.2.0
b66a6000-b66a7000 ---p 000ea000 08:01 4606388    /usr/lib/libX11.so.6.2.0
b66a7000-b66a8000 r--p 000ea000 08:01 4606388    /usr/lib/libX11.so.6.2.0
b66a8000-b66aa000 rw-p 000eb000 08:01 4606388    /usr/lib/libX11.so.6.2.0
b66aa000-b66ab000 rw-p b66aa000 00:00 0 
b66ab000-b66ca000 r-xp 00000000 08:01 4606073    /usr/lib/libjpeg.so.62.0.0
b66ca000-b66cb000 rw-p 0001e000 08:01 4606073    /usr/lib/libjpeg.so.62.0.0
b66cb000-b66cc000 rw-p b66cb000 00:00 0 
b66cc000-b66e1000 r-xp 00000000 08:01 229893     /lib/tls/i686/cmov/libpthread-2.9.so
b66e1000-b66e2000 r--p 00014000 08:01 229893     /lib/tls/i686/cmov/libpthread-2.9.so
b66e2000-b66e3000 rw-p 00015000 08:01 229893     /lib/tls/i686/cmov/libpthread-2.9.so
b66e3000-b66e5000 rw-p b66e3000 00:00 0 
b66e5000-b66e7000 r-xp 00000000 08:01 229524     /lib/tls/i686/cmov/libdl-2.9.so
b66e7000-b66e8000 r--p 00001000 08:01 229524     /lib/tls/i686/cmov/libdl-2.9.so
b66e8000-b66e9000 rw-p 00002000 08:01 229524     /lib/tls/i686/cmov/libdl-2.9.so
b66e9000-b66fe000 r-xp 00000000 08:01 4605454    /usr/lib/libICE.so.6.3.0
b66fe000-b66ff000 rw-p 00014000 08:01 4605454    /usr/lib/libICE.so.6.3.0
b66ff000-b6701000 rw-p b66ff000 00:00 0 
b6701000-b6708000 r-xp 00000000 08:01 4604378    /usr/lib/libSM.so.6.0.0
b6708000-b6709000 r--p 00006000 08:01 4604378    /usr/lib/libSDCOP aborting call from 'anonymous-3686' to 'krecipes'
KCrash: Application 'krecipes' crashing...
Could not find 'drkonqi' executable.
pablo@hem:~$ KCrash cannot reach kdeinit, launching directly.



Any suggestions? :confused:

---

### Post by Pablo W on 2009-07-12
Update on 12 July 09: I still cannot make it work. Since the previous post I have tried to fix the problem by uninstalling krecipes and installing it again from ther terminal (the first time I had installed it from Synaptic), but nothing changed.
I also tried to create a launcher from gnome's bar, and nothing (I do not have krecipes among the programmes to be launched). My knowledge is very limited and I really don't know what else I could try. :sad:

I guess it must be a pretty simple thing, but the lack of further feedback from the forum keeps me puzzled :confused:.

Is there anybody out there? Thanks!

---

### Post by leef on 2009-07-12
Did you try "gourmet" for gnome? It's a recipe manager too, not sure if it has the features you want but it's worth a try. For what it's worth I get the same problem trying to run krecipe you could try deleting the config (which is at $HOME/.kde/share/config/krecipesrc) and using a mysql database but not only would that be a pain, it probably wouldn't fix the problem.

---

### Post by Pablo W on 2009-07-13
> **leef said:**
> Did you try "gourmet" for gnome? It's a recipe manager too, not sure if it has the features you want but it's worth a try. For what it's worth I get the same problem trying to run krecipe you could try deleting the config (which is at $HOME/.kde/share/config/krecipesrc) and using a mysql database but not only would that be a pain, it probably wouldn't fix the problem.

Thanks, leef for your suggestion. I have installed "gourmet" and I'm trying it. Unfortunately, although it seems to be a nice recipe manager, apparently it provides just a few of the features you could find in krecipes. The ones I was looking for are not there :(

I'm probably wrong, but I thought I had read several times in the forum that running kde applications under gnome was a very simple task. I guess in the future I should not be so naive when reading the forum :(

Anyway, it would be great if someone could recommend another good recipe manager or (I'm not giving up) a way to run krecipes under gnome.

Thanks!

---

### Post by gordon3913 on 2009-09-22
I get this message when I tried to run krecipes:-

Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

This is the terminal notice:-
38f840c565b6ed5dad60d56-xKCrash: Application 'krecipes' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.


How can I fix this?

---


---
title: "Barrybackup Buffer Overflow"
date: 2011-10-31
forum: Desktop Environments
---

### Post by MSwal2846 on 2011-10-31
I just installed (clean install) of UBUNTU 11.10.  I am attempting to backup my Blackberry Torch utilizing the barrybackup and barrybackup-gui under Unity.  When I go to a terminal, connect my phone, stat barrybackup, I get this error:

[PHP]-> barrybackup

(process:5637): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (42) on option of type 0
*** buffer overflow detected ***: barrybackup terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0xb70cb8d5]
/lib/i386-linux-gnu/libc.so.6(+0xe66d7)[0xb70ca6d7]
/lib/i386-linux-gnu/libc.so.6(+0xe5c02)[0xb70c9c02]
/usr/lib/libtar.so.0(th_finish+0x48)[0xb729cb48]
/usr/lib/libtar.so.0(th_write+0x40)[0xb729c550]
barrybackup[0x80653fe]
barrybackup[0x8062bf1]
/usr/lib/libbarry.so.0(+0x4827e)[0xb77f927e]
/usr/lib/libbarry.so.0(_ZN5Barry4Mode7Desktop12LoadDatabaseEjRNS_6ParserE+0xc3)[0xb77fbb63]
barrybackup[0x8060f46]
/usr/lib/libglibmm-2.4.so.1(+0x37172)[0xb73e4172]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a5f4)[0xb73115f4]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d31)[0xb7166d31]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0xb70b60ce]
======= Memory map: ========
08048000-0806d000 r-xp 00000000 08:01 2892551    /usr/bin/barrybackup
0806d000-0806e000 r--p 00024000 08:01 2892551    /usr/bin/barrybackup
0806e000-0806f000 rw-p 00025000 08:01 2892551    /usr/bin/barrybackup
08533000-08777000 rw-p 00000000 00:00 0          [heap]
b302e000-b302f000 ---p 00000000 00:00 0 
b302f000-b382f000 rw-p 00000000 00:00 0 
b382f000-b388f000 rw-s 00000000 00:04 284688416  /SYSV00000000 (deleted)
b388f000-b38c0000 r-xp 00000000 08:01 2886467    /usr/lib/libcroco-0.6.so.3.0.1
b38c0000-b38c1000 r--p 00030000 08:01 2886467    /usr/lib/libcroco-0.6.so.3.0.1
b38c1000-b38c3000 rw-p 00031000 08:01 2886467    /usr/lib/libcroco-0.6.so.3.0.1
b38c3000-b38f9000 r-xp 00000000 08:01 2889059    /usr/lib/i386-linux-gnu/librsvg-2.so.2.34.1
b38f9000-b38fa000 r--p 00036000 08:01 2889059    /usr/lib/i386-linux-gnu/librsvg-2.so.2.34.1
b38fa000-b38fb000 rw-p 00037000 08:01 2889059    /usr/lib/i386-linux-gnu/librsvg-2.so.2.34.1
b390d000-b390e000 r-xp 00000000 08:01 2889431    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
b390e000-b390f000 r--p 00000000 08:01 2889431    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
b390f000-b3910000 rw-p 00001000 08:01 2889431    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
b3910000-b392b000 r--s 00000000 08:01 3415254    /usr/share/mime/mime.cache
b392b000-b3930000 r--s 00000000 08:01 5245980    /home/mswallow/.local/share/mime/mime.cache
b3930000-b46ce000 r--p 00000000 08:01 4337157    /usr/share/icons/hicolor/icon-theme.cache
b46ce000-b4904000 r--p 00000000 08:01 4338840    /usr/share/icons/gnome/icon-theme.cache
b4904000-b49ed000 r--p 00000000 08:01 4338955    /usr/share/icons/Humanity/icon-theme.cache
b49ed000-b49f8000 r--p 00000000 08:01 4346230    /usr/share/icons/Humanity-Dark/icon-theme.cache
b49f8000-b4a1b000 r--p 00000000 08:01 4348351    /usr/share/icons/ubuntu-mono-dark/icon-theme.cache
b4a1b000-b4a2e000 r-xp 00000000 08:01 2888180    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a2e000-b4a2f000 r--p 00012000 08:01 2888180    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a2f000-b4a30000 rw-p 00013000 08:01 2888180    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a30000-b4a40000 r-xp 00000000 08:01 19137518   /lib/i386-linux-gnu/libudev.so.0.12.0
b4a40000-b4a41000 r--p 0000f000 08:01 19137518   /lib/i386-linux-gnu/libudev.so.0.12.0
b4a41000-b4a42000 rw-p 00010000 08:01 19137518   /lib/i386-linux-gnu/libudev.so.0.12.0
b4a42000-b4a89000 r-xp 00000000 08:01 19137455   /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b4a89000-b4a8a000 r--p 00046000 08:01 19137455   /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b4a8a000-b4a8b000 rw-p 00047000 08:01 19137455   /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b4a8b000-b4aa0000 r-xp 00000000 08:01 2888736    /usr/lib/gvfs/libgvfscommon.so
b4aa0000-b4aa1000 r--p 00015000 08:01 2888736    /usr/lib/gvfs/libgvfscommon.so
b4aa1000-b4aa2000 rw-p 00016000 08:01 2888736    /usr/lib/gvfs/libgvfscommon.so
b4aa2000-b4acc000 r-xp 00000000 08:01 2888181    /usr/lib/gio/modules/libgvfsdbus.so
b4acc000-b4acd000 r--p 00029000 08:01 2888181    /usr/lib/gio/modules/libgvfsdbus.so
b4acd000-b4ace000 rw-p 0002a000 08:01 2888181    /usr/lib/gio/modules/libgvfsdbus.so
b4ace000-b4b0d000 r-xp 00000000 08:01 2886747    /usr/lib/libibus-1.0.so.0.0.0
b4b0d000-b4b0e000 r--p 0003f000 08:01 2886747    /usr/lib/libibus-1.0.so.0.0.0
b4b0e000-b4b0f000 rw-p 00040000 08:01 2886747    /usr/lib/libibus-1.0.so.0.0.0
b4b17000-b4b18000 rw-p 00000000 00:00 0 
b4b18000-b4b1f000 r-xp 00000000 08:01 2888179    /usr/lib/gio/modules/libdconfsettings.so
b4b1f000-b4b20000 r--p 00006000 08:01 2888179    /usr/lib/gio/modules/libdconfsettings.so
b4b20000-b4b21000 rw-p 00007000 08:01 2888179    /usr/lib/gio/modules/libdconfsettings.so
b4b21000-b4b26000 r-xp 00000000 08:01 2889454    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b4b26000-b4b27000 ---p 00005000 08:01 2889454    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b4b27000-b4b28000 r--p 00005000 08:01 2889454    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b4b28000-b4b29000 rw-p 00006000 08:01 2889454    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b4b29000-b4b7b000 r--p 00000000 08:01 3804743    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b4b7b000-b4bd2000 r--p 00000000 08:01 3804790    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b4bd2000-b4bd4000 r-xp 00000000 08:01 2889526    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b4bd4000-b4bd5000 r--p 00001000 08:01 2889526    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b4bd5000-b4bd6000 rw-p 00002000 08:01 2889526    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b4bd6000-b4bd7000 r--s 00000000 08:01 2359376    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4bd7000-b4bdd000 r--s 00000000 08:01 2359373    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4bdd000-b4bdf000 r--s 00000000 08:01 2359374    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4bdf000-b4be2000 r--s 00000000 08:01 2359384    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4be2000-b4be5000 r--s 00000000 08:01 2359361    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b4be5000-b4be6000 r--s 00000000 08:01 2359385    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4be6000-b4bea000 r--s 00000000 08:01 2359370    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4bea000-b4bee000 r--s 00000000 08:01 2359375    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4bee000-b4bf2000 r--s 00000000 08:01 2368033    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4bf2000-b4bff000 r--s 00000000 08:01 2359380    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4bff000-b4c00000 ---p 00000000 00:00 0 
b4c00000-b5400000 rw-p 00000000 00:00 0 
b5400000-b5425000 rw-p 00000000 00:00 0 
b5425000-b5500000 ---p 00000000 00:00 0 
b5500000-b550b000 r--s 00000000 08:01 2359359    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b550b000-b550c000 ---p 00000000 00:00 0 
b550c000-b5d0c000 rw-p 00000000 00:00 0 
b5d0c000-b5d24000 r-xp 00000000 08:01 2886475    /usr/lib/libdbusmenu-glib.so.4.0.5
b5d24000-b5d25000 r--p 00017000 08:01 2886475    /usr/lib/libdbusmenu-glib.so.4.0.5
b5d25000-b5d26000 rw-p 00018000 08:01 2886475    /usr/lib/libdbusmenu-glib.so.4.0.5
b5d26000-b5d36000 r-xp 00000000 08:01 2886477    /usr/lib/libdbusmenu-gtk.so.4.0.5
b5d36000-b5d37000 ---p 00010000 08:01 2886477    /usr/lib/libdbusmenu-gtk.so.4.0.5
b5d37000-b5d38000 r--p 00010000 08:01 2886477    /usr/lib/libdbusmenu-gtk.so.4.0.5
b5d38000-b5d39000 rw-p 00011000 08:01 2886477    /usr/lib/libdbusmenu-gtk.so.4.0.5
b5d39000-b5d3a000 r--s 00000000 08:01 2359365    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b5d3a000-b5d3b000 r--s 00000000 08:01 2359358    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b5d3b000-b5d42000 r--s 00000000 08:01 2367807    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b5d42000-b5d45000 r--s 00000000 08:01 2359381    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b5d45000-b5d4b000 r--s 00000000 08:01 2367941    /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b5d4b000-b5d78000 r-xp 00000000 08:01 2888670    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5d78000-b5d79000 r--p 0002c000 08:01 2888670    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5d79000-b5d7a000 rw-p 0002d000 08:01 2888670    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5d7a000-b5d80000 r-xp 00000000 08:01 2889020    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5d80000-b5d81000 r--p 00005000 08:01 2889020    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5d81000-b5d82000 rw-p 00006000 08:01 2889020    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5d82000-b5dab000 r-xp 00000000 08:01 2889102    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b5dab000-b5dac000 r--p 00028000 08:01 2889102    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b5dac000-b5dad000 rw-p 00029000 08:01 2889102    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b5dad000-b5db5000 r-xp 00000000 08:01 2886815    /usr/lib/libltdl.so.7.3.0
b5db5000-b5db6000 r--p 00008000 08:01 2886815    /usr/lib/libltdl.so.7.3.0
b5db6000-b5db7000 rw-p 00009000 08:01 2886815    /usr/lib/libltdl.so.7.3.0
b5db7000-b5dc8000 r-xp 00000000 08:01 2889089    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b5dc8000-b5dc9000 r--p 00010000 08:01 2889089    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b5dc9000-b5dca000 rw-p 00011000 08:01 2889089    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b5dca000-b5dd2000 r-xp 00000000 08:01 2889106    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b5dd2000-b5dd3000 r--p 00007000 08:01 2889106    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b5dd3000-b5dd4000 rw-p 00008000 08:01 2889106    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b5dd4000-b5de3000 r-xp 00000000 08:01 2888002    /usr/lib/libcanberra.so.0.2.5
b5de3000-b5de4000 r--p 0000e000 08:01 2888002    /usr/lib/libcanberra.so.0.2.5
b5de4000-b5de5000 rw-p 0000f000 08:01 2888002    /usr/lib/libcanberra.so.0.2.5
b5de5000-b5de9000 r-xp 00000000 08:01 2886441    /usr/lib/libcanberra-gtk.so.0.1.8
b5de9000-b5dea000 r--p 00003000 08:01 2886441    /usr/lib/libcanberra-gtk.so.0.1.8
b5dea000-b5deb000 rw-p 00004000 08:01 2886441    /usr/lib/libcanberra-gtk.so.0.1.8
b5deb000-b5dec000 r--s 00000000 08:01 2359368    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b5dec000-b5df0000 r-xp 00000000 08:01 2888673    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b5df0000-b5df1000 r--p 00004000 08:01 2888673    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b5df1000-b5df2000 rw-p 00005000 08:01 2888673    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b5df2000-b5dfb000 r-xp 00000000 08:01 2887683    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b5dfb000-b5dfc000 r--p 00008000 08:01 2887683    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b5dfc000-b5dfd000 rw-p 00009000 08:01 2887683    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b5dfd000-b5e08000 r-xp 00000000 08:01 19137486   /lib/i386-linux-gnu/libnss_files-2.13.so
b5e08000-b5e09000 r--p 0000a000 08:01 19137486   /lib/i386-linux-gnu/libnss_files-2.13.so
b5e09000-b5e0a000 rw-p 0000b000 08:01 19137486   /lib/i386-linux-gnu/libnss_files-2.13.so
b5e0a000-b5e14000 r-xp 00000000 08:01 19137490   /lib/i386-linux-gnu/libnss_nis-2.13.so
b5e14000-b5e15000 r--p 00009000 08:01 19137490   /lib/i386-linux-gnu/libnss_nis-2.13.so
b5e15000-b5e16000 rw-p 0000a000 08:01 19137490   /lib/i386-linux-gnu/libnss_nis-2.13.so
b5e16000-b5e2b000 r-xp 00000000 08:01 19137480   /lib/i386-linux-gnu/libnsl-2.13.so
b5e2b000-b5e2c000 r--p 00015000 08:01 19137480   /lib/i386-linux-gnu/libnsl-2.13.so
b5e2c000-b5e2d000 rw-p 00016000 08:01 19137480   /lib/i386-linux-gnu/libnsl-2.13.so
b5e2d000-b5e2f000 rw-p 00000000 00:00 0 
b5e2f000-b5e37000 r-xp 00000000 08:01 19137482   /lib/i386-linux-gnu/libnss_compat-2.13.so
b5e37000-b5e38000 r--p 00007000 08:01 19137482   /lib/i386-linux-gnu/libnss_compat-2.13.so
b5e38000-b5e39000 rw-p 00008000 08:01 19137482   /lib/i386-linux-gnu/libnss_compat-2.13.so
b5e39000-b5e3b000 r--s 00000000 08:01 2360381    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b5e3b000-b5e49000 r-xp 00000000 08:01 2886907    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b5e49000-b5e4a000 r--p 0000d000 08:01 2886907    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b5e4a000-b5e4b000 rw-p 0000e000 08:01 2886907    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b5e4b000-b5e4c000 r--p 0043a000 08:01 2890494    /usr/lib/locale/locale-archive
b5e4c000-b5e8c000 r--p 002bd000 08:01 2890494    /usr/lib/locale/locale-archive
b5e8c000-b608c000 r--p 00000000 08:01 2890494    /usr/lib/locale/locale-archive
b608c000-b6091000 rw-p 00000000 00:00 0 
b6091000-b6096000 r-xp 00000000 08:01 2888828    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6096000-b6097000 r--p 00004000 08:01 2888828    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6097000-b6098000 rw-p 00005000 08:01 2888828    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b6098000-b609a000 r-xp 00000000 08:01 2888820    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b609a000-b609b000 r--p 00001000 08:01 2888820    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b609b000-b609c000 rw-p 00002000 08:01 2888820    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b609c000-b60a1000 r-xp 00000000 08:01 2888919    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b60a1000-b60a2000 r--p 00004000 08:01 2888919    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b60a2000-b60a3000 rw-p 00005000 08:01 2888919    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b60a3000-b60c9000 r-xp 00000000 08:01 19137461   /lib/i386-linux-gnu/libexpat.so.1.5.2
b60c9000-b60ca000 ---p 00026000 08:01 19137461   /lib/i386-linux-gnu/libexpat.so.1.5.2
b60ca000-b60cc000 r--p 00026000 08:01 19137461   /lib/i386-linux-gnu/libexpat.so.1.5.2
b60cc000-b60cd000 rw-p 00028000 08:01 19137461   /lib/i386-linux-gnu/libexpat.so.1.5.2
b60cd000-b60ce000 rw-p 00000000 00:00 0 
b60ce000-b60eb000 r-xp 00000000 08:01 2889116    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b60eb000-b60ec000 r--p 0001c000 08:01 2889116    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b60ec000-b60ed000 rw-p 0001d000 08:01 2889116    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b60ed000-b60f5000 r-xp 00000000 08:01 2889110    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b60f5000-b60f6000 r--p 00007000 08:01 2889110    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b60f6000-b60f7000 rw-p 00008000 08:01 2889110    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b60f7000-b60f9000 r-xp 00000000 08:01 2889114    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b60f9000-b60fa000 r--p 00001000 08:01 2889114    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b60fa000-b60fb000 rw-p 00002000 08:01 2889114    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b60fb000-b6123000 r-xp 00000000 08:01 19137504   /lib/i386-linux-gnu/libpng12.so.0.46.0
b6123000-b6124000 r--p 00027000 08:01 19137504   /lib/i386-linux-gnu/libpng12.so.0.46.0
b6124000-b6125000 rw-p 00028000 08:01 19137504   /lib/i386-linux-gnu/libpng12.so.0.46.0Aborted
[/PHP]

This was working fine under 11.04 under Gnome.

Any ideas on how to fix this?

---

### Post by MSwal2846 on 2011-11-02
bump ... any ideas?

---

### Post by dave-is-not-here on 2011-11-16
MSwal2846,

Same thing here (11.10 on a single core atom).  Did you find a resolution?  I may start from sources and see.

dave

---

### Post by MSwal2846 on 2011-11-16
Actually, I gave up on my blackberry and went to android.  So I'm not going to be any help.

---

### Post by mwparis on 2012-04-10
Similar errors here, upon hitting the 'backup' radio in the barrybackup gui. (Am attempting to backup so that I can switch -- finally! -- to Android-based phone.) Halp!

EDIT: I should have mentioned Ubuntu 11.10 -- uname -a:
Linux xxx.xxx.com 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

/etc/apt$ barrybackup 

(process:14657): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (42) on option of type 0

*** buffer overflow detected ***: barrybackup terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7faa4551a4f7]
/lib/x86_64-linux-gnu/libc.so.6(+0xf9410)[0x7faa45519410]
/lib/x86_64-linux-gnu/libc.so.6(+0xf86f6)[0x7faa455186f6]
/usr/lib/libtar.so.0(th_finish+0x2f)[0x7faa461162ef]
/usr/lib/libtar.so.0(th_write+0x51)[0x7faa46115dc1]
barrybackup[0x41f91f]
barrybackup[0x41d1f7]
/usr/lib/libbarry.so.0(+0x487fd)[0x7faa4777c7fd]
/usr/lib/libbarry.so.0(_ZN5Barry4Mode7Desktop12LoadDatabaseEjRNS_6ParserE+0x9d)[0x7faa4777eb3d]
barrybackup[0x41b5b5]
/usr/lib/libglibmm-2.4.so.1(+0x3db3d)[0x7faa46a5cb3d]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6a2b6)[0x7faa463892b6]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x7efc)[0x7faa457c8efc]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d)[0x7faa4550359d]
======= Memory map: ========
00400000-00428000 r-xp 00000000 08:05 22027403                           /usr/bin/barrybackup
00627000-00628000 r--p 00027000 08:05 22027403                           /usr/bin/barrybackup
00628000-00629000 rw-p 00028000 08:05 22027403                           /usr/bin/barrybackup
00629000-0062a000 rw-p 00000000 00:00 0 
011ee000-0143f000 rw-p 00000000 00:00 0                                  [heap]
7faa2c000000-7faa2c054000 rw-p 00000000 00:00 0 
7faa2c054000-7faa30000000 ---p 00000000 00:00 0 
7faa34000000-7faa34021000 rw-p 00000000 00:00 0 
7faa34021000-7faa38000000 ---p 00000000 00:00 0 
7faa3939c000-7faa3939d000 ---p 00000000 00:00 0 
7faa3939d000-7faa39b9d000 rw-p 00000000 00:00 0 
7faa39b9d000-7faa39baa000 r-xp 00000000 08:05 2887364                    /lib/x86_64-linux-gnu/libudev.so.0.12.0
7faa39baa000-7faa39da9000 ---p 0000d000 08:05 2887364                    /lib/x86_64-linux-gnu/libudev.so.0.12.0
7faa39da9000-7faa39daa000 r--p 0000c000 08:05 2887364                    /lib/x86_64-linux-gnu/libudev.so.0.12.0
7faa39daa000-7faa39dab000 rw-p 0000d000 08:05 2887364                    /lib/x86_64-linux-gnu/libudev.so.0.12.0
7faa39dab000-7faa39dd4000 r-xp 00000000 08:05 22024688                   /usr/lib/gio/modules/libgvfsdbus.so
7faa39dd4000-7faa39fd4000 ---p 00029000 08:05 22024688                   /usr/lib/gio/modules/libgvfsdbus.so
7faa39fd4000-7faa39fd5000 r--p 00029000 08:05 22024688                   /usr/lib/gio/modules/libgvfsdbus.so
7faa39fd5000-7faa39fd6000 rw-p 0002a000 08:05 22024688                   /usr/lib/gio/modules/libgvfsdbus.so
7faa39fd6000-7faa39fd7000 rw-p 00000000 00:00 0 
7faa39fd7000-7faa39fde000 r-xp 00000000 08:05 22024686                   /usr/lib/gio/modules/libdconfsettings.so
7faa39fde000-7faa3a1de000 ---p 00007000 08:05 22024686                   /usr/lib/gio/modules/libdconfsettings.so
7faa3a1de000-7faa3a1df000 r--p 00007000 08:05 22024686                   /usr/lib/gio/modules/libdconfsettings.so
7faa3a1df000-7faa3a1e0000 rw-p 00008000 08:05 22024686                   /usr/lib/gio/modules/libdconfsettings.so
7faa3a1e0000-7faa3a1f6000 r-xp 00000000 08:05 22025243                   /usr/lib/gvfs/libgvfscommon.so
7faa3a1f6000-7faa3a3f5000 ---p 00016000 08:05 22025243                   /usr/lib/gvfs/libgvfscommon.so
7faa3a3f5000-7faa3a3f6000 r--p 00015000 08:05 22025243                   /usr/lib/gvfs/libgvfscommon.so
7faa3a3f6000-7faa3a3f7000 rw-p 00016000 08:05 22025243                   /usr/lib/gvfs/libgvfscommon.so
7faa3a3f7000-7faa3a439000 r-xp 00000000 08:05 2887315                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7faa3a439000-7faa3a638000 ---p 00042000 08:05 2887315                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7faa3a638000-7faa3a639000 r--p 00041000 08:05 2887315                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7faa3a639000-7faa3a63a000 rw-p 00042000 08:05 2887315                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7faa3a63a000-7faa3a64d000 r-xp 00000000 08:05 22024687                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7faa3a64d000-7faa3a84c000 ---p 00013000 08:05 22024687                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7faa3a84c000-7faa3a84d000 r--p 00012000 08:05 22024687                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7faa3a84d000-7faa3a84e000 rw-p 00013000 08:05 22024687                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7faa3a84e000-7faa3a88e000 r-xp 00000000 08:05 22023256                   /usr/lib/libibus-1.0.so.0.0.0
7faa3a88e000-7faa3aa8e000 ---p 00040000 08:05 22023256                   /usr/lib/libibus-1.0.so.0.0.0
7faa3aa8e000-7faa3aa8f000 r--p 00040000 08:05 22023256                   /usr/lib/libibus-1.0.so.0.0.0
7faa3aa8f000-7faa3aa90000 rw-p 00041000 08:05 22023256                   /usr/lib/libibus-1.0.so.0.0.0
7faa3aa90000-7faa3aa91000 rw-p 00000000 00:00 0 
7faa3aa91000-7faa3aa97000 r-xp 00000000 08:05 22415973                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7faa3aa97000-7faa3ac96000 ---p 00006000 08:05 22415973                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7faa3ac96000-7faa3ac97000 r--p 00005000 08:05 22415973                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7faa3ac97000-7faa3ac98000 rw-p 00006000 08:05 22415973                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7faa3ac98000-7faa3ac9a000 r-xp 00000000 08:05 22416047                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7faa3ac9a000-7faa3ae99000 ---p 00002000 08:05 22416047                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7faa3ae99000-7faa3ae9a000 r--p 00001000 08:05 22416047                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7faa3ae9a000-7faa3ae9b000 rw-p 00002000 08:05 22416047                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7faa3ae9b000-7faa3ae9c000 ---p 00000000 00:00 0 
7faa3ae9c000-7faa3b69c000 rw-p 00000000 00:00 0 
7faa3b69c000-7faa3b69d000 ---p 00000000 00:00 0 
7faa3b69d000-7faa3be9d000 rw-p 00000000 00:00 0 
7faa3be9d000-7faa3beb4000 r-xp 00000000 08:05 22022984                   /usr/lib/libdbusmenu-glib.so.4.0.5
7faa3beb4000-7faa3c0b4000 ---p 00017000 08:05 22022984                   /usr/lib/libdbusmenu-glib.so.4.0.5
7faa3c0b4000-7faa3c0b5000 r--p 00017000 08:05 22022984                   /usr/lib/libdbusmenu-glib.so.4.0.5
7faa3c0b5000-7faa3c0b6000 rw-p 00018000 08:05 22022984                   /usr/lib/libdbusmenu-glib.so.4.0.5
7faa3c0b6000-7faa3c0c7000 r-xp 00000000 08:05 22022986                   /usr/lib/libdbusmenu-gtk.so.4.0.5
7faa3c0c7000-7faa3c2c6000 ---p 00011000 08:05 22022986                   /usr/lib/libdbusmenu-gtk.so.4.0.5
7faa3c2c6000-7faa3c2c7000 r--p 00010000 08:05 22022986                   /usr/lib/libdbusmenu-gtk.so.4.0.5
7faa3c2c7000-7faa3c2c8000 rw-p 00011000 08:05 22022986                   /usr/lib/libdbusmenu-gtk.so.4.0.5
7faa3c2c8000-7faa3c2cd000 r-xp 00000000 08:05 22025180                   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7faa3c2cd000-7faa3c4cc000 ---p 00005000 08:05 22025180                   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7faa3c4cc000-7faa3c4cd000 r--p 00004000 08:05 22025180                   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7faa3c4cd000-7faa3c4ce000 rw-p 00005000 08:05 22025180                   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7faa3c4ce000-7faa3c4d7000 r-xp 00000000 08:05 22416117                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
7faa3c4d7000-7faa3c6d7000 ---p 00009000 08:05 22416117                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
7faa3c6d7000-7faa3c6d8000 r--p 00009000 08:05 22416117                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
7faa3c6d8000-7faa3c6d9000 rw-p 0000a000 08:05 22416117                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
7faa3c6d9000-7faa3c708000 r-xp 00000000 08:05 22025177                   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7faa3c708000-7faa3c908000 ---p 0002f000 08:05 22025177                   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7faa3c908000-7faa3c909000 r--p 0002f000 08:05 22025177                   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7faa3c909000-7faa3c90a000 rw-p 00030000 08:05 22025177                   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
7faa3c90a000-7faa3c910000 r-xp 00000000 08:05 22027478                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7faa3c910000-7faa3cb0f000 ---p 00006000 08:05 22027478                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7faa3cb0f000-7faa3cb10000 r--p 00005000 08:05 22027478                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7faa3cb10000-7faa3cb11000 rw-p 00006000 08:05 22027478                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7faa3cb11000-7faa3cb3c000 r-xp 00000000 08:05 22026103                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7faa3cb3c000-7faa3cd3b000 ---p 0002b000 08:05 22026103                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7faa3cd3b000-7faa3cd3c000 r--p 0002a000 08:05 22026103                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7faa3cd3c000-7faa3cd3d000 rw-p 0002b000 08:05 22026103                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7faa3cd3d000-7faa3cd45000 r-xp 00000000 08:05 22023324                   /usr/lib/libltdl.so.7.3.0
7faa3cd45000-7faa3cf45000 ---p 00008000 08:05 22023324                   /usr/lib/libltdl.so.7.3.0
7faa3cf45000-7faa3cf46000 r--p 00008000 08:05 22023324                   /usr/lib/libltdl.so.7.3.0
7faa3cf46000-7faa3cf47000 rw-p 00009000 08:05 22023324                   /usr/lib/libltdl.so.7.3.0
7faa3cf47000-7faa3cf57000 r-xp 00000000 08:05 22027547                   /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7faa3cf57000-7faa3d156000 ---p 00010000 08:05 22027547                   /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7faa3d156000-7faa3d157000 r--p 0000f000 08:05 22027547                   /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7faa3d157000-7faa3d158000 rw-p 00010000 08:05 22027547                   /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7faa3d158000-7faa3d15f000 r-xp 00000000 08:05 22023909                   /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7faa3d15f000-7faa3d35e000 ---p 00007000 08:05 22023909                   /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7faa3d35e000-7faa3d35f000 r--p 00006000 08:05 22023909                   /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7faa3d35f000-7faa3d360000 rw-p 00007000 08:05 22023909                   /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7faa3d360000-7faa3d36f000 r-xp 00000000 08:05 22020891                   /usr/lib/libcanberra.so.0.2.5
7faa3d36f000-7faa3d56e000 ---p 0000f000 08:05 22020891                   /usr/lib/libcanberra.so.0.2.5
7faa3d56e000-7faa3d56f000 r--p 0000e000 08:05 22020891                   /usr/lib/libcanberra.so.0.2.5
7faa3d56f000-7faa3d570000 rw-p 0000f000 08:05 22020891                   /usr/lib/libcanberra.so.0.2.5
7faa3d570000-7faa3d574000 r-xp 00000000 08:05 22020899                   /usr/lib/libcanberra-gtk.so.0.1.8
7faa3d574000-7faa3d773000 ---p 00004000 08:05 22020899                   /usr/lib/libcanberra-gtk.so.0.1.8
7faa3d773000-7faa3d774000 r--p 00003000 08:05 22020899                   /usr/lib/libcanberra-gtk.so.0.1.8
7faa3d774000-7faa3d775000 rw-p 00004000 08:05 22020899                   /usr/lib/libcanberra-gtk.so.0.1.8
7faa3d775000-7faa3d77a000 r-xp 00000000 08:05 22023247                   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7faa3d77a000-7faa3d979000 ---p 00005000 08:05 22023247                   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7faa3d979000-7faa3d97a000 r--p 00004000 08:05 22023247                   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7faa3d97a000-7faa3d97b000 rw-p 00005000 08:05 22023247                   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
7faa3d97b000-7faa3d989000 r-xp 00000000 08:05 22023416                   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
7faa3d989000-7faa3db88000 ---p 0000e000 08:05 22023416                   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
7faa3db88000-7faa3db89000 r--p 0000d000 08:05 22023416                   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
7faa3db89000-7faa3db8a000 rw-p 0000e000 08:05 22023416                   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
7faa3db8a000-7faa3db96000 r-xp 00000000 08:05 2888132                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7faa3db96000-7faa3dd95000 ---p 0000c000 08:05 2888132                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7faa3dd95000-7faa3dd96000 r--p 0000b000 08:05 2888132                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7faa3dd96000-7faa3dd97000 rw-p 0000c000 08:05 2888132                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7faa3dd97000-7faa3dda1000 r-xp 00000000 08:05 2888136                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7faa3dda1000-7faa3dfa1000 ---p 0000a000 08:05 2888136                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7faa3dfa1000-7faa3dfa2000 r--p 0000a000 08:05 2888136                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7faa3dfa2000-7faa3dfa3000 rw-p 0000b000 08:05 2888136                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7faa3dfa3000-7faa3dfba000 r-xp 00000000 08:05 2888124                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7faa3dfba000-7faa3e1b9000 ---p 00017000 08:05 2888124                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7faa3e1b9000-7faa3e1ba000 r--p 00016000 08:05 2888124                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7faa3e1ba000-7faa3e1bb000 rw-p 00017000 08:05 2888124                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7faa3e1bb000-7faa3e1bd000 rw-p 00000000 00:00 0 
7faa3e1bd000-7faa3e1c5000 r-xp 00000000 08:05 2888127                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7faa3e1c5000-7faa3e3c4000 ---p 00008000 08:05 2888127                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7faa3e3c4000-7faa3e3c5000 r--p 00007000 08:05 2888127                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7faa3e3c5000-7faa3e3c6000 rw-p 00008000 08:05 2888127                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7faa3e3c6000-7faa3eaaa000 r--p 00000000 08:05 22026341                   /usr/lib/locale/locale-archive
7faa3eaaa000-7faa3eaaf000 r-xp 00000000 08:05 22027286                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7faa3eaaf000-7faa3ecae000 ---p 00005000 08:05 22027286                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7faa3ecae000-7faa3ecaf000 r--p 00004000 08:05 22027286                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7faa3ecaf000-7faa3ecb0000 rw-p 00005000 08:05 22027286                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7faa3ecb0000-7faa3ecb2000 r-xp 00000000 08:05 22027278                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7faa3ecb2000-7faa3eeb1000 ---p 00002000 08:05 22027278                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7faa3eeb1000-7faa3eeb2000 r--p 00001000 08:05 22027278                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7faa3eeb2000-7faa3eeb3000 rw-p 00002000 08:05 22027278                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7faa3eeb3000-7faa3eeba000 r-xp 00000000 08:05 22027377                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7faa3eeba000-7faa3f0b9000 ---p 00007000 08:05 22027377                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7faa3f0b9000-7faa3f0ba000 r--p 00006000 08:05 22027377                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7faa3f0ba000-7faa3f0bb000 rw-p 00007000 08:05 22027377                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7faa3f0bb000-7faa3f0e2000 r-xp 00000000 08:05 2887321                    /lib/x86_64-linux-gnu/libexpat.so.1.5.2
7faa3f0e2000-7faa3f2e2000 ---p 00027000 08:05 2887321                    /lib/x86_64-linux-gnu/libexpat.so.1.5.2Aborted

```

---

### Post by mwparis on 2012-04-10
Can anyone give me a hand here?

---

### Post by deadimp on 2012-11-03
I ran into this problem as well on 12.04. Looked around and saw that other peeps were having the same problem on Gentoo. One person [posted]("http://forums.gentoo.org/viewtopic-p-6877454.html?sid=0479913fb3f9e9885fb7f0a70ed6faac#6877454") a solution which leads to a [fixed bug for Gentoo]("https://bugs.gentoo.org/show_bug.cgi?id=340253").

Downloaded the source for the [libtar]("https://bugs.launchpad.net/ubuntu/+source/libtar/+bugs") 1.2.11 package and found that the bugfix is not made in the debian stream (or whatever you call it).

Gonna file a bug report and see about fixing. First time for me lol.

EDIT: Posted the bug: [https://bugs.launchpad.net/ubuntu/+source/libtar/+bug/1074752](https://bugs.launchpad.net/ubuntu/+source/libtar/+bug/1074752)

---


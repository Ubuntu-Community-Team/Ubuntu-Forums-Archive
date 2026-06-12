---
title: "Kiba-Dock wont load right :("
date: 2007-04-29
forum: Desktop Environments
---

### Post by SableSlayer on 2007-04-29
Hi I installed Kiba dock like it said to on the kiba dock wiki

```
 
  1.  Open a Terminal Window.
   2. Type the following:

# sudo gedit /etc/apt/sources.list

   1. Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins


```

but after i try to run kiba dock it wont run and i get this error message

root@XeN-desktop:/home/sableslayer# kiba-dock
** Message: cant load file /root/.kiba-dock/config into buffer notifications: Failed to open file '/root/.kiba-dock/config': No such file or directory

Its like its not their but i know i installed it. Any ideas?

---

### Post by scanez on 2007-04-29
Run gset-kiba first. Then try again.

Also, why on earth are you running this as root?!?!? :)

---

### Post by SableSlayer on 2007-04-29
i ran it under root cause thats what i installed it under Lol. 

anyways i ran gset-kiba and got this

```

sableslayer@XeN-desktop:~$ gset-kiba
** Message: Failed to open Launcher Directory /home/sableslayer/.kiba-dock/launcher/
otification: Error opening directory '/home/sableslayer/.kiba-dock/launcher/': No such file or directory

*** glibc detected *** gset-kiba: double free or corruption (fasttop): 0x08314db8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb776b7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb776ee30]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb787a131]
gset-kiba[0x804bc55]
gset-kiba[0x804dcfe]
gset-kiba[0x804b7bc]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7719ebc]
gset-kiba[0x804b5b1]
======= Memory map: ========
08048000-08054000 r-xp 00000000 03:01 5511295    /usr/bin/gset-kiba
08054000-08055000 rw-p 0000b000 03:01 5511295    /usr/bin/gset-kiba
08055000-0831a000 rw-p 08055000 00:00 0          [heap]
b2d00000-b2d21000 rw-p b2d00000 00:00 0 
b2d21000-b2e00000 ---p b2d21000 00:00 0 
b2eab000-b2eb6000 r-xp 00000000 03:01 1949760    /lib/libgcc_s.so.1
b2eb6000-b2eb7000 rw-p 0000a000 03:01 1949760    /lib/libgcc_s.so.1
b2ec7000-b2ec8000 ---p b2ec7000 00:00 0 
b2ec8000-b36c8000 rw-p b2ec8000 00:00 0 
b36c8000-b36c9000 ---p b36c8000 00:00 0 
b36c9000-b3ec9000 rw-p b36c9000 00:00 0 
b3ec9000-b40af000 r--p 00000000 03:01 5886691    /usr/share/icons/hicolor/icon-theme.cache
b40af000-b5197000 r--p 00000000 03:01 6099068    /usr/share/icons/crystalsvg/icon-theme.cache
b5197000-b583e000 r--p 00000000 03:01 5886687    /usr/share/icons/gnome/icon-theme.cache
b583e000-b5a95000 r--p 00000000 03:01 5884984    /usr/share/icons/Tango/icon-theme.cache
b5a95000-b5b36000 r--p 00000000 03:01 5883787    /usr/share/icons/Tangerine/icon-theme.cache
b5b36000-b5c9c000 r--p 00000000 03:01 5882241    /usr/share/icons/Human/icon-theme.cache
b5c9c000-b5c9d000 ---p b5c9c000 00:00 0 
b5c9d000-b649d000 rw-p b5c9d000 00:00 0 
b649d000-b649e000 ---p b649d000 00:00 0 
b649e000-b6c9e000 rw-p b649e000 00:00 0 
b6c9e000-b6ca5000 r-xp 00000000 03:01 5506749    /usr/lib/libfam.so.0.0.0
b6ca5000-b6ca6000 rw-p 00006000 03:01 5506749    /usr/lib/libfam.so.0.0.0
b6ca6000-b6cac000 r-xp 00000000 03:01 1949723    /lib/libacl.so.1.1.0
b6cac000-b6cad000 rw-p 00005000 03:01 1949723    /lib/libacl.so.1.1.0
b6cad000-b6cb0000 r-xp 00000000 03:01 1949727    /lib/libattr.so.1.1.0
b6cb0000-b6cb1000 rw-p 00002000 03:01 1949727    /lib/libattr.so.1.1.0
b6cc1000-b6cf7000 r-xp 00000000 03:01 1949814    /lib/libsepol.so.1
b6cf7000-b6cf8000 rw-p 00035000 03:01 1949814    /lib/libsepol.so.1
b6cf8000-b6d02000 rw-p b6cf8000 00:00 0 
b6d02000-b6d05000 r-xp 00000000 03:01 5506902    /usr/lib/libgpg-error.so.0.3.0
b6d05000-b6d06000 rw-p 00002000 03:01 5506902    /usr/lib/libgpg-error.so.0.3.0
b6d06000-b6d55000 r-xp 00000000 03:01 5506790    /usr/lib/libgcrypt.so.11.2.2
b6d55000-b6d57000 rw-p 0004e000 03:01 5506790    /usr/lib/libgcrypt.so.11.2.2
b6d57000-b6d6b000 r-xp 00000000 03:01 5507246    /usr/lib/libtasn1.so.3.0.6
b6d6b000-b6d6c000 rw-p 00013000 03:01 5507246    /usr/lib/libtasn1.so.3.0.6
b6d6c000-b6e2c000 r-xp 00000000 03:01 5506614    /usr/lib/libasound.so.2.0.0
b6e2c000-b6e31000 rw-p 000bf000 03:01 5506614    /usr/lib/libasound.so.2.0.0
b6e31000-b6e46000 r-xp 00000000 03:01 5506521    /usr/lib/libICE.so.6.3.0
b6e46000-b6e48000 rw-p 00014000 03:01 5506521    /usr/lib/libICE.so.6.3.0
b6e48000-b6e49000 rw-p b6e48000 00:00 0 
b6e49000-b6e51000 r-xp 00000000 03:01 5506539    /usr/lib/libSM.so.6.0.0
b6e51000-b6e52000 rw-p 00007000 03:01 5506539    /usr/lib/libSM.so.6.0.0
b6e52000-b6e70000 r-xp 00000000 03:01 5507027    /usr/lib/libjpeg.so.62.0.0
b6e70000-b6e71000 rw-p 0001d000 03:01 5507027    /usr/lib/libjpeg.so.62.0.0
b6e71000-b6e7d000 r-xp 00000000 03:01 5506862    /usr/lib/libgnome-keyring.so.0.0.1
b6e7d000-b6e7e000 rw-p 0000b000 03:01 5506862    /usr/lib/libgnome-keyring.so.0.0.1
b6e7e000-b6e92000 r-xp 00000000 03:01 5506612    /usr/lib/libart_lgpl_2.so.2.3.17
b6e92000-b6e93000 rw-p 00013000 03:01 5506612    /usr/lib/libart_lgpl_2.so.2.3.17
b6e93000-b6ebc000 r-xp 00000000 03:01 5506872    /usr/lib/libgnomecanvas-2.so.0.1400.0
b6ebc000-b6ebd000 rw-p 00029000 03:01 5506872    /usr/lib/libgnomecanvas-2.so.0.1400.0
b6ebd000-b6f18000 r-xp 00000000 03:01 5506649    /usr/lib/libbonoboui-2.so.0.0.0
b6f18000-b6f1b000 rw-p 0005a000 03:01 5506649    /usr/lib/libbonoboui-2.so.0.0.0
b6f1b000-b6f1d000 r-xp 00000000 03:01 1953030    /lib/tls/i686/cmov/libutil-2.5.so
b6f1d000-b6f1f000 rw-p 00001000 03:01 1953030    /lib/tls/i686/cmov/libutil-2.5.so
b6f1f000-b6f33000 r-xp 00000000 03:01 1949813    /lib/libselinux.so.1
b6f33000-b6f35000 rw-p 00013000 03:01 1949813    /lib/libselinux.so.1
b6f35000-b6f44000 r-xp 00000000 03:01 1953024    /lib/tls/i686/cmov/libresolv-2.5.so
b6f44000-b6f46000 rw-p 0000f000 03:01 1953024    /lib/tls/i686/cmov/libresolv-2.5.so
b6f46000-b6f48000 rw-p b6f46000 00:00 0 
b6f48000-b6f56000 r-xp 00000000 03:01 5506628    /usr/lib/libavahi-client.so.3.2.2
b6f56000-b6f57000 rw-p 0000e000 03:01 5506628    /usr/lib/libavahi-client.so.3.2.2
b6f57000-b6f61000 r-xp 00000000 03:01 5506630    /usr/lib/libavahi-common.so.3.4.3
b6f61000-b6f62000 rw-p 00009000 03:01 5506630    /usr/lib/libavahi-common.so.3.4.3
b6f62000-b6fcc000 r-xp 00000000 03:01 5506898    /usr/lib/libgnutls.so.13.0.9
b6fcc000-b6fd2000 rw-p 0006a000 03:01 5506898    /usr/lib/libgnutls.so.13.0.9
b6fd2000-b7003000 r-xp 00000000 03:01 5506687    /usr/lib/libdbus-1.so.3.2.0
b7003000-b7004000 rw-p 00031000 03:01 5506687    /usr/lib/libdbus-1.so.3.2.0
b7004000-b701e000 r-xp 00000000 03:01 5506689    /usr/lib/libdbus-glib-1.so.2.1.0
b701e000-b701f000 rw-p 0001a000 03:01 5506689    /usr/lib/libdbus-glib-1.so.2.1.0
b701f000-b7136000 r-xp 00000000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b7136000-b713c000 rw-p 00116000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b713c000-b7140000 r-xp 00000000 03:01 5506535    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7140000-b7141000 rw-p 00003000 03:01 5506535    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7141000-b7161000 r-xp 00000000 03:01 5506626    /usr/lib/libaudiofile.so.0.0.2
b7161000-b7163000 rw-p 00020000 03:01 5506626    /usr/lib/libaudiofile.so.0.0.2
b7163000-b716c000 r-xp 00000000 03:01 5506736    /usr/lib/libesd.so.0.2.36
b716c000-b716d000 rw-p 00009000 03:01 5506736    /usr/lib/libesd.so.0.2.36
b716d000-b7174000 r-xp 00000000 03:01 1949803    /lib/libpopt.so.0.0.0
b7174000-b7175000 rw-p 00006000 03:01 1949803    /lib/libpopt.so.0.0.0
b7175000-b71ff000 r-xp 00000000 03:01 5506888    /usr/lib/libgnomeui-2.so.0.1788.4
b71ff000-b7203000 rw-p 00089000 03:01 5506888    /usr/lib/libgnomeui-2.so.0.1788.4
b7203000-b720a000 r-xp 00000000 03:01 1953026    /lib/tls/i686/cmov/librt-2.5.so
b720a000-b720c000 rw-p 00006000 03:01 1953026    /lib/tls/i686/cmov/librt-2.5.so
b720c000-b7210000 r-xp 00000000 03:01 5506954    /usr/lib/libgthread-2.0.so.0.1200.11
b7210000-b7211000 rw-p 00003000 03:01 5506954    /usr/lib/libgthread-2.0.so.0.1200.11
b7211000-b725a000 r-xp 00000000 03:01 5506531    /usr/lib/libORBit-2.so.0.1.0
b725a000-b7264000 rw-p 00048000 03:01 5506531    /usr/lib/libORBit-2.so.0.1.0
b7264000-b7293000 r-xp 00000000 03:01 5506788    /usr/lib/libgconf-2.so.4.1.2
b7293000-b7296000 rw-p 0002e000 03:01 5506788    /usr/lib/libgconf-2.so.4.1.2
b7296000-b72ec000 r-xp 00000000 03:01 5506890    /usr/lib/libgnomevfs-2.so.0.1800.1
b72ec000-b72ef000 rw-p 00055000 03:01 5506890    /usr/lib/libgnomevfs-2.so.0.1800.1
b72ef000-b7302000 r-xp 00000000 03:01 5506647    /usr/lib/libbonobo-activation.so.4.0.0
b7302000-b7304000 rw-p 00013000 03:01 5506647    /usr/lib/libbonobo-activation.so.4.0.0
b7304000-b7356000 r-xp 00000000 03:01 5506645    /usr/lib/libbonobo-2.so.0.0.0
b7356000-b7360000 rw-p 00051000 03:01 5506645    /usr/lib/libbonobo-2.so.0.0.0
b7360000-b7374000 r-xp 00000000 03:01 5506858    /usr/lib/libgnome-2.so.0.1800.0
b7374000-b7375000 rw-p 00014000 03:01 5506858    /usr/lib/libgnome-2.so.0.1800.0
b7378000-b7384000 r-xp 00000000 03:01 5509087    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7384000-b7385000 rw-p 0000b000 03:01 5509087    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7385000-b738f000 r-xp 00000000 03:01 5570591    /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
b738f000-b7390000 rw-p 00009000 03:01 5570591    /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
b7390000-b740d000 r--p 00000000 03:01 5750934    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b740d000-b740f000 r-xp 00000000 03:01 5637307    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b740f000-b7410000 rw-p 00001000 03:01 5637307    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7410000-b7416000 r--s 00000000 03:01 294991     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7416000-b7417000 r--s 00000000 03:01 295019     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b7417000-b741a000 r--s 00000000 03:01 295007     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b741a000-b741b000 r--s 00000000 03:01 295013     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b741b000-b741c000 r--s 00000000 03:01 294994     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b741c000-b7420000 r--s 00000000 03:01 294988     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7420000-b7421000 r--s 00000000 03:01 294976     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7421000-b7423000 r--s 00000000 03:01 294981     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b7423000-b7425000 r--s 00000000 03:01 294969     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b7425000-b7426000 r--s 00000000 03:01 294984     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b7426000-b7428000 r--s 00000000 03:01 294992     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b7428000-b742e000 r--s 00000000 03:01 294982     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b742e000-b7430000 r--s 00000000 03:01 295008     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7430000-b7432000 r--s 00000000 03:01 295005     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b7432000-b743a000 r--s 00000000 03:01 295011     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b743a000-b7440000 r--s 00000000 03:01 294965     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b7440000-b7441000 r--s 00000000 03:01 294974     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7441000-b7443000 r--s 00000000 03:01 295009     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7443000-b7449000 r--s 00000000 03:01 295003     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7449000-b744c000 r--s 00000000 03:01 294980     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b744c000-b7450000 r--s 00000000 03:01 294963     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7450000-b7452000 r--s 00000000 03:01 295177     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7452000-b7453000 r--s 00000000 03:01 295017     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7453000-b7454000 r--s 00000000 03:01 295014     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7454000-b7455000 r--s 00000000 03:01 294999     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b7455000-b7456000 r--s 00000000 03:01 294970     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b7456000-b7457000 r--s 00000000 03:01 295000     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b7457000-b745a000 r--s 00000000 03:01 294996     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b745a000-b745f000 r--s 00000000 03:01 295018     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b745f000-b7461000 r--s 00000000 03:01 294962     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7461000-b7462000 r--s 00000000 03:01 295015     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7462000-b7464000 r--s 00000000 03:01 294967     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7464000-b7465000 r--s 00000000 03:01 294993     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b7465000-b746a000 r--s 00000000 03:01 294987     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b746a000-b746e000 r--s 00000000 03:01 294964     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b746e000-b7470000 r--s 00000000 03:01 294985     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7470000-b7473000 r--s 00000000 03:01 294977     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7473000-b7474000 r--s 00000000 03:01 295010     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7474000-b7476000 r--s 00000000 03:01 294972     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7476000-b747a000 r--s 00000000 03:01 294968     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b747a000-b7480000 r--s 00000000 03:01 294966     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7480000-b7481000 r--s 00000000 03:01 294989     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7481000-b7489000 r--s 00000000 03:01 294995     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b7489000-b749b000 r-xp 00000000 03:01 5570590    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b749b000-b749c000 rw-p 00011000 03:01 5570590    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b749c000-b74a5000 r-xp 00000000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b74a5000-b74a7000 rw-p 00008000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b74a7000-b74af000 r-xp 00000000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b74af000-b74b1000 rw-p 00007000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b74b1000-b74c4000 r-xp 00000000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b74c4000-b74c6000 rw-p 00012000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b74c6000-b74c8000 rw-p b74c6000 00:00 0 
b74c8000-b74cf000 r-xp 00000000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b74cf000-b74d1000 rw-p 00006000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b74d2000-b74d4000 r-xp 00000000 03:01 5506634    /usr/lib/libavahi-glib.so.1.0.1
b74d4000-b74d5000 rw-p 00001000 03:01 5506634    /usr/lib/libavahi-glib.so.1.0.1
b74d5000-b74d7000 r--s 00000000 03:01 294990     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b74d7000-b74da000 r--s 00000000 03:01 294997     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b74da000-b74dc000 r--s 00000000 03:01 294978     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b74dc000-b74de000 r--s 00000000 03:01 297137     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b74de000-b74df000 r-xp 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b74df000-b74e1000 rw-p 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b74e1000-b751c000 r--p 00000000 03:01 5571581    /usr/lib/locale/en_US.utf8/LC_CTYPE
b751c000-b751d000 r--p 00000000 03:01 5571586    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b751d000-b75f4000 r--p 00000000 03:01 5571580    /usr/lib/locale/en_US.utf8/LC_COLLATE
b75f4000-b75f6000 rw-p b75f4000 00:00 0 
b75f6000-b7609000 r-xp 00000000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b7609000-b760b000 rw-p 00013000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b760b000-b760d000 rw-p b760b000 00:00 0 
b760d000-b7611000 r-xp 00000000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b7611000-b7612000 rw-p 00003000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b7612000-b7613000 rw-p b7612000 00:00 0 
b7613000-b7635000 r-xp 00000000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b7635000-b7636000 rw-p 00021000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b7636000-b7638000 r-xp 00000000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b7638000-b7639000 rw-p 00001000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b7639000-b7657000 r-xp 00000000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b7657000-b7659000 rw-p 0001d000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b7659000-b766c000 r-xp 00000000 03:01 5507304    /usr/lib/libz.so.1.2.3
b766c000-b766d000 rw-p 00012000 03:01 5507304    /usr/lib/libz.so.1.2.3
b766d000-b76d5000 r-xp 00000000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b76d5000-b76d8000 rw-p 00068000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b76d8000-b76d9000 rw-p b76d8000 00:00 0 
b76d9000-b7703000 r-xp 00000000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7703000-b7704000 rw-p 0002a000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7704000-b783f000 r-xp 00000000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b783f000-b7840000 r--p 0013b000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7840000-b7842000 rw-p 0013c000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7842000-b7845000 rw-p b7842000 00:00 0 
b7845000-b78d9000 r-xp 00000000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b78d9000-b78da000 rw-p 00093000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b78da000-b78dc000 r-xp 00000000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b78dc000-b78de000 rw-p 00001000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b78de000-b78e0000 r-xp 00000000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b78e0000-b78e1000 rw-p 00002000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b78e1000-b78e2000 rw-p b78e1000 00:00 0 
b78e2000-b791b000 r-xp 00000000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b791b000-b791c000 rw-p 00039000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b791c000-b7a09000 r-xp 00000000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b7a09000-b7a0d000 rw-p 000ed000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b7a0d000-b7a7b000 r-xp 00000000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b7a7b000-b7a7d000 rw-p 0006d000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b7a7d000-b7ab9000 r-xp 00000000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7ab9000-b7abb000 rw-p 0003b000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7abb000-b7abf000 r-xp 00000000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7abf000-b7ac0000 rw-p 00003000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7ac0000-b7ac8000 r-xp 00000000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7ac8000-b7ac9000 rw-p 00007000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7ac9000-b7aca000 rw-p b7ac9000 00:00 0 
b7aca000-b7acf000 r-xp 00000000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7acf000-b7ad0000 rw-p 00005000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7ad0000-b7ad7000 r-xp 00000000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7ad7000-b7ad8000 rw-p 00006000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7ad8000-b7ada000 r-xp 00000000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7ada000-b7adb000 rw-p 00001000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7adb000-b7ae2000 r-xp 00000000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7ae2000-b7ae3000 rw-p 00006000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7ae3000-b7af0000 r-xp 00000000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7af0000-b7af1000 rw-p 0000d000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7af1000-b7b14000 r-xp 00000000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b14000-b7b1c000 rw-p 00023000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b1c000-b7b1d000 rw-p b7b1c000 00:00 0 
b7b1d000-b7b24000 r-xp 00000000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b24000-b7b25000 rw-p 00007000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b25000-b7b4a000 r-xp 00000000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b7b4a000-b7b4c000 rw-p 00024000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b7b4c000-b7b62000 r-xp 00000000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7b62000-b7b63000 rw-p 00015000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7b63000-b7b7c000 r-xp 00000000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7b7c000-b7b7e000 rw-p 00018000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7b7e000-b7c01000 r-xp 00000000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c01000-b7c04000 rw-p 00083000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c04000-b7f55000 r-xp 00000000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f55000-b7f5b000 rw-p 00351000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f5b000-b7f5d000 rw-p b7f5b000 00:00 0 
b7f5d000-b7f5e000 r--p 00000000 03:01 5571589    /usr/lib/locale/en_US.utf8/LC_TIME
b7f5e000-b7f5f000 r--p 00000000 03:01 5571584    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f5f000-b7f60000 r--p 00000000 03:01 5571590    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f60000-b7f61000 r--p 00000000 03:01 5571587    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f61000-b7f62000 r--p 00000000 03:01 5571585    /usr/lib/locale/en_US.utf8/LC_NAME
b7f62000-b7f63000 r--p 00000000 03:01 5571579    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f63000-b7f64000 r--p 00000000 03:01 5571588    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f64000-b7f65000 r--p 00000000 03:01 5571583    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f65000-b7f6c000 r--s 00000000 03:01 5508729    /usr/lib/gconv/gconv-modules.cache
b7f6c000-b7f6d000 r--p 00000000 03:01 5571582    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f6d000-b7f6e000 rw-p b7f6d000 00:00 0 
b7f6e000-b7f87000 r-xp 00000000 03:01 1949717    /lib/ld-2.5.so
b7f87000-b7f89000 rw-p 00019000 03:01 1949717    /lib/ld-2.5.so
bfe3b000-bfe53000 rw-p bfe3b000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by scanez on 2007-04-29
... and then did you try running kiba-dock again?

Also, I strongly suggest you not run it (or anything that is not absolutely necessary) as root.

---

### Post by SableSlayer on 2007-04-29
wow it works now :) thanks..


tho i do have to run it under root for it to work. if i run it under my normal user it wont run and i get this
```

sableslayer@XeN-desktop:~$ kiba-dock
*** glibc detected *** kiba-dock: malloc(): memory corruption (fast): 0x08094eb0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76aa6fc]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0x8d)[0xb76ab31d]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x3e)[0xb7a0f22e]
/usr/lib/libgobject-2.0.so.0[0xb7a99e65]
/usr/lib/libgobject-2.0.so.0(g_type_register_static+0x3a0)[0xb7aa1f90]
/usr/lib/libatk-1.0.so.0(atk_implementor_get_type+0x44)[0xb7bab064]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_get_type+0x73)[0xb7e9a443]
kiba-dock(kiba_get_type+0x2f)[0x805200f]
kiba-dock(kiba_new+0xc)[0x805205c]
kiba-dock(main+0x235)[0x8051235]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7657ebc]
kiba-dock[0x8050f71]
======= Memory map: ========
08048000-0806b000 r-xp 00000000 03:01 5512133    /usr/bin/kiba-dock
0806b000-0806d000 rw-p 00022000 03:01 5512133    /usr/bin/kiba-dock
0806d000-080af000 rw-p 0806d000 00:00 0          [heap]
b6800000-b6821000 rw-p b6800000 00:00 0 
b6821000-b6900000 ---p b6821000 00:00 0 
b6973000-b697c000 r-xp 00000000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b697c000-b697e000 rw-p 00008000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b697e000-b6986000 r-xp 00000000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6986000-b6988000 rw-p 00007000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6988000-b699b000 r-xp 00000000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b699b000-b699d000 rw-p 00012000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b699d000-b699f000 rw-p b699d000 00:00 0 
b699f000-b69a6000 r-xp 00000000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b69a6000-b69a8000 rw-p 00006000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b69a9000-b69b4000 r-xp 00000000 03:01 1949760    /lib/libgcc_s.so.1
b69b4000-b69b5000 rw-p 0000a000 03:01 1949760    /lib/libgcc_s.so.1
b69b5000-b69b6000 r-xp 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b69b6000-b69b8000 rw-p 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b69b8000-b69f3000 r--p 00000000 03:01 5571581    /usr/lib/locale/en_US.utf8/LC_CTYPE
b69f3000-b69f4000 r--p 00000000 03:01 5571586    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b69f4000-b69f5000 r--p 00000000 03:01 5571589    /usr/lib/locale/en_US.utf8/LC_TIME
b69f5000-b6acc000 r--p 00000000 03:01 5571580    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6acc000-b6acd000 r--p 00000000 03:01 5571584    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6acd000-b6b32000 rw-p b6acd000 00:00 0 
b6b32000-b6b41000 r-xp 00000000 03:01 1949734    /lib/libbz2.so.1.0.3
b6b41000-b6b42000 rw-p 0000f000 03:01 1949734    /lib/libbz2.so.1.0.3
b6b42000-b6b43000 r-xp 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6b43000-b6b44000 rw-p 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6b44000-b6b45000 rw-p b6b44000 00:00 0 
b6b45000-b7392000 r-xp 00000000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b7392000-b73c7000 rwxp 0084d000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b73c7000-b73cb000 rwxp b73c7000 00:00 0 
b73cb000-b73cf000 r-xp 00000000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b73cf000-b73d0000 rw-p 00003000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b73d0000-b73f2000 r-xp 00000000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b73f2000-b73f3000 rw-p 00021000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b73f3000-b750a000 r-xp 00000000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b750a000-b7510000 rw-p 00116000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b7510000-b7540000 r-xp 00000000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b7540000-b7543000 rw-p 0002f000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b7543000-b7544000 rw-p b7543000 00:00 0 
b7544000-b7570000 r-xp 00000000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b7570000-b7573000 rw-p 0002b000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b7573000-b7574000 rw-p b7573000 00:00 0 
b7574000-b759e000 r-xp 00000000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b759e000-b759f000 rw-p 0002a000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b759f000-b75a1000 r-xp 00000000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b75a1000-b75a2000 rw-p 00001000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b75a2000-b75c0000 r-xp 00000000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b75c0000-b75c2000 rw-p 0001d000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b75c2000-b75d5000 r-xp 00000000 03:01 5507304    /usr/lib/libz.so.1.2.3
b75d5000-b75d6000 rw-p 00012000 03:01 5507304    /usr/lib/libz.so.1.2.3
b75d6000-b75d7000 rw-p b75d6000 00:00 0 
b75d7000-b763f000 r-xp 00000000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b763f000-b7642000 rw-p 00068000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b7642000-b777d000 r-xp 00000000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b777d000-b777e000 r--p 0013b000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b777e000-b7780000 rw-p 0013c000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7780000-b7783000 rw-p b7780000 00:00 0 
b7783000-b77a8000 r-xp 00000000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b77a8000-b77aa000 rw-p 00024000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b77aa000-b77ce000 r-xp 00000000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b77ce000-b77cf000 rw-p 00024000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b77cf000-b77e2000 r-xp 00000000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b77e2000-b77e4000 rw-p 00013000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b77e4000-b77e7000 rw-p b77e4000 00:00 0 
b77e7000-b7858000 r-xp 00000000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b7858000-b7872000 rwxp 00070000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b7872000-b7873000 rwxp b7872000 00:00 0 
b7873000-b7960000 r-xp 00000000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b7960000-b7964000 rw-p 000ed000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b7964000-b7969000 r-xp 00000000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b7969000-b796a000 rw-p 00004000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b796a000-b79d8000 r-xp 00000000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b79d8000-b79da000 rw-p 0006d000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b79da000-b7a6e000 r-xp 00000000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a6e000-b7a6f000 rw-p 00093000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a6f000-b7a71000 r-xp 00000000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a71000-b7a73000 rw-p 00001000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a73000-b7a74000 rw-p b7a73000 00:00 0 
b7a74000-b7a76000 r-xp 00000000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a76000-b7a77000 rw-p 00002000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a77000-b7ab0000 r-xp 00000000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7ab0000-b7ab1000 rw-p 00039000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7ab1000-b7ac7000 r-xp 00000000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ac7000-b7ac8000 rw-p 00015000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ac8000-b7af7000 r-xp 00000000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7af7000-b7af8000 rw-p 0002f000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7af8000-b7b34000 r-xp 00000000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7b34000-b7b36000 rw-p 0003b000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7b36000-b7b3d000 r-xp 00000000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b3d000-b7b3e000 rw-p 00007000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b3e000-b7b3f000 rw-p b7b3e000 00:00 0 
b7b3f000-b7b43000 r-xp 00000000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7b43000-b7b44000 rw-p 00003000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7b44000-b7b4c000 r-xp 00000000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7b4c000-b7b4d000 rw-p 00007000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7b4d000-b7b52000 r-xp 00000000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7b52000-b7b53000 rw-p 00005000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7b53000-b7b5a000 r-xp 00000000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7b5a000-b7b5b000 rw-p 00006000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7b5b000-b7b5d000 r-xp 00000000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7b5d000-b7b5e000 rw-p 00001000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7b5e000-b7b65000 r-xp 00000000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7b65000-b7b66000 rw-p 00006000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7b66000-b7b67000 rw-p b7b66000 00:00 0 
b7b67000-b7b74000 r-xp 00000000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b74000-b7b75000 rw-p 0000d000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b75000-b7b98000 r-xp 00000000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b98000-b7ba0000 rw-p 00023000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7ba0000-b7bb9000 r-xp 00000000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7bb9000-b7bbb000 rw-p 00018000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7bbb000-b7c3e000 r-xp 00000000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c3e000-b7c41000 rw-p 00083000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c41000-b7f92000 r-xp 00000000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f92000-b7f98000 rw-p 00351000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f98000-b7f99000 rw-p b7f98000 00:00 0 
b7f99000-b7f9c000 r-xp 00000000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f9c000-b7f9d000 rw-p 00002000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f9d000-b7f9e000 rw-p b7f9d000 00:00 0 
b7f9e000-b7f9f000 r--p 00000000 03:01 5571590    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f9f000-b7fa0000 r--p 00000000 03:01 5571587    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fa0000-b7fa1000 r--p 00000000 03:01 5571585    /usr/lib/locale/en_US.utf8/LC_NAME
b7fa1000-b7fa2000 r--p 00000000 03:01 5571579    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fa2000-b7fa3000 r--p 00000000 03:01 5571588    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fa3000-b7fa4000 r--p 00000000 03:01 5571583    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fa4000-b7fab000 r--s 00000000 03:01 5508729    /usr/lib/gconv/gconv-modules.cache
b7fab000-b7fac000 r--p 00000000 03:01 5571582    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fac000-b7fae000 rwxp 00000000 00:0d 2701       /dev/zero
b7fae000-b7faf000 rw-p b7fae000 00:00 0 
b7faf000-b7fc8000 r-xp 00000000 03:01 1949717    /lib/ld-2.5.so
b7fc8000-b7fca000 rw-p 00019000 03:01 1949717    /lib/ld-2.5.so
bff66000-bff7b000 rwxp bff66000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

anyway of doing this with out being root? I would like to add it to my session but i cant since it only runs under root :\

Also i get this message when im running it under root
```

root@XeN-desktop:/home/sableslayer# kiba-dock

** (kiba-dock:5910): WARNING **: Failed to make connection to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---


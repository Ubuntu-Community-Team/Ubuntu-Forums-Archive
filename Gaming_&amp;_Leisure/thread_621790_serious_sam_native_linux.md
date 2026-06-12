---
title: "serious sam native linux"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by go_beep_yourself on 2007-11-23
I am supposed to move files from the cd? Where are those instructions?

---

### Post by go_beep_yourself on 2007-11-24
I've tried with and without linux32. Any ideas how to get this working? I've been all over google trying to figure how to install Serious Sam for  Linux. I need instructons. If I had them, then I would RTFM.

```
chris@ubuntu:~/Desktop$ linux32 sh ./ssamtse-beta1.sh.bin 
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./ssamtse-beta1.sh.bin -check
 All good.
Uncompressing Serious Sam: The Second Encounter for GNU/Linux 1.07beta1tail: Warning: "+number" syntax is deprecated, please use "-n +number"
...
Second stage unpacker running...
Starting actual installer...
The setup program seems to have failed on x86/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)
chris@ubuntu:~/Desktop$ ldd ssamtse-beta1.sh.bin | grep not
        not a dynamic executable
chris@ubuntu:~/Desktop$ dpkg -l | grep ia32
ii  ia32-alsa-oss                          1.0.10-1                             32bit package for AMD64. ALSA wrapper for OS
ii  ia32-lib-firefox                       0.1                                  Libraries and other files to help 32bit Fire
ii  ia32-libs                              2.1ubuntu3                           ia32 shared libraries for use on amd64 and i
rc  ia32-libs-gtk                          25                                   gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                          12                                   KDE ia32 shared libraries for with OpenOffic
rc  ia32-libs-sdl                          1.0ubuntu3                           ia32 shared libraries of sdl related package
ii  ia32-sun-java6-bin                     6-03-0ubuntu2                        Sun Java(TM) Runtime Environment (JRE) 6 (32
chris@ubuntu:~/Desktop$ ls ../.32bitLibs
et-sdl-sound.so               libopenal.so.0          libQtXml.so.4              libwx_baseu_net-2.6.so.0
ld-2.5.so                     libopenal.so.0.0.0      libQtXml.so.4.2            libwx_baseu_net-2.6.so.0.3.1
ld-linux.so.2                 libphysfs-1.0.so.0      libQtXml.so.4.2.3          libwx_baseu_xml-2.6.so.0
libdbus-1.so.2                libphysfs-1.0.so.0.0.0  libSDL-1.3.so.0            libwx_baseu_xml-2.6.so.0.3.1
libdbus-1.so.3                libQtCore.so.4          libSDL_image-1.2.so.0      libwx_gtk2u_adv-2.6.so.0
libdbus-1.so.3.2.0            libQtCore.so.4.2        libSDL_image-1.2.so.0.1.4  libwx_gtk2u_adv-2.6.so.0.3.1
libgdkglext-x11-1.0.so.0      libQtCore.so.4.2.3      libsigc-2.0.so.0           libwx_gtk2u_core-2.6.so.0
libgdkglext-x11-1.0.so.0.0.0  libQtDBus.so.4          libsigc-2.0.so.0.0.0       libwx_gtk2u_core-2.6.so.0.3.1
libgtk-1.2.so.0               libQtDBus.so.4.2        libsmpeg-0.4.so.0          libwx_gtk2u_html-2.6.so.0
libgtk-1.2.so.0.9.1           libQtDBus.so.4.2.3      libsmpeg-0.4.so.0.1.4      libwx_gtk2u_html-2.6.so.0.3.1
libgtkglext-x11-1.0.so.0      libQtGui.so.4           libvorbisfile.so.3         libwx_gtk2u_qa-2.6.so.0
libgtkglext-x11-1.0.so.0.0.0  libQtGui.so.4.2         libvorbisfile.so.3.1.1     libwx_gtk2u_qa-2.6.so.0.3.1
libmad.so.0                   libQtGui.so.4.2.3       libvorbis.so.0             libwx_gtk2u_xrc-2.6.so.0
libmad.so.0.2.1               libQtNetwork.so.4       libvorbis.so.0.3.1         libwx_gtk2u_xrc-2.6.so.0.3.1
libogg.so.0                   libQtNetwork.so.4.2     libwx_baseu-2.6.so.0       libXss.so.1
libogg.so.0.5.3               libQtNetwork.so.4.2.3   libwx_baseu-2.6.so.0.3.1   libXss.so.1.0.0
chris@ubuntu:~/Desktop$ 
```

---

### Post by go_beep_yourself on 2007-11-24
Where on earth is the instructions to intall Serious Sam 1 or 2 or both?

---

### Post by go_beep_yourself on 2007-11-24
I have the same error, but with a different 32 bit game in 64 bit Linux.

I've tried with and without linux32. Any ideas how to get this working? I've been all over google trying to figure how to install Serious Sam for  Linux. I need instructons. If I had them, then I would RTFM.

```
chris@ubuntu:~/Desktop$ linux32 sh ./ssamtse-beta1.sh.bin 
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./ssamtse-beta1.sh.bin -check
 All good.
Uncompressing Serious Sam: The Second Encounter for GNU/Linux 1.07beta1tail: Warning: "+number" syntax is deprecated, please use "-n +number"
...
Second stage unpacker running...
Starting actual installer...
The setup program seems to have failed on x86/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)
chris@ubuntu:~/Desktop$ ldd ssamtse-beta1.sh.bin | grep not
        not a dynamic executable
chris@ubuntu:~/Desktop$ dpkg -l | grep ia32
ii  ia32-alsa-oss                          1.0.10-1                             32bit package for AMD64. ALSA wrapper for OS
ii  ia32-lib-firefox                       0.1                                  Libraries and other files to help 32bit Fire
ii  ia32-libs                              2.1ubuntu3                           ia32 shared libraries for use on amd64 and i
rc  ia32-libs-gtk                          25                                   gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                          12                                   KDE ia32 shared libraries for with OpenOffic
rc  ia32-libs-sdl                          1.0ubuntu3                           ia32 shared libraries of sdl related package
ii  ia32-sun-java6-bin                     6-03-0ubuntu2                        Sun Java(TM) Runtime Environment (JRE) 6 (32
chris@ubuntu:~/Desktop$ ls ../.32bitLibs
et-sdl-sound.so               libopenal.so.0          libQtXml.so.4              libwx_baseu_net-2.6.so.0
ld-2.5.so                     libopenal.so.0.0.0      libQtXml.so.4.2            libwx_baseu_net-2.6.so.0.3.1
ld-linux.so.2                 libphysfs-1.0.so.0      libQtXml.so.4.2.3          libwx_baseu_xml-2.6.so.0
libdbus-1.so.2                libphysfs-1.0.so.0.0.0  libSDL-1.3.so.0            libwx_baseu_xml-2.6.so.0.3.1
libdbus-1.so.3                libQtCore.so.4          libSDL_image-1.2.so.0      libwx_gtk2u_adv-2.6.so.0
libdbus-1.so.3.2.0            libQtCore.so.4.2        libSDL_image-1.2.so.0.1.4  libwx_gtk2u_adv-2.6.so.0.3.1
libgdkglext-x11-1.0.so.0      libQtCore.so.4.2.3      libsigc-2.0.so.0           libwx_gtk2u_core-2.6.so.0
libgdkglext-x11-1.0.so.0.0.0  libQtDBus.so.4          libsigc-2.0.so.0.0.0       libwx_gtk2u_core-2.6.so.0.3.1
libgtk-1.2.so.0               libQtDBus.so.4.2        libsmpeg-0.4.so.0          libwx_gtk2u_html-2.6.so.0
libgtk-1.2.so.0.9.1           libQtDBus.so.4.2.3      libsmpeg-0.4.so.0.1.4      libwx_gtk2u_html-2.6.so.0.3.1
libgtkglext-x11-1.0.so.0      libQtGui.so.4           libvorbisfile.so.3         libwx_gtk2u_qa-2.6.so.0
libgtkglext-x11-1.0.so.0.0.0  libQtGui.so.4.2         libvorbisfile.so.3.1.1     libwx_gtk2u_qa-2.6.so.0.3.1
libmad.so.0                   libQtGui.so.4.2.3       libvorbis.so.0             libwx_gtk2u_xrc-2.6.so.0
libmad.so.0.2.1               libQtNetwork.so.4       libvorbis.so.0.3.1         libwx_gtk2u_xrc-2.6.so.0.3.1
libogg.so.0                   libQtNetwork.so.4.2     libwx_baseu-2.6.so.0       libXss.so.1
libogg.so.0.5.3               libQtNetwork.so.4.2.3   libwx_baseu-2.6.so.0.3.1   libXss.so.1.0.0
chris@ubuntu:~/Desktop$ 
```

---

### Post by hikaricore on 2007-11-24
I am tired of this scattershot multiple posting on the same topic.
[B]
STOP IT.[/B]

---

### Post by Sockerdrickan on 2007-11-24
I sincerely agree with hikaricore. Please have more patience go_beep_yourself

---

### Post by SIXAXIS on 2008-02-16
Sorry to bring this back, but I installed Super Mario War on my 64-bit Ubuntu 7.10 system and it's giving me the error that libSDL_image-1.2.so.0 is the wrong type (it's 64-bit). Obviously SMW needs a 32 bit version. How do I aquire a 32-bit version that will work with 64-bit Gutsy Gibbons?

---

### Post by Sockerdrickan on 2008-02-16
> **SIXAXIS said:**
> Sorry to bring this back, but I installed Super Mario War on my 64-bit Ubuntu 7.10 system and it's giving me the error that libSDL_image-1.2.so.0 is the wrong type (it's 64-bit). Obviously SMW needs a 32 bit version. How do I aquire a 32-bit version that will work with 64-bit Gutsy Gibbons?

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---


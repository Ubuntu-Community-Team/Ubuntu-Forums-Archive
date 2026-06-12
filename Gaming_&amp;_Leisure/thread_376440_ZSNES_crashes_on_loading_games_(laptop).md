---
title: "ZSNES crashes on loading games (laptop)"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by ZeroXR on 2007-03-04
My project laptop was running ZSNES just fine until I was trying to fix the crackling sound playback on ZSNES.

The laptop does do direct rendering according to "glxinfo | grep rendering" syntax in Terminal.

Here's the output from the Terminal on the laptop:

```
   1.
      *** glibc detected *** zsnes: malloc(): memory corruption: 0x08607440 ***
   2.
      ======= Backtrace: =========
   3.
      /lib/tls/i686/cmov/libc.so.6[0xb7c031cd]
   4.
      /lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb7c0483f]
   5.
      /lib/tls/i686/cmov/libc.so.6[0xb7bf26af]
   6.
      /lib/tls/i686/cmov/libc.so.6(fopen+0x2c)[0xb7bf277c]
   7.
      zsnes[0x80dea54]
   8.
      ======= Memory map: ========
   9.
      08048000-082fa000 r-xp 00000000 03:01 3990069    /usr/bin/zsnes
  10.
      082fa000-0834d000 rwxp 002b1000 03:01 3990069    /usr/bin/zsnes
  11.
      0834d000-0861c000 rwxp 0834d000 00:00 0          [heap]
  12.
      b5300000-b5321000 rwxp b5300000 00:00 0
  13.
      b5321000-b5400000 ---p b5321000 00:00 0
  14.
      b54d7000-b54d8000 ---p b54d7000 00:00 0
  15.
      b54d8000-b5cd8000 rwxp b54d8000 00:00 0
  16.
      b5cd8000-b5cf8000 rwxs 00000000 00:08 884749     /SYSV0056a4d6 (deleted)
  17.
      b5cf8000-b5d08000 rwxs 00000000 00:0d 7348       /dev/snd/pcmC0D0p
  18.
      b5d08000-b5d11000 r-xp 00000000 03:01 1766358    /lib/tls/i686/cmov/libnss_files-2.4.so
  19.
      b5d11000-b5d13000 rwxp 00008000 03:01 1766358    /lib/tls/i686/cmov/libnss_files-2.4.so
  20.
      b5d13000-b5d1b000 r-xp 00000000 03:01 1766360    /lib/tls/i686/cmov/libnss_nis-2.4.so
  21.
      b5d1b000-b5d1d000 rwxp 00007000 03:01 1766360    /lib/tls/i686/cmov/libnss_nis-2.4.so
  22.
      b5d1d000-b5d2f000 r-xp 00000000 03:01 1766355    /lib/tls/i686/cmov/libnsl-2.4.so
  23.
      b5d2f000-b5d31000 rwxp 00011000 03:01 1766355    /lib/tls/i686/cmov/libnsl-2.4.so
  24.
      b5d31000-b5d33000 rwxp b5d31000 00:00 0
  25.
      b5d33000-b5d3a000 r-xp 00000000 03:01 1766356    /lib/tls/i686/cmov/libnss_compat-2.4.so
  26.
      b5d3a000-b5d3c000 rwxp 00006000 03:01 1766356    /lib/tls/i686/cmov/libnss_compat-2.4.so
  27.
      b5d3c000-b5d3d000 r-xp 00000000 03:01 4006700    /usr/lib/gconv/ISO8859-1.so
  28.
      b5d3d000-b5d3f000 rwxp 00001000 03:01 4006700    /usr/lib/gconv/ISO8859-1.so
  29.
      b5d3f000-b5d46000 r-xs 00000000 03:01 4006758    /usr/lib/gconv/gconv-modules.cache
  30.
      b5d46000-b5db7000 rwxp b5d46000 00:00 0
  31.
      b5db7000-b5e97000 rwxs 00000000 00:08 786443     /SYSV00000000 (deleted)
  32.
      b5e97000-b5e9b000 r-xp 00000000 03:01 3991157    /usr/lib/libXfixes.so.3.1.0
  33.
      b5e9b000-b5e9c000 rwxp 00003000 03:01 3991157    /usr/lib/libXfixes.so.3.1.0
  34.
      b5e9c000-b5ea4000 r-xp 00000000 03:01 3991147    /usr/lib/libXcursor.so.1.0.2
  35.
      b5ea4000-b5ea5000 rwxp 00007000 03:01 3991147    /usr/lib/libXcursor.so.1.0.2
  36.
      b5eaf000-b5ecb000 r-xp 00000000 03:01 4022730    /usr/lib/X11/locale/common/ximcp.so.2.0.0
  37.
      b5ecb000-b5ecd000 rwxp 0001b000 03:01 4022730    /usr/lib/X11/locale/common/ximcp.so.2.0.0
  38.
      b5ecd000-b5ecf000 r-xp 00000000 03:01 3991175    /usr/lib/libXrandr.so.2.0.0
  39.
      b5ecf000-b5ed0000 rwxp 00002000 03:01 3991175    /usr/lib/libXrandr.so.2.0.0
  40.
      b5ed2000-b5ed3000 rwxs 81000000 00:0d 7348       /dev/snd/pcmC0D0p
  41.
      b5ed3000-b5ed4000 r-xs 80000000 00:0d 7348       /dev/snd/pcmC0D0p
  42.
      b5ed4000-b5ed9000 r-xp 00000000 03:01 4022736    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
  43.
      b5ed9000-b5eda000 rwxp 00004000 03:01 4022736    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
  44.
      b5eda000-b5edb000 ---p b5eda000 00:00 0
  45.
      b5edb000-b7994000 rwxp b5edb000 00:00 0
  46.
      b7994000-b7998000 r-xp 00000000 03:01 3991151    /usr/lib/libXdmcp.so.6.0.0
  47.
      b7998000-b7999000 rwxp 00003000 03:01 3991151    /usr/lib/libXdmcp.so.6.0.0
  48.
      b7999000-b799b000 r-xp 00000000 03:01 3991142    /usr/lib/libXau.so.6.0.0
  49.
      b799b000-b799c000 rwxp 00001000 03:01 3991142    /usr/lib/libXau.so.6.0.0
  50.
      b799c000-b79a2000 r-xp 00000000 03:01 3991296    /usr/lib/libdrm.so.2.0.0
  51.
      b79a2000-b79a3000 rwxp 00005000 03:01 3991296    /usr/lib/libdrm.so.2.0.0
  52.
      b79a3000-b79a7000 r-xp 00000000 03:01 3991191    /usr/lib/libXxf86vm.so.1.0.0
  53.
      b79a7000-b79a8000 rwxp 00003000 03:01 3991191    /usr/lib/libXxf86vm.so.1.0.0
  54.
      b79a8000-b79b4000 r-xp 00000000 03:01 3991155    /usr/lib/libXext.so.6.4.0
  55.
      b79b4000-b79b5000 rwxp 0000c000 03:01 3991155    /usr/lib/libXext.so.6.4.0
  56.
      b79b5000-b7a7b000 r-xp 00000000 03:01 3991136    /usr/lib/libX11.so.6.2.0
  57.
      b7a7b000-b7a7e000 rwxp 000c5000 03:01 3991136    /usr/lib/libX11.so.6.2.0
  58.
      b7a7e000-b7a7f000 rwxp b7a7e000 00:00 0
  59.
      b7a7f000-b7a81000 r-xp 00000000 03:01 1766352    /lib/tls/i686/cmov/libdl-2.4.so
  60.
      b7a81000-b7a83000 rwxp 00001000 03:01 1766352    /libAborted (core dumped) 
```

I assume the corruption is the thing that is killing ZSNES, correct? Can someone help me fix my ZSNES? Even doing a "sudo aptitude remove zsnes" then reinstalling ZSNES doesn't remedy the problem either.

---

### Post by Phenax on 2007-03-04
[http://www.ubuntuforums.org/archive/index.php/t-295614.html](http://www.ubuntuforums.org/archive/index.php/t-295614.html)
Possible help.. There's a few things on Google too.

---

### Post by ZeroXR on 2007-03-05
Thanks for the archive...

It looks like building from source may be my only option, though play0r's post in that link mentions adding some missing code to .asoundrc to solve crackling sound and the crashing problem: 

```
pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}
```

The only thing is... I don't know where that file is! How do I go about finding the .asoundrc file? :(

---

### Post by Phenax on 2007-03-05
Probably in ~/.asoundrc (or /home/whatever/.asoundrc) either one works. It's a "Hidden file." so you can only see it with ls -A/ls -a or using a special option in your file browser.

---

### Post by ZeroXR on 2007-03-05
I'll probably give it another shot tomorrow... Rebuilding from source helped resolve the crash issue, now it's the crackling and popping that's bothersome. The laptop is away from things generating magnetic resonance and any other devices close by are magnetically shielded from generating magnetic resonance.

I would assume that I would go to Terminal and run the following commands:

cd home/(user name)/
ls -A
sudo gedit .asoundrc

Then in gedit, I would just paste in that piece of code?

---

### Post by ZeroXR on 2007-03-05
Can anyone verify this?

---

### Post by po0f on 2007-03-05
ZeroXR,

From a terminal:

```
$ echo -e 'pcm.!default {\n\ttype hw\n\tcard 0\n}\nctl.!default {\n\ttype hw\n\tcard 0\n}' | tee ~/.asoundrc
```

The above command will overwrite ~/.asoundrc if it exists.  What will be written to ~/.asoundrc will also be echoed to the terminal.  The single quotes are important.  Just copy-and-paste everything after the dollar sign and hit enter and you should be fine.  :)

---

### Post by ZeroXR on 2007-03-05
**po0f:** You sir, are a godsend... I tried so many other boards on this problem and they had so much more complicated methods other than that syntax you provided. The sound is nice and crisp on the laptop and it's as perfect as it is on my PC.

---

### Post by TheVelho on 2007-06-08
Thank you, po0f. This command solved my crackling sound problem. Thank you, thank you, thank you.

---


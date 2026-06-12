---
title: "Kega Fusion now available for Linux (but I can't get it to work)"
date: 2009-09-28
forum: Emulators
---

### Post by tghe-retford on 2009-09-28
Megadrive/Genesis/32X/Mega-CD (and pretty much the vast majority of pre 1995 Sega consoles) emulator Kega Fusion has been released as a pre-compiled binary for Linux. However, when I have downloaded it, it just isn't working, once you click onto the Kega Fusion window, it just segfaults. It is great to see this emulator finally released for Linux. Gerbilsoft has done some excellent work on Gens/GS but it was also nice to see this emulator, which I used extensively on Windows long ago (before I switched to (K)Ubuntu) finally ported to Linux, despite fears from some people that it would never have happened. I can now use Gens/GS and Kega alongside. :)

Just as an additional note to my problem, I am using this on a 64-bit system, and the Windows version of Kega Fusion used to work, but that now segfaults (different issue).

Any ideas?

Information: [http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

Thanks in advance.

---

### Post by mister_playboy on 2009-09-28
Kega is one of the few closed source free emulators... hence binary only.

I'll give it a try and report back.

EDIT: Well, it certainly doesn't run well out of the box, but I don't get instant segfaults, either.  Compiz needs to be turned off first to stop the picture from flickering wildly, and then it kept crashing when I was trying to configure my joypad.  Running it from the terminal stopped the crashing, and then everything looked and ran well, but the CD-audio part of the Sega CD game I was playing (Third World War) would not work... sound effects were working though... this in PulseAudio, by the way.  The Linux version does not allow direct from CD play, and I cannot confirm that I made a working image of the disc, so I'm not sure on the sound problem.

This is the a good first effort for Linux, I think.  The read me says something like "this is the first (and the last?) version for Linux", so I'm not sure what the future will bring.

Copy of the terminal output I got:
```
mister7playboy@VGN-NR430E:~/Downloads/Fusion$ ./Fusion
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
Segmentation fault
mister7playboy@VGN-NR430E:~/Downloads/Fusion$ ./Fusion
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
Segmentation fault
```

---

### Post by mister_playboy on 2009-09-29
I can confirm the image I made is good.  Loading the .bin part of the image makes the game run without CD-audio (but otherwise correctly) in both Linux and Windows.  Loading the .cue part of the image makes the game run correctly in Windows, but in Linux the game won't boot.

I'm using the same BIOS, game image, and settings on both platforms. :confused:

---

### Post by tghe-retford on 2009-09-29
I have tried with KWin switched off and on, and the problem remains.

This is about as far as I get. As soon as I click the window, bang - segfault:
```
(Fusion.exe:2881): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(Fusion.exe:2881): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
Segmentation fault (core dumped)
```
From /var/log/message:
```
Sep 29 19:08:30 TGHE kernel: [ 2893.623402] Fusion.exe[2863]: segfault at ffff8001 ip 00000000ffff8001 sp 00000000ffe8081c error 14
Sep 29 19:21:03 TGHE kernel: [ 2992.981175] Fusion.exe[2883]: segfault at ffff8019 ip 0000000008181203 sp 00000000f5198180 error 4
Sep 29 19:21:03 TGHE kernel: [ 3522.834002] Fusion.exe[3012]: segfault at ffff8019 ip 0000000008181203 sp 00000000f5148180 error 4
Sep 29 19:21:03 TGHE kernel: [ 3742.428534] Fusion.exe[3122]: segfault at ffff8009 ip 00000000f76ca148 sp 00000000fff6c18c error 6 in libc-2.10.1.so[f765c000+151000]
Sep 29 19:21:03 TGHE kernel: [ 3743.949041] Fusion.exe[3129]: segfault at ffff8009 ip 00000000f7673148 sp 00000000ffc5e4dc error 6 in libc-2.10.1.so[f7605000+151000]
```
Truly no idea of what is wrong...

---

### Post by mister_playboy on 2009-09-29
I posted over at the Kega Forums, and Snake advised me that the BIN/CUE problem would be a case-sensitive issue... sure enough, the file extension was .bin for the image, but .BIN in the CUE sheet... make sure they match! Kega couldn't see the files in load screen with the extension .BIN and .CUE, so they have to be called .bin and .cue.

I might also mention the Linux binary is name "Fusion.exe"... doubleclicking tries to extract .exes by default.  Rename it to "Fusion" and you can run it with doubleclicking. :)

So other than the segfault when I try to use my controller (I'm using the keyboard right now), it's all working perfectly for me whether from the terminal or Nautilus. :guitar:

Link to the Kega forum:
[COLOR="Red"][http://www.eidolons-inn.net/tiki-view_forum.php?forumId=10](http://www.eidolons-inn.net/tiki-view_forum.php?forumId=10)[/COLOR]

---

### Post by GerbilSoft on 2009-09-29
The "Wrong ELF Class" errors are caused by Kega trying to load 64-bit libraries instead of 32-bit libraries. (Kega's a 32-bit binary.) Unfortunately, I'm not sure how to tell it to load 32-bit libraries instead of 64-bit libraries.

---

### Post by mister_playboy on 2009-09-30
One related issue in the problem of using BIN/CUE or ISO/CUE in Linux... support for CUE files is very lacking natively.  The free Windows program ImgBurn can be used via WINE to make images for Kega Fusion.  WINE is even considered by the devs to be an officially supported platform!  :)

[[COLOR="DarkOrange"]Here is their site.[/COLOR]]("http://www.imgburn.com/")

---

### Post by Perfect Storm on 2009-09-30
> **GerbilSoft said:**
> The "Wrong ELF Class" errors are caused by Kega trying to load 64-bit libraries instead of 32-bit libraries. (Kega's a 32-bit binary.) Unfortunately, I'm not sure how to tell it to load 32-bit libraries instead of 64-bit libraries.

with getlibs: [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by mister_playboy on 2009-09-30
> **Artificial Intelligence said:**
> with getlibs: [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

aiming getlibs at the binary reports 
```
This application isn't missing any dependencies

```

I also tried
```
getlibs libcanberra-gtk-module.so libgvfsdbus.so libgioremote-volume-monitor.so libgiogconf.so
```
and installed those libs, but running Fusion gives the same errors.

---

### Post by Perfect Storm on 2009-09-30
can you please **ldd** the binary file and post the output.

---

### Post by tghe-retford on 2009-09-30
> **Artificial Intelligence said:**
> can you please **ldd** the binary file and post the output.
Output of ldd:
```
        not a dynamic executable
```

Still no movement on trying to get Kega Fusion to play nice. I've had some head-scratchers in the past, but this is a real puzzler as to why it doesn't work on my 64-bit install, yet can on others.

---

### Post by dfreer on 2009-09-30
It could be that the binary is compressed with UPX; I seem to remember a case where ldd wouldn't work until you decompressed the binary.

Beyond that, if getlibs fails, you could always try to manually install the 32-bit libs. Use packages.ubuntu.com, search for each library that your terminal tells you is missing, and hopefully it will work. 

I do think however that installing the 32-bit libs of GVFS will not be enough...

---

### Post by tghe-retford on 2009-09-30
> **dfreer said:**
> It could be that the binary is compressed with UPX; I seem to remember a case where ldd wouldn't work until you decompressed the binary.
I think I managed to decompress the library using upx (with the upx-ucl package) and got this output:

```
        linux-gate.so.1 =>  (0xf7f17000)               
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e37000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7dc5000)
        libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf79a4000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf799e000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf78bc000)          
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf78b3000)                  
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf77c0000)          
        libm.so.6 => /lib32/libm.so.6 (0xf7797000)                        
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf776a000)            
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7750000)            
        libc.so.6 => /lib32/libc.so.6 (0xf75f4000)                        
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf74c5000)                
        libdl.so.2 => /lib32/libdl.so.2 (0xf74c1000)                      
        libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf74a4000)
        libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf7401000)      
        libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf73b9000)          
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7374000)      
        libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf72af000)                
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf72ac000)            
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf623d000)                
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf623b000)    
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf622b000)                    
        libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf621e000)
        libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf621a000)        
        libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6216000)              
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6210000)
        libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf61f3000)
        libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf616c000)
        libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf60c1000)
        libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf6097000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6018000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf5feb000)
        libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf5fe6000)
        librt.so.1 => /lib32/librt.so.1 (0xf5fdd000)
        libpcre.so.3 => /lib32/libpcre.so.3 (0xf5faa000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf5f8f000)
        libuuid.so.1 => /lib32/libuuid.so.1 (0xf5f8a000)
        /lib/ld-linux.so.2 (0xf7f18000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf5f6c000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf5f62000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf5f56000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf5f4d000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf5f42000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5f3e000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf5f28000)
        libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf5ee0000)
        libdirectfb-1.2.so.0 => /usr/lib32/libdirectfb-1.2.so.0 (0xf5e66000)
        libfusion-1.2.so.0 => /usr/lib32/libfusion-1.2.so.0 (0xf5e5c000)
        libdirect-1.2.so.0 => /usr/lib32/libdirect-1.2.so.0 (0xf5e44000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf5e1c000)
        libxcb-render-util.so.0 => /usr/lib32/libxcb-render-util.so.0 (0xf5e16000)
        libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf5e0d000)
        libresolv.so.2 => /lib32/libresolv.so.2 (0xf5df7000)
        libselinux.so.1 => /lib32/libselinux.so.1 (0xf5dd9000)
        libexpat.so.1 => /lib32/libexpat.so.1 (0xf5db2000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf5dac000)
```

Getlibs for qtcurve did manage to remove those relevant error messages, now all I get now is when I click the window is this:
```
Segmentation fault (core dumped)
```

---

### Post by dfreer on 2009-09-30
Not much else we can do, you can try contacting the kega fusion developers.

---

### Post by mister_playboy on 2009-09-30
I spent two hours playing various games on Kega today, and everything worked very nicely.

Perhaps Snake will release a 64-bit version for us sometime to sort out the errors... guessing from the way he spoke about Linux, I think he has no real personal experience with it.

Best thing to do is ask him nicely. :popcorn:

---

### Post by tghe-retford on 2009-10-02
OK, even after the creator of Kega Fusion installed Kubuntu Karmic Koala himself to see if he could duplicate the error (and he couldn't), I reinstalled Karmic (since the beta is out and I wanted to start again with a clean slate) and it still segfaults when I click the window.

Something about Kega Fusion just hates my computer! :(

---

### Post by GSZX1337 on 2009-10-03
Yay! This kicks ***, finally, Linux has a good SMS emulator. :)

---

### Post by tghe-retford on 2009-10-03
I posted this to the developer, but luckily I managed to get a backtrace of the crash. Hope this is of help to someone:

```

*** glibc detected *** /home/sonic/Desktop/Fusion/Fusion: corrupted double-linked list: 0x0a0a4e90 ***
======= Backtrace: =========                                          
/lib32/libc.so.6[0xf7714cc1]                                          
/lib32/libc.so.6[0xf771806f]                                          
/lib32/libc.so.6(__libc_calloc+0xa9)[0xf7718d09]                      
/usr/lib32/libasound.so.2[0xf798abd6]                                 
/usr/lib32/libasound.so.2[0xf798ac96]                                 
/usr/lib32/libasound.so.2[0xf798d3ce]                                 
/usr/lib32/libasound.so.2[0xf798d7b2]                                 
/usr/lib32/libasound.so.2[0xf798dcd2]                                 
/usr/lib32/libasound.so.2[0xf798d842]                                 
/usr/lib32/libasound.so.2[0xf798ddc5]                                 
/usr/lib32/libasound.so.2(snd_config_update_r+0x1b2)[0xf7990d82]      
/usr/lib32/libasound.so.2(snd_config_update+0x48)[0xf79913f8]         
/usr/lib32/libasound.so.2(snd_pcm_open+0x39)[0xf79b7ee9]              
/home/sonic/Desktop/Fusion/Fusion[0x80c3693]                          
/home/sonic/Desktop/Fusion/Fusion[0x80c4059]                          
/home/sonic/Desktop/Fusion/Fusion[0x80844f4]                          
/home/sonic/Desktop/Fusion/Fusion[0x806d7fe]                          
/home/sonic/Desktop/Fusion/Fusion[0x80ba8ef]                          
/home/sonic/Desktop/Fusion/Fusion[0x80b8e62]                          
/home/sonic/Desktop/Fusion/Fusion[0x80b8f51]                          
/home/sonic/Desktop/Fusion/Fusion[0x816cafd]                          
/home/sonic/Desktop/Fusion/Fusion[0x80b7080]                          
/lib32/libc.so.6(__libc_start_main+0xe6)[0xf76bfb56]                  
/home/sonic/Desktop/Fusion/Fusion[0x8057a21]                          
======= Memory map: ========                                          
08048000-082c8000 r-xp 00000000 08:05 139186                             /home/sonic/Desktop/Fusion/Fusion                                  
082c8000-0846f000 rwxp 0027f000 08:05 139186                             /home/sonic/Desktop/Fusion/Fusion                                  
0846f000-085c9000 rwxp 00000000 00:00 0                               
09ff8000-0a24b000 rwxp 00000000 00:00 0                                  [heap]                                                             
f4a00000-f4a21000 rwxp 00000000 00:00 0                               
f4a21000-f4b00000 ---p 00000000 00:00 0                               
f4b0d000-f4b0e000 rwxp 00000000 00:00 0                               
f4b0e000-f4b0f000 ---p 00000000 00:00 0                               
f4b0f000-f530f000 rwxp 00000000 00:00 0                               
f530f000-f5310000 r-xp 00000000 08:05 135410                             /home/sonic/.Kega Fusion/Plugins/QuadRaw.rpi                       
f5310000-f5311000 rwxp 00000000 08:05 135410                             /home/sonic/.Kega Fusion/Plugins/QuadRaw.rpi                       
f5311000-f5312000 r-xp 00000000 08:05 139443                             /home/sonic/.Kega Fusion/Plugins/Double.rpi                        
f5312000-f5313000 rwxp 00000000 08:05 139443                             /home/sonic/.Kega Fusion/Plugins/Double.rpi                        
f5313000-f53d2000 r-xp 00000000 08:05 139441                             /home/sonic/.Kega Fusion/Plugins/hq4x.rpi                          
f53d2000-f53d3000 rwxp 000bf000 08:05 139441                             /home/sonic/.Kega Fusion/Plugins/hq4x.rpi                          
f53d3000-f5453000 rwxp 00000000 00:00 0                               
f5453000-f5454000 r-xp 00000000 08:05 139437                             /home/sonic/.Kega Fusion/Plugins/Scale2x.rpi                       
f5454000-f5455000 rwxp 00000000 08:05 139437                             /home/sonic/.Kega Fusion/Plugins/Scale2x.rpi                       
f5455000-f5457000 r-xp 00000000 08:05 139440                             /home/sonic/.Kega Fusion/Plugins/Scale3x.rpi                       
f5457000-f5458000 rwxp 00001000 08:05 139440                             /home/sonic/.Kega Fusion/Plugins/Scale3x.rpi                       
f5458000-f5459000 r-xp 00000000 08:05 139444                             /home/sonic/.Kega Fusion/Plugins/2xSaI.rpi                         
f5459000-f545a000 rwxp 00001000 08:05 139444                             /home/sonic/.Kega Fusion/Plugins/2xSaI.rpi                         
f545a000-f545b000 r-xp 00000000 08:05 139434                             /home/sonic/.Kega Fusion/Plugins/DoubleRaw.rpi                     
f545b000-f545c000 rwxp 00000000 08:05 139434                             /home/sonic/.Kega Fusion/Plugins/DoubleRaw.rpi                     
f545c000-f5492000 r-xp 00000000 08:05 139236                             /home/sonic/.Kega Fusion/Plugins/hq2x.rpi                          
f5492000-f5493000 rwxp 00036000 08:05 139236                             /home/sonic/.Kega Fusion/Plugins/hq2x.rpi                          
f5493000-f5513000 rwxp 00000000 00:00 0                               
f5513000-f5516000 r-xp 00000000 08:05 139438                             /home/sonic/.Kega Fusion/Plugins/MDNTSC.rpi                        
f5516000-f5517000 rwxp 00002000 08:05 139438                             /home/sonic/.Kega Fusion/Plugins/MDNTSC.rpi                        
f5517000-f5527000 rwxp 00000000 00:00 0                               
f5527000-f5528000 r-xp 00000000 08:05 139442                             /home/sonic/.Kega Fusion/Plugins/2xPM_LQ.rpi                       
f5528000-f5529000 rwxp 00000000 08:05 139442                             /home/sonic/.Kega Fusion/Plugins/2xPM_LQ.rpi                       
f5529000-f556f000 r-xp 00000000 08:05 139436                             /home/sonic/.Kega Fusion/Plugins/hq3x.rpi                          
f556f000-f5570000 rwxp 00046000 08:05 139436                             /home/sonic/.Kega Fusion/Plugins/hq3x.rpi                          
f5570000-f55f0000 rwxp 00000000 00:00 0                               
f55f0000-f55f2000 r-xp 00000000 08:05 139435                             /home/sonic/.Kega Fusion/Plugins/Scale4x.rpi                       
f55f2000-f55f3000 rwxp 00001000 08:05 139435                             /home/sonic/.Kega Fusion/Plugins/Scale4x.rpi                       
f55f3000-f55f8000 rwxp 00000000 00:00 0                               
f55f8000-f55fa000 r-xp 00000000 08:05 139439                             /home/sonic/.Kega Fusion/Plugins/2xPM.rpi                          
f55fa000-f55fb000 rwxp 00001000 08:05 139439                             /home/sonic/.Kega Fusion/Plugins/2xPM.rpi                          
f55fb000-f55fc000 r-xp 00000000 08:05 135409                             /home/sonic/.Kega Fusion/Plugins/Quad.rpi                          
f55fc000-f55fd000 rwxp 00000000 08:05 135409                             /home/sonic/.Kega Fusion/Plugins/Quad.rpi                          
f55fd000-f5777000 rwxp 00000000 00:00 0
f5777000-f5778000 ---p 00000000 00:00 0
f5778000-f5798000 rwxp 00000000 00:00 0
f5798000-f5998000 rwxs 4de65000 00:0f 5818                               /dev/nvidia0
f5998000-f599c000 rwxs 4de60000 00:0f 5818                               /dev/nvidia0
f599c000-f5a9c000 rwxs 4dca6000 00:0f 5818                               /dev/nvidia0
f5a9c000-f5aa0000 rwxs 4dcad000 00:0f 5818                               /dev/nvidia0
f5aa0000-f5aa1000 rwxs d0005000 00:0f 5818                               /dev/nvidia0
f5aa1000-f5aa2000 rwxs 4dcac000 00:0f 5818                               /dev/nvidia0
f5aa2000-f5aa6000 rwxs 4dc90000 00:0f 5818                               /dev/nvidia0
f5aa6000-f5aa7000 rwxs fac08000 00:0f 5818                               /dev/nvidia0
f5aa7000-f5ae7000 rwxs 52508000 00:0f 5818                               /dev/nvidia0
f5ae7000-f5b07000 rwxs 5259b000 00:0f 5818                               /dev/nvidia0
f5b07000-f5bd9000 rwxp 00000000 00:00 0
f5bd9000-f5c2a000 rwxp 00000000 00:0f 1681                               /dev/zero
f5c2a000-f5c60000 rwxp 00000000 00:00 0
f5c60000-f5c63000 rwxs 00000000 00:09 1736726                            /SYSV00000000 (deleted)Aborted (core dumped)
```

---

### Post by ZarathustraDK on 2009-10-08
Best emulator I've tried so far. Other emulators either skips frames or render the game too slow, and usually with audioglitches as well. Kega do all these things very nicely, in fact, some of the games actually run more smoothly than on the genesis itself (like when there's lots of stuff going on on the screen).

Only problem so far is missing mp3-audio in MegaCD-games. The files are correctly named, but I still get no audio. Think it's a pulseaudio thing or something. Normal audio is fine, it's only the mp3's.

---

### Post by tghe-retford on 2009-10-08
3.63x is now out, and whatever changes got made, Kega Fusion now works on my computer.

Problem I am seeing now is that VLC and Kega Fusion will not play nicely in terms of sound. If I want sound in Kega Fusion, I have to quit VLC (which I use for digital TV, whilst interlacing options are missing from Kaffeine).

And MP3 playback does not work for Mega CD either, even though I downloaded the 32-bit libmpg123.so using getlibs and edited ~/.Kega Fusion/Fusion.ini to:
```
libmpg123path=/usr/lib32/libmpg123.so
```
as stated in the readme.

EDIT: If you have the disc space, you can always convert the MP3 files to WAV and they will work, as long as you keep the filenames the same.

---

### Post by Xcursion666 on 2010-11-05
i got my copy from here  [http://www.zophar.net/linux/sms-gg/kega-fusion.html](http://www.zophar.net/linux/sms-gg/kega-fusion.html) it ran fine i had no problems with it it ran every game i had  (over 500 games)

---

### Post by Floomer999 on 2012-03-03
Downloaded Kega Fusion to try it out on Ubuntu 11.10, but when I load up the application it won't open.  It just gives me a blank screen.  No menu or anything.  What is going on?

---

### Post by Soulcage on 2012-03-04
Run it from the terminal and see what it says. You're probably missing a package.

---


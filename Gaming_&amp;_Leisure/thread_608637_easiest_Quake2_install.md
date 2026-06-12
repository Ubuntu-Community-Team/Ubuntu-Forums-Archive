---
title: "easiest Quake2 install"
date: 2007-11-10
forum: Gaming &amp; Leisure
---

### Post by myname on 2007-11-10
Hey all,

I found my backup Quake 2 (version 3.20) install for windows, which has all my configuration settings, maps and skins.

What is the easiest way to install Q2 for Linux, which would use this install and allow me to connect to people running Quake 2 v.3.20 for windows.  Which installer should I use (synaptic, Loki, build from ID's site)?  

Any help would be greatly appreciated, as I'm in the dire need for some fragging fun.

--kevin

---

### Post by mbradlcu on 2007-11-11
you may want to check out the apt packaged version of quake2. I believe it's just the binaries and expects the assets to be copied over from the disk,, in your case this would be perfect.

---

### Post by myname on 2007-11-11
Since  already had the Windows install of Quake2, I followed the method on this page: 
```

http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html#quake2-linux-binaries

```
The "Windows to Linux install" section.

and then the "Adding the Binaries" section.

Since  am on Gutsy, I used the following binary:
a libc5 tar.gz package

and then rand the following code:

```

     cd ~/games/quake2
     sudo  tar -xzf quake2-3.20-i386-unknown-linux2.0.tar.gz

```

When I try to run quake2 with ./quake2, I get the following:

> 
~/games/quake2$ ./quake2
bash: ./quake2: No such file or directory


anyone know why?  Does this method still work?

--Kevin

---

### Post by aoanla on 2007-11-11
Hrm. If there genuinely is a quake2 binary in that directory, have you tried

chmod +x ./quake2

and then executing it? It's possible that it doesn't have execute permissions, so the shell is (obtusely) refusing to treat it as a program.

---

### Post by myname on 2007-11-11
been working with this more.  

I followed the instructions here:
```

https://help.ubuntu.com/community/Games/Native/Quake2#head-68e1f6f3814b9434d756f2426757732274863e9a

```

and I am now getting this:

```

:~/games/quake2$ ./quake2 +set vid_ref gl +set gl_driver lib3dfxgl.so 
Added packfile ./baseq2/pak0.pak (3307 files)
Added packfile ./baseq2/pak1.pak (279 files)
Added packfile ./baseq2/pak2.pak (2 files)
Added packfile ./baseq2/pak7.pak (164 files)
Added packfile ./baseq2/pak9.pak (1 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_gl.so -------
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
ref_gl version: GL 0.01
libglide2x.so: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "lib3dfxgl.so"
------- Loading ref_soft.so -------
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
Using VESA driver, 16384KB. VBE3
svgalib 1.4.3
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
svgalib: Failed to initialize mouse.
mode 320: 200 -1211791804
mode 320: 240 -1211791804
mode 320: 400 -1211791804
mode 360: 480 -1211791804
mode 640: 480 -1211791804
mode 800: 600 -1211791804
mode 1024: 768 -1211791804
mode 640: 400 -1211791804
setting mode 0: 320 240
svgalib: can't open /dev/tty0 

```

any ideas?

--Kevin

---

### Post by aoanla on 2007-11-11
> **myname said:**
> been working with this more.  

I followed the instructions here:
```

https://help.ubuntu.com/community/Games/Native/Quake2#head-68e1f6f3814b9434d756f2426757732274863e9a

```

and I am now getting this:

```

:~/games/quake2$ ./quake2 +set vid_ref gl +set gl_driver lib3dfxgl.so 
Added packfile ./baseq2/pak0.pak (3307 files)
Added packfile ./baseq2/pak1.pak (279 files)
Added packfile ./baseq2/pak2.pak (2 files)
Added packfile ./baseq2/pak7.pak (164 files)
Added packfile ./baseq2/pak9.pak (1 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_gl.so -------
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
ref_gl version: GL 0.01
libglide2x.so: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "lib3dfxgl.so"
------- Loading ref_soft.so -------
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
Using VESA driver, 16384KB. VBE3
svgalib 1.4.3
You must be the owner of the current console to use svgalib.
Not running in a graphics capable console,
and unable to find one.
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
svgalib: Failed to initialize mouse.
mode 320: 200 -1211791804
mode 320: 240 -1211791804
mode 320: 400 -1211791804
mode 360: 480 -1211791804
mode 640: 480 -1211791804
mode 800: 600 -1211791804
mode 1024: 768 -1211791804
mode 640: 400 -1211791804
setting mode 0: 320 240
svgalib: can't open /dev/tty0 

```

any ideas?

--Kevin

Well, the logs suggest that the engine is expecting 3dfx drivers (which, of course, you don't have, because 3dfx were acquired by nVidia some years back now), and isn't looking for the actual OpenGL drivers you do have. You don't want to set your gl_driver as lib3dfxgl.so - try libGL.so instead?

---

### Post by myname on 2007-11-11
tried it, the same results.

It appears that the only version of quake I can get running is the one from the repositories.  Evidently, following the instructions didn't do it, the Loki installer didn't work.  Crap. 

Is the one from the repos compatible with 3.20 for Windows?

--kevin

---

### Post by mbradlcu on 2007-11-12
hey,, myname
I did the same as you're attempting, I had a backup copy of a fully patched q2 with a bunchO mods.. I'm thinking I'll put up the binaries and what ever config files on my server and you can just DL them.  [http://qndfix.com/pub/q2/](http://qndfix.com/pub/q2/)  ... there's also q2-coop server, it's pretty fun. please let me know if you have any problems with it..

---

### Post by mbradlcu on 2007-11-12
Hi again myname,
thought I'd keep the info public for my reference too... the q2 I used was from an old windows install that I backed up a long time ago, I just used the icculs binaries. the ones I put up on my site.

---


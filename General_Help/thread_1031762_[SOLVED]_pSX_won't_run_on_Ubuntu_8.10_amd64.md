---
title: "[SOLVED] pSX won't run on Ubuntu 8.10 amd64"
date: 2009-01-05
forum: General Help
---

### Post by thegreenblob on 2009-01-05
Hello, I'm trying to get a ps1 emu working under 64 bit ubuntu and it is not working...

I downloaded pSX and tried running it but get the following:

```
joe@desktop:~/Desktop/pSX$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
joe@desktop:~/Desktop/pSX$ 

```

But I cannot find anything in synaptic that matches that.

And I also tried PCSX, it ran but when trying to start up a game is just disappears.

So, any help here?

---

### Post by ju2wheels on 2009-01-05
```

sudo apt-get install libgtkglext1

```

---

### Post by thegreenblob on 2009-01-06
Just tried that and it says it's already installed. :(

```
joe@desktop:~$ sudo apt-get install libgtkglext1
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtkglext1 is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2ldbl libfltk1.1 libgtk1.2-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@desktop:~$
```

---

### Post by ju2wheels on 2009-01-06
Could you post the output of:

```

file pSX
ldd pSX

```

It sounds like it may be looking for 32bit libs instead of the 64bit ones. In that case you may need to use getlibs to satisfy the 32bit dependencies.

---

### Post by thegreenblob on 2009-01-06
Here ya go:

```
joe@desktop:~/Emulators/pSX$ file pSX
pSX: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.9, dynamically linked (uses shared libs), stripped
joe@desktop:~/Emulators/pSX$ ldd pSX
	linux-gate.so.1 =>  (0xf7f76000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7ebd000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7ea7000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7dde000)
	libgtkglext-x11-1.0.so.0 => not found
	libgdkglext-x11-1.0.so.0 => not found
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7d6d000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7d57000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d05000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7cfc000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7ce4000)
	libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7cd7000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7cd1000)
	librt.so.1 => /lib32/librt.so.1 (0xf7cc8000)
	libglade-2.0.so.0 => /usr/lib32/libglade-2.0.so.0 (0xf7cb0000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf7912000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf77d6000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf774a000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf772e000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf7713000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf7708000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf76c5000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf7652000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7614000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf760f000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf760a000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7553000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7465000)
	libm.so.6 => /lib32/libm.so.6 (0xf743f000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7430000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7417000)
	libc.so.6 => /lib32/libc.so.6 (0xf72b8000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6546000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6544000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6535000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6446000)
	/lib/ld-linux.so.2 (0xf7f77000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf641d000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf63b5000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf633f000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6312000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf630e000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf630a000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6305000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf62fb000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf62f8000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf62ee000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf62e6000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf62dd000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf629b000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6275000)
	libxcb-render-util.so.0 => /usr/lib32/libxcb-render-util.so.0 (0xf6270000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf6267000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf624e000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6224000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6221000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf621e000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf6203000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf61dc000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf61d7000)
joe@desktop:~/Emulators/pSX$
```

---

### Post by ju2wheels on 2009-01-06
Ok so yes, it is definitely a 32bit app and you are missing the 32bit libs (although apparently you do have the 64bit libs it will not use those).

So install the following package: [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

Then run:
```

getlibs pSX

```

After installing the relevant 32bit packages try pSX again.

---

### Post by thegreenblob on 2009-01-06
Well... did that. And the language selection screen came up. When I clicked ok it got a Segmentation fault x_x

```
joe@desktop:~/Emulators/pSX$ ./pSX

(pSX:10291): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libnodoka.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
joe@desktop:~/Emulators/pSX$
```

edit: When running as root it gets a little farther (bios selection), but when I select them it gets a similar error...

```
joe@desktop:~/Emulators/pSX$ sudo ./pSX

(pSX:10332): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libnodoka.so: wrong ELF class: ELFCLASS64

(pSX:10332): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libnodoka.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(pSX:10332): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10332): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10332): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10332): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10332): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10332): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10332): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10332): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
joe@desktop:~/Emulators/pSX$
```

---

### Post by ju2wheels on 2009-01-06
Im not familiar with using pSX, but from this string: "ELFCLASS64" I can only assume its still having 64bit compatibility issues with some libraries. I would check if pSX has any support forum or mailing list and ask there...

---

### Post by thegreenblob on 2009-01-06
I seem to have solved it with this post: [http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=2998](http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=2998)

Ran it with his script and it seems to work. (Though sound seemed to have stopped working for banshee x_x, oh well it works for the game I'm playing)

---

### Post by dael99 on 2009-12-28
also we need to
$ getlibs -p libgtkglext1

and we are in FF!!

---


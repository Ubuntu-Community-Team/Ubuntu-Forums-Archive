---
title: "Firefox 1.5 say it is missing libgtk-x11-2.0.so.0"
date: 2005-12-12
forum: General Help
---

### Post by Vantskruv on 2005-12-12
After I've download Fiirefox 1.5 and unpacked in the folder /opt. I'm trying to run it but this message comes up:

johannes@LGJB:/opt/firefox$ ./firefox
./firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I got a tip to use the ldd command for firefox-bin, the output looks like this:

johannes@LGJB:/opt/firefox$ ldd firefox-bin
        linux-gate.so.1 =>  (0xffffe000)
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => not found
        libplc4.so => not found
        libnspr4.so => not found
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x5557d000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5558e000)
        libgtk-x11-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libatk-1.0.so.0 => not found
        libgdk_pixbuf-2.0.so.0 => not found
        libpangoxft-1.0.so.0 => not found
        libpangox-1.0.so.0 => not found
        libpango-1.0.so.0 => not found
        libgobject-2.0.so.0 => not found
        libgmodule-2.0.so.0 => not found
        libglib-2.0.so.0 => not found
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x55593000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55653000)
        libsmime3.so => not found
        libssl3.so => not found
        libnss3.so => not found
        libsoftokn3.so => not found
        libXrender.so.1 => not found
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x55676000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x556e0000)
        libxpcom_compat.so => not found
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x5572f000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x557e9000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x557f4000)
        libXft.so.2 => not found
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x55923000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55951000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55954000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55958000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x5596c000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x55974000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x5598d000)


It seems many files are missing. How do I install them?
And I don't find any  libgtk-x11-2.0.so.0 in Adept-manager, and I've libgtk2.0-0 installed.

Help!

:???:

---

### Post by daller on 2005-12-12
Have you tried installing "libgtk1.2" and "libgtk1.2-dev"?

---

### Post by Vantskruv on 2005-12-12
Yes, still doesn't work. I've tried to fix a little with the script files "run-mozilla.sh" and "firefox" but nothing helps (and I'm also very bad on it).

Are there no install command for the Firefox? I just unpacked it in the folder.

Note that I'm using Kubuntu, but I don't think it is a big difference compared with Ubuntu.

---

### Post by daller on 2005-12-12
Is there a reason why you compile it, instead of installing "firefox"

```
sudo apt-get install firefox
```

---

### Post by schilcha on 2005-12-12
Check if you can find libgtk-x11-2.0.so.0 in /usr/lib. If so either: 

*) add /usr/lib to your LD_LIBRARY_PATH environment variable

or

*) add /usr/lib to your /etc/ld.so.conf

Good Luck

---

### Post by mo_x on 2005-12-12
Are you trying to run Firefox for i686 on x86-64 ?

---

### Post by Vantskruv on 2005-12-12
I've already tried what you told me.

And yes, I'm using Firefox for i686 on x86-64...

---

### Post by mo_x on 2005-12-12
[QUOTE=Vantskruv]I've already tried what you told me.

And yes, I'm using Firefox for i686 on x86-64...[/QUOTE]
That is not going to work. You need a 32 bit chroot for that.
I compiled firefox 1.5 from source on x86-64 but that was not really easy.
There still don't seem to be any offical x86-64 build available.

---

### Post by Vantskruv on 2005-12-12
Yep! I downloaded the 32-bit distribution and now it works! Phew, what heck a of a struggle, but I've learned much in the way.:p

---


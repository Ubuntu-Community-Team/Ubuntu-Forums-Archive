---
title: "Missing Steam Libraries"
date: 2016-12-20
forum: Gaming &amp; Leisure
---

### Post by oblivion12 on 2016-12-20
[B]Steam was working fine before I turned off my computer, then came back to turn it on.
When I attempt to open steam now I get these.[/B]
[B]
You are missing the following 32-bit libraries, and Steam may not run:
libv8.so
libSDL2-2.0.so.0
libXtst.so.6
libgobject-2.0.so.0
libglib-2.0.so.0
libgtk-x11-2.0.so.0
libpulse.so.0
libgdk_pixbuf-2.0.so.0
libavcodec.so.56
libavformat.so.56
libavresample.so.2
libavutil.so.54
libswscale.so.3


Anyway to work around for this or any fixes?
 
Done Raccoon's Post. 

All I get is "Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."
[/B]

---

### Post by oldrocker99 on 2016-12-20
Did you enter this? ```
sudo apt-get -f install
```

When you're posting terminal output, please surround it with (in brackets--[]) **code** at the beginning and **/code** at the end.

---

### Post by oblivion12 on 2016-12-21
[B]Ok when I did 

```
sudo apt-get -f install
```

I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libstdc++-5-dev
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 177 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,262 kB of archives.
After this operation, 6,936 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 262044 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu5) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu5
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
oblivion12@AnonHFUser:~$ 

When I attempted to open Steam everything booted up but still said I was missing all the was libraries as before.


[/B]

---

### Post by oblivion12 on 2016-12-21
[B]I found this code that helped me 

```
 find ~/.steam/root/ \( -name "libgcc_s.so*" -o -name "libstdc++.so*" -o -name "libxcb.so*" -o -name "libgpg-error.so*" \) -print -delete 
```

This doesn't look like it does anything, but I went to open steam and it opened perfectly.
[/B]

---

### Post by oldrocker99 on 2016-12-22
Where'd you find the code? If your problem is solved, please use the Thread tools to mark this thread as [SOLVED].

---


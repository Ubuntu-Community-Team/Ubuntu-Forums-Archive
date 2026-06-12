---
title: "error with &quot;./configure&quot;"
date: 2008-12-27
forum: General Help
---

### Post by Jakey_TheSnake on 2008-12-27
I get the following when I use the ./configure command:

checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Please help me with that.
thanks

---

### Post by didac on 2008-12-27
> **Jakey_TheSnake said:**
> I get the following when I use the ./configure command:

checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Please help me with that.
thanks

Either the development files for gtk+-2.0 haven't been installed, or they have been installed in the local directory. You should find gtk+-2.0.pc in /usr/lib/pkgconfig, while maybe it is in /usr/local/lib/pkgconfig

---

### Post by kevdog on 2008-12-27
apt-cache is your friend

Try 

sudo aptitude install libglib2.0-dev


That should be one package.

---

### Post by xiaosilent on 2008-12-27
you should install the dev. libs of glib and gtk.

---

### Post by Jakey_TheSnake on 2008-12-28
> **kevdog said:**
> apt-cache is your friend

Try 

sudo aptitude install libglib2.0-dev


That should be one package.

Done, didn't fix. 

Tried the local thing too, it wasn't there so that's not the problem. I do have several files with "gtk-2.0.pc" in the title, such as "gtk-sharp-2.0.pc", but none "gtk+-2.0.pc". 

To the above poster, could you please tell me which in particular? Or what to search for in Synaptic and install all. 

If all else fails someone could always upload the file?

---

### Post by snova on 2008-12-28
Install the 'libgtk2.0-dev' package.

What are you trying to install?

---

### Post by Jakey_TheSnake on 2008-12-29
Airsnort. 

I have installed the package and ./configure now works, but whilst making I get this (sorry for long code output):

```
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from callbacks.c:24:
PacketSource.h:153: error: expected specifier-qualifier-list before ‘pcap_t’
PacketSource.h:178: warning: ‘struct pcap_pkthdr’ declared inside parameter list
PacketSource.h:178: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:179: warning: ‘struct pcap_pkthdr’ declared inside parameter list
callbacks.c:79: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
callbacks.c: In function ‘savePacketData’:
callbacks.c:562: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:563: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:566: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:568: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:569: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:574: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:575: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:576: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:581: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:582: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:583: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:584: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
callbacks.c:586: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/jake/Documents/untitled folder/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jake/Documents/untitled folder/airsnort-0.2.7e'
make: *** [all] Error 2

```

I have absolutely no idea what to do at this point.

---

### Post by kevdog on 2008-12-29
Where did you grab these sources so I can try to compile them?

---

### Post by ajcham on 2008-12-29
From the [Airsnort homepage:]("http://airsnort.shmoo.com/")

[QUOTE=http://airsnort.shmoo.com]

**This software is OLD**
It is no longer maintained or supported. Besides, there are much better tools out there. You really should be trying something like [aircrack-ng]("http://www.aircrack-ng.org/doku.php"). [/QUOTE]

The last release was 4 years ago.

PS. I hope you are using this software for testing purposes, rather than more nefarious motives.

---

### Post by ibuclaw on 2008-12-29
You could try using [wireshark]("apt:wireshark") if you want to monitor your network...

Regards
Iain

---


---
title: "Installing cdEMU in Ubuntu 8.10"
date: 2008-12-31
forum: General Help
---

### Post by geyids on 2008-12-31
Happy New Years Ubuntus.

I have a prob installing cdEMU, I go to the download page [here]("http://sourceforge.net/project/showfiles.php?group_id=93175&package_id=296278&release_id=635207") and I get the list and i'm confused. I download the ones for Ubuntu 8.10. but not all are installed. says missing a certain package. e.g when I install cdEmu-daemon, says ```
No package 'glib-2.0' found
```
Please help

---

### Post by taurus on 2008-12-31
Which one did you download?

---

### Post by geyids on 2008-12-31
> **taurus said:**
> Which one did you download?

I started with cdemu-daemon_1.1.0.orig.tar.gz then after it didnt finish compiling, I thought glib-2.0 was in the other packages but still doesnt work. I only know to work with tar.gz

---

### Post by taurus on 2008-12-31
If you want to compile it from source, you need to install the developing package for glib.  Open synaptic and search for glib-2.0.  In there, you would see a package called libglib2.0-dev.  That's the one you need.  So install it and try to run the ./configure command again.

---

### Post by geyids on 2008-12-31
I have installed, asked for 'dbus-1' and 'dbus-glib-1', I have installed now its asking for 'ao'
```
checking for dbus... yes
checking for libao... configure: error: Package requirements (ao >= 0.8.0) were not met:

No package 'ao' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libao_CFLAGS
and libao_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by albinootje on 2008-12-31
[QUOTE=geyids;6468415]I have installed, asked for 'dbus-1' and 'dbus-glib-1', I have installed now its asking for 'ao'
```
checking for dbus... yes
checking for libao... configure: error: Package requirements (ao >= 0.8.0) were not met:

```
$ apt-cache search libao|grep dev
libao-dev - Cross Platform Audio Output Library Development

$ apt-cache show libao-dev|grep -i version
Version: 0.8.8-4

---

### Post by taurus on 2008-12-31
Look for libao2 & libao-dev.

---

### Post by geyids on 2009-01-01
I've understood how these works now. Is there a way to check for all the needed softwares so that I dont have to install one after another? These is because its asking for one depedency after another and I want to download them all at once.

Thanks you all for your responses and HAPPY NEW YEAR

---

### Post by geyids on 2009-01-01
I made it to compile. now when I make, I get these error
```
In file included from /usr/local/include/libmirage-1.0/mirage.h:47,
                 from cdemud.h:44,
                 from cdemud-daemon.c:20:
/usr/local/include/libmirage-1.0/mirage-disc-structures.h:24:1: warning: this is the location of the previous definition
cdemud-daemon.c:33: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
cdemud-daemon.c:43: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
cdemud-daemon.c: In function &#8216;__cdemud_daemon_io_handler&#8217;:
cdemud-daemon.c:154: error: &#8216;struct vhba_request&#8217; has no member named &#8216;cdb&#8217;
cdemud-daemon.c:154: error: &#8216;struct vhba_request&#8217; has no member named &#8216;cdb_len&#8217;
cdemud-daemon.c:155: error: &#8216;struct vhba_request&#8217; has no member named &#8216;cdb_len&#8217;
cdemud-daemon.c:156: error: &#8216;struct vhba_request&#8217; has no member named &#8216;cdb_len&#8217;
cdemud-daemon.c:156: error: &#8216;struct vhba_request&#8217; has no member named &#8216;cdb_len&#8217;
cdemud-daemon.c:160: error: &#8216;struct vhba_request&#8217; has no member named &#8216;data_len&#8217;
cdemud-daemon.c:166: error: &#8216;struct vhba_response&#8217; has no member named &#8216;tag&#8217;
cdemud-daemon.c:166: error: &#8216;struct vhba_request&#8217; has no member named &#8216;tag&#8217;
cdemud-daemon.c:167: error: &#8216;struct vhba_response&#8217; has no member named &#8216;status&#8217;
cdemud-daemon.c:169: error: &#8216;struct vhba_response&#8217; has no member named &#8216;data_len&#8217;
cdemud-daemon.c:148: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
cdemud-daemon.c:171: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
make[3]: *** [cdemud-daemon.o] Error 1
make[3]: Leaving directory `/home/john/Downs/cdemu-daemon-1.1.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/john/Downs/cdemu-daemon-1.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/Downs/cdemu-daemon-1.1.0'
make: *** [all] Error 2

```

whats could be the problem

---

### Post by albinootje on 2009-01-01
There are precompiled cdemu packages here :
[http://cdemu.sourceforge.net/project.php#binary](http://cdemu.sourceforge.net/project.php#binary)

---


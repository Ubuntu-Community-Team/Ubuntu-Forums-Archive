---
title: "Unsolvable Opera and Java Errors"
date: 2005-11-01
forum: Desktop Environments
---

### Post by brisamrus on 2005-11-01
Hello All,

I'm new to Ubuntu Breezy and have had a difficult time getting Opera 8.5 to recognize I've got Java installed (jre-1_5_0_05-linux-i586) on my system. I've followed all the instruction on the Ubuntu OperaBrowser page ([https://wiki.ubuntu.com/OperaBrowser)](https://wiki.ubuntu.com/OperaBrowser)), and I've tried each of the different ways listed for installing Opera found there with no luck. I still get the startup errors when I start Opera through the terminal too...

> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

Opera and Java both installed fine. Opera just can't seem to find Java in the JRE default directory, or anywhere else for that matter.

Anyone heard of, or experienced, similar problems and found a solution. Thanks.

---

### Post by Xian on 2005-11-01
Let's get a two bits of info and then we can proceed. I'm going to assume that you don't have slocate installed in the instructions below (but if you do then you can skip the install step). Otherwise just please post the info requested in steps 1 & 2.

```
$ sudo apt-get install slocate
```
```
$ sudo updatedb
```

1. Copy/Paste the output of this command:

```
$ locate lib/i386
```

2. Copy/Paste the text in the box (in Opera) from:
Tools > Preferences > Advanced > Content > Java Options > Java Path

---

### Post by brisamrus on 2005-11-01
Thanks for the help.

I did as you suggested. slocate was already installed so I ran

> $ sudo updatedb

Here are the results of runing "locate lib/i386"

> /usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre/lib/i386
/usr/lib/j2re1.5-sun/lib/i386
/usr/lib/j2re1.5-sun/lib/i386/libnative_chmod.so
/usr/lib/j2re1.5-sun/lib/i386/native_threads
/usr/lib/j2re1.5-sun/lib/i386/native_threads/libhpi.so
/usr/lib/j2re1.5-sun/lib/i386/server
/usr/lib/j2re1.5-sun/lib/i386/server/libjvm.so
/usr/lib/j2re1.5-sun/lib/i386/server/Xusage.txt
/usr/lib/j2re1.5-sun/lib/i386/server/libjsig.so
/usr/lib/j2re1.5-sun/lib/i386/libdeploy.so
/usr/lib/j2re1.5-sun/lib/i386/client
/usr/lib/j2re1.5-sun/lib/i386/client/libjvm.so
/usr/lib/j2re1.5-sun/lib/i386/client/Xusage.txt
/usr/lib/j2re1.5-sun/lib/i386/client/classes.jsa
/usr/lib/j2re1.5-sun/lib/i386/client/libjsig.so
/usr/lib/j2re1.5-sun/lib/i386/libzip.so
/usr/lib/j2re1.5-sun/lib/i386/jvm.cfg
/usr/lib/j2re1.5-sun/lib/i386/libjavaplugin_jni.so
/usr/lib/j2re1.5-sun/lib/i386/libjsig.so
/usr/lib/j2re1.5-sun/lib/i386/libj2pkcs11.so
/usr/lib/j2re1.5-sun/lib/i386/libverify.so
/usr/lib/j2re1.5-sun/lib/i386/libjavaplugin_nscp.so
/usr/lib/j2re1.5-sun/lib/i386/libjava.so
/usr/lib/j2re1.5-sun/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/j2re1.5-sun/lib/i386/libjava_crw_demo.so
/usr/lib/j2re1.5-sun/lib/i386/libhprof.so
/usr/lib/j2re1.5-sun/lib/i386/libnet.so
/usr/lib/j2re1.5-sun/lib/i386/libnio.so
/usr/lib/j2re1.5-sun/lib/i386/libmanagement.so
/usr/lib/j2re1.5-sun/lib/i386/libinstrument.so
/usr/lib/j2re1.5-sun/lib/i386/libjsound.so
/usr/lib/j2re1.5-sun/lib/i386/libjsoundalsa.so
/usr/lib/j2re1.5-sun/lib/i386/libmlib_image.so
/usr/lib/j2re1.5-sun/lib/i386/libdcpr.so
/usr/lib/j2re1.5-sun/lib/i386/libfontmanager.so
/usr/lib/j2re1.5-sun/lib/i386/libawt.so
/usr/lib/j2re1.5-sun/lib/i386/awt_robot
/usr/lib/j2re1.5-sun/lib/i386/gtkhelper
/usr/lib/j2re1.5-sun/lib/i386/xawt
/usr/lib/j2re1.5-sun/lib/i386/xawt/libmawt.so
/usr/lib/j2re1.5-sun/lib/i386/motif21
/usr/lib/j2re1.5-sun/lib/i386/motif21/libmawt.so
/usr/lib/j2re1.5-sun/lib/i386/headless
/usr/lib/j2re1.5-sun/lib/i386/headless/libmawt.so
/usr/lib/j2re1.5-sun/lib/i386/libioser12.so
/usr/lib/j2re1.5-sun/lib/i386/libjpeg.so
/usr/lib/j2re1.5-sun/lib/i386/libcmm.so
/usr/lib/j2re1.5-sun/lib/i386/libJdbcOdbc.so
/usr/lib/j2re1.5-sun/lib/i386/librmi.so
/usr/lib/j2re1.5-sun/lib/i386/libjaas_unix.so
/usr/lib/j2re1.5-sun/lib/i386/libjawt.so
/usr/lib/j2re1.5-sun/lib/i386/libunpack.so
/usr/lib/j2re1.5-sun/lib/i386/libjdwp.so
/usr/lib/j2re1.5-sun/lib/i386/libdt_socket.so


I copied and pasted "/usr/lib/j2re1.5-sun/lib/i386/" into Opera in Tools > Preferences > Advanced > Content > Java Options > Java Path. I also tried "/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre/lib/i386" as well.

I then tried to load [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) to test it all out. Still nothing happened. After loading the page, if I go back into the Java preferences the Java box is unchecked and turned off.

Also running Opera from Terminal gives the same results as before. Did I miss something somewhere. And thanks for responding.

---

### Post by Xian on 2005-11-01
In the ~/Java Options > Java Path box, when you click "Validate Java Path" what is the response? The paths you posted look correct, but I am using the j2re1.4 package so I can't attempt to reproduce the problem you are encountering. Perhaps you should use that version as well if you continue to experience this issue.

```
$ sudo apt-cache policy j2re1.4
j2re1.4:
  Installed: 1.4.2.02-1ubuntu3
  Candidate: 1.4.2.02-1ubuntu3
  Version table:
 *** 1.4.2.02-1ubuntu3 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
```

---

### Post by brisamrus on 2005-11-02
That was the problem. I installed j2re1.4 from the repository and now things are fine. Sure appreciate the help. Will I have any trouble running two versions of Java (1.4 & 1.5)? Thanks again for everything.

---

### Post by Xian on 2005-11-03
[QUOTE=brisamrus]Will I have any trouble running two versions of Java (1.4 & 1.5)? [/QUOTE]
No, they do not conflict. You are fine.

---


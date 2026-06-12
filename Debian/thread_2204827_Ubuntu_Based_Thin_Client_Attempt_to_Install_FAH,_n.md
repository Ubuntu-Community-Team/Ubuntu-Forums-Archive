---
title: "Ubuntu Based Thin Client Attempt to Install FAH, needs GLIBCXX_3.4.15"
date: 2014-02-10
forum: Debian
---

### Post by xtaylorsanchez on 2014-02-10
I wanted to install Folding At Home (FAH) on some Thin Clients I have. These are Igel Thin Clients, which are Ubuntu based. They have been very stripped down to the point that I do not even have the *dpkg* command. So far I extracted the .deb I received from [FAH's website]("http://folding.stanford.edu/"). When I attempt to run the FAHCoreWrapper I receive:

```
root@new-host-3:FAHClient start
FAHCoreWrapper: /lib/libstdc++.so.6: version `GLIBCXX_3.4.15` not found (required by FAHCoreWrapper)
root@new-host-3:
```

So I found that libstdc++.so.6.0.13 is installed under the /lib. But I can't follow [this]("http://stackoverflow.com/questions/5216399/usr-lib-libstdc-so-6-version-glibcxx-3-4-15-not-found") thread and run the *strings* command because it is another command that doesn't exist on this box. I am unsure how to move forward. There are quite a few threads that show up on Google with this error, but many expect a more 'versatile' command availability.

Update 0:
I ran ldd ```

root@new-host-3:ldd /lib/libstdc++.so.6
    linux-gate.so.1 => (0x0030c000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x005ce000)    
    libm.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00918000)
    /lib/ld-linux.so.2 (0x00195000)    
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x001d4000)
root@new-host-3:
```

Update 1:
I scp'ed the file off the Thin Client so that I can run strings on it:
```
  taylor@tsanchez-desktop:~$ strings libstdc++.so.6.0.13 | grep GLIBCGLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBC_2.0
GLIBC_2.3
GLIBC_2.4
GLIBC_2.1
GLIBC_2.3.4
GLIBC_2.1.3
GLIBC_2.3.2
GLIBC_2.2
GLIBCXX_FORCE_NEW
GLIBCXX_DEBUG_MESSAGE_LENGTH
taylor@tsanchez-desktop:~$ 

```
Which is easy to see the GLIBCXX_3.4.15 that is required is not available. 

I compared this to my local machine's libstdc++.so.0.18 and found that what I wanted was available. I attempted to just replace version (with full expectation that this was the wrong way to update it). This was done through a scp and then a symlink update in the /lib folder.

```
taylor@tsanchez-desktop:~$ strings /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18 | grep GLIBC
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBC_2.3
GLIBC_2.0
GLIBC_2.4
GLIBC_2.3.4
GLIBC_2.1
GLIBC_2.17
GLIBC_2.1.3
GLIBC_2.3.2
GLIBC_2.2
GLIBCXX_DEBUG_MESSAGE_LENGTH
taylor@tsanchez-desktop:~$ 

```

Which in turn gave me:
```
root@new-host-3:FAHClient start
FAHClient: /lib/tls/i686/cmov/libstdc++.so.6: version `GLIBC_2.17` not found (required by /lib/libstdc++.so.6)
root@new-host-3:
```
I figure this means that other files are lacking the update required to work with the new file I attempted to force onto the system. I will try to download a newer version of the firmware for the Thin Client and hope it has the updated libraries required.

---


---
title: "Run-Detectors"
date: 2008-03-13
forum: Gaming &amp; Leisure
---

### Post by MaindotC on 2008-03-13
In case you ever get this message:```


run-detectors: unable to find an interpreter for ./UrbanTerror_41_FULL.exe 
```

As you can see I cleverly downloaded the .exe and not the .zip source (which I'm downloading now and I assume it will have the installer files for *nix).

Just thought I'd post this because when I search the forums I couldn't find this error message anywhere.

Stupid me!

---

### Post by kayvortex on 2009-06-08
Let me just expand on that a bit: a "run-detectors: unable to find an interpreter for *some_binary*" means that your system can't run the binary because it is in a format not native to the system (or, at least, in a format for which there is no interpreter -- as the error says!).

For example, if you have *not* installed wine, and try to run a windows binary, you will get a run-detectors error. Let's try it. First, we see that my Windows binary is not in the native ELF binary format:
```
$ file /bin/cp
/bin/cp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
$ file /mnt/Windows_partition/WINDOWS/system32/taskmgr.exe
/mnt/Windows_partition/WINDOWS/system32/taskmgr.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit
```
So, let's confirm that I have execute permissions on the file:
```
$ ls -lh /mnt/Windows_partition/WINDOWS/system32/taskmgr.exe
-rwxrwx--- 1 root plugdev 133K 2008-04-14 01:12 /mnt/Windows_partition/WINDOWS/system32/taskmgr.exe
$ groups 
*user_name* adm dialout cdrom plugdev lpadmin admin sambashare
```
I do. So, no problems there. Let's try to run it:
```
$ /mnt/Windows_partition/WINDOWS/system32/taskmgr.exe
run-detectors: unable to find an interpreter for /mnt/Windows_partition/WINDOWS/system32/taskmgr.exe
```
And we see that I can't run it because the system doesn't know how to run a PE32 format binary.

---


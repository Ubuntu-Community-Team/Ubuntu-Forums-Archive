---
title: "Urban Terror"
date: 2011-10-20
forum: Gaming &amp; Leisure
---

### Post by 7cardcha on 2011-10-20
I downloaded a game called "Urban terror" as I thought it looked pretty cool. I chmoded the executable and ran it.
```

imps@vostro:~/Downloads/UrbanTerror$ sudo ./ioUrTded.i386 
[sudo] password for imps: 
ioq3 1.35urt linux-i386 Jan 28 2009
----- FS_Startup -----
Current search path:
/home/imps/.q3a/q3ut4
./q3ut4/zpak001_assets.pk3 (2411 files)
./q3ut4/zpak000_assets.pk3 (7933 files)
./q3ut4/zpak000.pk3 (99 files)
./q3ut4/ut4_commune.pk3 (150 files)
./q3ut4

----------------------
10593 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: vostro
IP: 127.0.1.1


```



And it stops there. it doesn't lag the computer. It doesn't pig cpu. It doesn't crash. I waited 2 minutes and nothing. Any ideas?

---

### Post by Perfect Storm on 2011-10-21
First of all, you don't run it with 'sudo'. Only if you're going to make an install system wide. You never run your applications with 'sudo'.

You properly messed up its permission. Set nautilus to see hidden files. Go and delete ./q3ut4 it may require you delete it with 'sudo' as the files are now set to 'root'
```
sudo rm -rf ./q3ut4
```

---


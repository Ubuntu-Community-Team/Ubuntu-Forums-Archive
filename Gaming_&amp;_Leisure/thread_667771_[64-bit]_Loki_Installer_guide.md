---
title: "[64-bit] Loki Installer guide"
date: 2008-01-14
forum: Gaming &amp; Leisure
---

### Post by Cappy on 2008-01-14
First, make sure the libc6 libraries are installed to avoid problems.
```
sudo apt-get install ia32-libs libc6 libc6-i386
```

[SIZE="3"][B]This guide will help if you get messages such as ```
Unable to find file /bin/Linux/x86/glibc-2.0/installer
```
or
```

This installation doesn't support glibc-2.0 on Linux / unknown
The setup program seems to have failed on unknown/glibc-2.0
```
[/B][/SIZE]

----

**Solution 1:**
Try ```
SETUP_LIBC=glibc-2.1
linux32 ./loki_installer.run
``` first. If that fails continue on:

**Solution 2:**
```
./loki_installer.run --target new_loki_dir
cd new_loki_dir
mv setup.sh setupold.sh
sed 's/`DetectLIBC`/"glibc-2.1"/' setupold.sh | sed 's/`DetectARCH`/"x86"/' > setup.sh
chmod +x setup.sh
./setup.sh

```

Replace "glibc-2.1" with whatever glibc it wants. You will still get the same errors during the extraction but it will extract.

You can use ```
./loki_installer.run --help
``` on a loki installer to see the correct syntax for extracting it without installing it.

---

### Post by robeast on 2008-05-06
Thanks for the guide! I just successfully installed Alpha Centauri based on your second error's first solution (simply using linux32). It also took me a minute to realize that it was trying to install the loki updater and loki uninstaller first, which both produced errors. Finally I just let it continue anyway and it installed Alpha Centauri fine.

Now if I could only get Alpha Centauri to run properly...

---

### Post by Vadi on 2008-06-16
Note that on Ubuntu 8.04 I got a "The setup program seems to have failed on x86_64/glibc-2.1" message. The solution to problem 1 helped.

---

### Post by Vadi on 2008-07-06
And thanks again Cappy, had to use this on the Ankh 2 demo as well.

---

### Post by KIAaze on 2009-08-23
Thanks, this helped a lot.
But for the doom 3 demo, I had to do this additionally:
```
mv new_loki_dir/bin/Linux/x86/glibc-2.1 new_loki_dir/bin/Linux/x86/glibc-2.0
```

(it was nice to add the "./loki_installer.run --help" tip, even if it wasn't necessary. :) )

i.e. the complete walkthrough:
```
./doom3-linux-1.1.1282-demo.x86.run --target new_loki_dir
cd new_loki_dir
mv setup.sh setupold.sh
sed 's/`DetectLIBC`/"glibc-2.1"/' setupold.sh | sed 's/`DetectARCH`/"x86"/' > setup.sh
chmod +x setup.sh
mv ./bin/Linux/x86/glibc-2.1 ./bin/Linux/x86/glibc-2.0
./setup.sh

```

---


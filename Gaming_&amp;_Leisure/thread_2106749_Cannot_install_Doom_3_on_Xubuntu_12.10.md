---
title: "Cannot install Doom 3 on Xubuntu 12.10"
date: 2013-01-19
forum: Gaming &amp; Leisure
---

### Post by ...waffles? on 2013-01-19
Hello all, haven't used ubuntu for a while ( last time was when 10.04 was still new lol) but started feeling bogged down by the ancient software in Debian Squeeze.  Anyway, I have been trying to install Doom 3 and the ol' Doom 3 SDK, and strangely enough I get the same error with both.  After downloading the doom3-linux-1.3.1.1304.x86 installer, chmod +x'ing it, and sudoing it, I get this 

```
Verifying archive integrity... All good.
Uncompressing DOOM 3.............................................................................................
./setup.sh: 192: ./setup.sh: /home/me/.setup3713: not found
```

The number ".setup3713" is different each time, but I get the same error with both the installer and the SDK.

The only other thread I found that is similar is here : [http://ubuntuforums.org/showthread.php?t=1979241](http://ubuntuforums.org/showthread.php?t=1979241)

Same problem, but as I am on 12.10, when I try to install ia32-libs it gives me WAY to much.  So I tried switching my nvidia driver from the software sources menu but I get the same error on both driver versions 304 and 310.

I am assuming I need something that would normally have been a part of ia32-libs, but I have no clue what.  As I said, when trying to install ia32-libs aptitude spit a huge list of stuff at me, and I don't want to install that much pork :D

Some of my specs:
Xubuntu 12.10
AMD Athlon II 64
Nvidia GTX 550 ti

Sorry about the messy post, any and all help will be appreciated.

---

### Post by ...waffles? on 2013-01-20
Well I went ahead and installed the ia32-libs package, switched back to the 310 Nvidia driver, and everything installed fine.  Lotta fuss over nothing, but at least it all turned out ok in the end.  :D

---


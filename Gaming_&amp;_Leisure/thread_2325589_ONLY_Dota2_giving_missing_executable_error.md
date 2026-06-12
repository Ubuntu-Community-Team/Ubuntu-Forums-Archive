---
title: "ONLY Dota2 giving missing executable error?"
date: 2016-05-23
forum: Gaming &amp; Leisure
---

### Post by charleswmanuel on 2016-05-23
Hello All, 

so I installed Steam, and it wouldn't open. found this bit of code to fix it: 
```
mv ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1{,.disable}
mv ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6{,.disable
```

Opens right up! yay! all other games work fine. Dota 2...my one true love...will not open. I get the DREADED missing executable error. 

The above was done from a LITERALLY fresh install (steam was the first thing i loaded onto my 14.04 install) without any other changes except updates. 

would love any help.

---

### Post by thanosapostolou on 2016-05-24
If you use 64bit Ubuntu, I think Dota 2 uses the 64bit libraries so try to do the same for:
~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libgcc_s.so.1
~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6

---


---
title: "ndiswrapper, problems obtaining .sys and .inf files"
date: 2006-08-20
forum: Desktop Environments
---

### Post by nzk on 2006-08-20
I have the .exe's for both my wifi cards, but I have absolutely no idea how to get the .sys and .inf files out of the .exes! ](*,)  Help please

---

### Post by llamakc on 2006-08-20
Google.

** How do I unpack a Windows driver file in .EXE format? **

 [LIST]
[*] Usually these are self-extracting zip files. If that is the case, in Linux, you can run 'unzip' on the .EXE file, which should extract files. Sometimes, they are .cab files, in which case, you can use 'cabextract' to unpack. If you find .INF and .SYS files at this step, that is all you need. However, some drivers, after extracting, will give install shield files, usually in 'data2.cab' file. To extract files out of data2.cab, run 'unshield x data2.cab'. You should now have .INF and .SYS files in a sub-directory where you extracted. So, in short, a combination of unzip/cabextract/unshied can unpack driver file in most cases. This combination doesn't always work though - sometimes you may need to use 'wine' to extract. And in a few cases, even that doesn't work and you need to use Windows to install the driver and find .INF and .SYS files.[/LIST]

---


---
title: "Steam No Longer Launches after Latest (Steam) Update (Ubuntu/KDE 12.10)"
date: 2013-11-05
forum: Gaming &amp; Leisure
---

### Post by casparov on 2013-11-05
Hi, Everyone...  

I had Steam (WINE version 1.4x) running beautifully in Ubuntu 12.10 (KDE Plasma 4.10) until today when a Steam update wouldn't launch the program.  The following is a (very) partial paste of the text displayed in Terminal:

  > Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005ad0, 0x3f03ab30, 0x3f03ab28
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005ad0, 0x3f03ab68, 0x3f03ab60
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005ad0, 0x3f03aaf8, 0x3f03aaf0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005ad0, 0x3f03aba0, 0x3f03ab98
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005ad0, 0x3f03abd8, 0x3f03abd0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
whit@HAL:~/Desktop$ fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub


I was wondering if anybody has an idea about this (or if this error is a known bug in Steam).

Thanks so much for anyone reading and/or replying in any way...          Casp

---

### Post by mastablasta on 2013-11-06
perhaps update wine? or better yet not use unsupported ubuntu?

---

### Post by simon-grant-biggs on 2013-12-22
Revert from using the Beta. Can do that in the following ways:
[https://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=19444&iThreadId=88269](https://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=19444&iThreadId=88269)
[https://developer.valvesoftware.com/wiki/Betas](https://developer.valvesoftware.com/wiki/Betas)

---

### Post by oldrocker99 on 2013-12-23
Steam wouldn't start for me for Skyrim, which I installed using the PlayOnLinux script. I enabled the wine PPA, chose "configure" and installed wine 1.78. Success!

---

### Post by Ranko Kohime on 2013-12-23
Something in the Steam update from Dec. 3rd broke it in Wine for everybody.  You need to update Wine to 1.7.8 to get it working again.

ETA: To do that, add the Wine PPA, and then update, like so:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get upgrade
```

---


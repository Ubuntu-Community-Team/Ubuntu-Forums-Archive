---
title: "RAR with SFX ?  ;)"
date: 2009-05-02
forum: General Help
---

### Post by frenchn00b on 2009-05-02
Hello the command is:

```
rar a -s   -v1000 myrar.rar * 
```
a for add
 
v1000 for 1mb, splitting
**-s for SFX with modules into the home directory, ok, but what/how?**


--
instead of posting use WINE, which is not brigth, I recommand to do man rar before ;)

---

### Post by frenchn00b on 2009-05-02
he he 

**1/ How to make a rar extractable for windows?**

so 
get those on megaupload 
5a74b0c8e3d35fe498d580e08e90650c *default.sfx
76ab410e2826456a9ca9a006ffea6766 *wincon.sfx
5a74b0c8e3d35fe498d580e08e90650c *windows.sfx
eeb322f1978b711140ec076fa735cb50 *zip.sfx
f53dce3ad1e2f73ccf5aa577519f1c92 *freebsd.sfx
6887d39229d11a8b063d8c9c03b0a732 *linux.sfx
4be71f85fc808ed14355ae5e2e69e9e7 *macos_x.sfx
8a70b6be524d625d17291c6d5766cced *7z.sfx
fbec918cd09e5bd955411c474d440f27 *7zCon.sfx
put that 
under /home/username/.sfx

2/ 
go to the folder where owns the file:
so type:
cp /home/username/.sfx/windows.sfx .
```
rar a -sfxdefault.sfx myexeforwindows.exe myfiledocument.doc
```

Enjoy, 

**Say thanks please !! cuz it is no where on LINUX Boards !!**

--
DN1NVFP0

---


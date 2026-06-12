---
title: "wine not executing applications"
date: 2008-12-10
forum: General Help
---

### Post by keygiwawah on 2008-12-10
I recently installed wine and have been unable to use my windows .exe files.  I tried reinstalling it, but it did not change anything.  I'm not sure if it's a problem with my computer or what.  Also I downloaded it on a mac and transfered it to my linux machine with a usb flashdrive.  I didn't think that woult effect anything.

---

### Post by ajcham on 2008-12-10
Are you trying to run programs from a Windows partition?  If the Windows partition is NTFS, then I believe this is a no go.

Ideally you should install the programs within Wine itself (just run the setup program with Wine).  This will install the software into a virtual C: drive located in your ~/.wine directory.

Also, be sure to check the Wine [AppDB]("http://appdb.winehq.org/") to see if the program you are using is known to run in Wine.

---

### Post by keygiwawah on 2008-12-10
Thanks, that worked just fine.

---


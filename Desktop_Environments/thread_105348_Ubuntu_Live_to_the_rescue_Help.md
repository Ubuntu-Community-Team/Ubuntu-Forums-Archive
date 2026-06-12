---
title: "Ubuntu Live to the rescue Help"
date: 2005-12-18
forum: Desktop Environments
---

### Post by rlange on 2005-12-18
I need to delete a spyware file that has attached itself to the windows login process. The file resides in C:/windows/AppPatch    it is named javaad.dll

Because it has attached itself to the winlogin process  windows will not delete it because it is in use.

Can I use Ubuntu Live to delete this file? If so how can I do this?


I have a Ubuntu 5.04 live cd.

Thanks

---

### Post by aysiu on 2005-12-18
Is your Windows installation using an NTFS filesystem?
If so, you may be corrupting your entire installation by trying to delete that file from Ubuntu.
NTFS is read-only from Linux.

---

### Post by rlange on 2005-12-18
yes it is ntfs however several spyware scanners are reporting this file as spyware. This file is not on any other machines I have looked at so I am very sure this file is spyware. If winlogon is not used I could delete it but winlogon must be used to get to the desktop.

---

### Post by aysiu on 2005-12-18
Isn't there some kind of safe mode or recovery mode in Windows you can use?

---

### Post by rlange on 2005-12-18
You must use winlogon.exe even in safe mode. Also using recovery will not delete this file it will ony repair system files not deleteing any. Been there done that.

---

### Post by Rackerz on 2005-12-18
Search Techforums in google. Alot of them will help you out with this problem. They've helped me ;).

---

### Post by rlange on 2005-12-18
Solved.    I used total commander in a pre boot state.

---


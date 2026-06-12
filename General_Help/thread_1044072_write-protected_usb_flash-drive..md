---
title: "write-protected usb flash-drive."
date: 2009-01-19
forum: General Help
---

### Post by unzoo on 2009-01-19
I recently tried to install Ubuntu 8.10 onto a 4G usb flash-drive. I think the Live CD I used might of been dodge because the drive never worked and has been write-protected ever since. I downloaded and burnt a new Live CD wich worked fine on a smaller 1G flash-drive.I've tried searching threw web forums and nothing I try removes the write-protection. Someone please help.

P.S. my hard drive recently failed wich is wy i need to use the 4G flash-drive. 1G is to small

---

### Post by scouser73 on 2009-01-19
Perhaps you don't have permissions set on the USB flash drive, if that's the case then open up Terminal and enter **gksudo nautilus** this will then open nautilus where you can then navigate to the correct drive, and then check and set permissions. Good luck.

---


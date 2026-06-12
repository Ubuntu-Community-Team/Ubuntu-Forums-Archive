---
title: "double boot options"
date: 2008-12-04
forum: General Help
---

### Post by moot1 on 2008-12-04
Hi, 

I recently installed Ubuntu again through windows and on the screen where it asks you to choose which OS you want to boot, Ubuntu shows up twice. Is there anyway for me to get rid of one of the ubuntu boot up options?

This is how it looks like:

Vista
Ubuntu
Ubuntu

Thanks for your help.

---

### Post by Partyboi2 on 2008-12-05
Check your C:\boot.ini file and make sure that there is only one entry for ubuntu.

---

### Post by banana jama on 2008-12-05
use this command in terminal  
> gksudo gedit /boot/grub/menu.lst
scrol down and delete the extra ubuntu entry that you donot want. once completed save the file. there should now only be one ubuntu on your loading screen.

o yea OS entries are usually 4 or five lines long. 
i used this method to remove an windows entry from my boot screen it should work for removing an extra ubuntu entry.

---

### Post by utsuprainfra on 2008-12-05
> **Partyboi2 said:**
> Check your C:\boot.ini file and make sure that there is only one entry for ubuntu.

funny.

---

### Post by Partyboi2 on 2008-12-07
> **utsuprainfra said:**
> funny.
I was under the impression that the orginal poster had installed ubuntu using wubi which uses the windows boot loader. I could be wrong :p

---


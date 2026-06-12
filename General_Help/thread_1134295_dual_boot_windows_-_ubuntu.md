---
title: "dual boot windows - ubuntu"
date: 2009-04-23
forum: General Help
---

### Post by themacedonian on 2009-04-23
ok, hier is my new problem :)))
i have installed windowsxp after that i ve install ubuntu 
when i finished instalation with ubuntu, i restart my pc ( i must ) and i have no menu, just load windows. how i can make menu using windowsXP ?


10x in advance

---

### Post by Monotoko on 2009-04-23
Its fairly simple, you just need to restore the MBR, find that Ubuntu Live CD and boot it, then:

```
sudo su
```
```
grub
```
```
find /boot/grub/stage1
```

You should get something like (hd0,2) remember that


run:
```
root (hd0,2)
``` (replace 0,2) with your own code which you got from the last step

```
setup (hd0)
```

Now all thats left, type quit then restart

EDIT: You will also want to use this to get Windows to show up on the menu
```
sudo gedit /boot/grub/menu.lst
```

Then add this to the bottom of the file somewhere, replace (hdx,y) with the location of the Windows partition

title   Windows
root   (hdx,y)
makeactive
chainloader   +1

---

### Post by ubu-for on 2009-04-23
You have to install Windows first and Ubuntu afterwards, if you don't like HOWTOs.

Otherwise try this.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

---


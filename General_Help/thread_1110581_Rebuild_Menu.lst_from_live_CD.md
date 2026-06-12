---
title: "Rebuild Menu.lst from live CD?"
date: 2009-03-29
forum: General Help
---

### Post by ownaginatious on 2009-03-29
I accidentally deleted my menu.lst file, and now I'm unable to boot my computer. I've tried regenerating it on from the live CD by chroot-ing to my hard drive and running update-grub, but that just creates a blank menu.lst file without any kernal entries.

Can anyone help me out with this? It's becoming very frustrating to not be able to boot my computer.

Thanks,

Dillon

---

### Post by cariboo on 2009-03-30
If you have used gedit to edit /boot/grub/menu.lst you should have a backup of your menu.lst called /boot/grub/~menu.lst, just rename the file to menu.lst. In an Applications-->Accessories-->Terminal type:

```
sudo mv /boot/grub/~menu.lst /boot/grub/menu.lst
```

If you don't have a backup, use the LiveCD to boot to the desktop, open a terminal and type:

```
sudo grub
```

at the prompt type:

```
find /boot/grub/stage1
```

the result should look like this:

```
(hd0,0)
```

Use the resut of the find command to set where to look  for menu.lst:

```
root (hd0,0)
```

then set up the MBR:

```
setup (hd0)
```

Next type:

```
quit
```

You should now have a valid /boot/grub/menu.lst. Reboot and you should be good to go.

Jim

---


---
title: "How do I make sudoers work again, permissions have changed"
date: 2008-12-23
forum: General Help
---

### Post by infocom on 2008-12-23
I accidentally pressed Ctrl+C in a sudoers session.
So it was locked and I could not access it again. 
Found a thread that stated to change permissions to u+x but it didn't work.
So now I just get the following error everytime I try to run it or even change permissions:
```
sudo: /etc/sudoers is mode 0540, should be 0440
```

Well, this error is bit pointless because I am trying to change permissions to 0444, but because permissions aren't 0444 I can't change them to 0444. :(

Could someone please let me know how to get sudoers back, all I want to do is allow my user to run sudo commands without entering passwords as its extremely annoying and I cant run automated shut down without it. 

Thanks

---

### Post by albandy on 2008-12-23
So if you can't use sudo you should reboot your computer in "single user mode"
then change the file permisions.

---

### Post by Titan8990 on 2008-12-23
First off, is your drive formatted in a Linux format (EXT2, EXT3, JFS, XFS)?

Without it, you will not be able to restore the permissions.


Log in to recovery mode and select the root shell. From the root shell, the following command will fix the permissions:


chmod 440 /etc/sudoers
chown root:root /etc/sudoers

---

### Post by unutbu on 2008-12-23
Reboot the machine. If you can not use the GUI to shutdown cleanly, press
```

Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B
```

Wait a few seconds between each key combination.

This will reboot your machine.

During the boot process, get to the GRUB menu. You might have to press ESC to see the GRUB menu. There, select "Recovery Mode". You will either be dropped directly into a root shell (for pre-Hardy Ubuntu) or you will be shown a menu. If you see the menu, select "drop to root shell".

At the root shell type
```

chmod 0440 /etc/sudoers
init 2
```

init 2 will resume the default boot process and get you to the gdm login window.

---

### Post by Titan8990 on 2008-12-23
> There, select "Recovery Mode". You will either be dropped directly into a root shell (for pre-Intrepid Ubuntu) or you will be shown a menu.


That menu actually started in 8.04, not 8.10 but a good guide nonetheless.

---

### Post by infocom on 2008-12-23
thanks for all your speeedy replies! thats fixed it. I restarted in Recovery Mode and entered the prompt as root, then chmod 0440 /etc/sudoers fixed it. 
phew, quite some work for a simple accidental ctrl+c
thanks

---

### Post by unutbu on 2008-12-23
infocom, there is a safe way to edit /etc/sudoers:
```

sudo visudo 
```
I believe be default on Intrepid this command launches the nano editor. If you would like a graphical editor like gedit, you can use
```

EDITOR=gedit gksu visudo
```

visudo checks the syntax of the edited /etc/sudoers file and does not allow you to save it unless it passes some checks.

---

### Post by Titan8990 on 2008-12-23
I thought that it launched vi, hence the name visudo, although it doesn't say anything about that in the man page description.

---


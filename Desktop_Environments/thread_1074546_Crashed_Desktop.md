---
title: "Crashed Desktop"
date: 2009-02-19
forum: Desktop Environments
---

### Post by AndyP79 on 2009-02-19
Okay, so my desktop has crashed. I am not able to do anything except use the shut down button. No panel, no icons, no scrrenlets, nothing works. But, I can access stuff through logining into the terminal made, though I don't know too many commands. 

I would like to remove, gnome and compiz through the terminal, then re-install them, how would I go about doing that, then if that does not work, I just want to save all my files to my external harddrive, and reload. 
Anyone?
Thanks
-a

---

### Post by taurus on 2009-02-19
If you want to go back to the default settings, you could try removing ~/.gconf, ~/.gconfd, ~/.gnome2.

```
rm -rf ~/.gconf ~/.gconfd ~/.gnome2
```
And if you want to save your all files to an external harddrive, you need to mount it first before you can use/access it.  What happens if you plug it in?  Does it automount for you?  Otherwise, you can mount it by hand from a terminal.

```
sudo fdisk -l
df -h
```

---


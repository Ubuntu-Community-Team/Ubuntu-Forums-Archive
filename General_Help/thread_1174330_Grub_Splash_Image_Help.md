---
title: "Grub Splash Image Help"
date: 2009-05-30
forum: General Help
---

### Post by kyle2595 on 2009-05-30
I have been wanting to change the Splash Image in Grub for some time now.  I had viewed this post: [http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341). One of the first steps says: " move the image to the grub folder (assuming the current dir is your home folder and this is were you downloaded the image)." I tried running the command:

sudo mv usplash.xpm.gz /boot/grub/images Just like it said, but it tells me "cannot stat `usplash.xpm.gz': No such file or directory.
Firefox saves the .xpm.gz file to the desktop.  Can any one help?

---

### Post by pastalavista on 2009-05-30
cd to the desktop before running the mv command

---

### Post by kyle2595 on 2009-05-30
How do you do that?  I am new to Linux and all.

---

### Post by pastalavista on 2009-05-30
> **kyle2595 said:**
> How do you do that?  I am new to Linux and all.
When you open the terminal, it starts you in your home directory. enter
```
cd /Desktop
``` and now your prompt will say "$~/Desktop". 

'$' means you're a regular user and '~' represents /home/username

so '$~/Desktop' = the '/home/username/Desktop' directory. That is where your file is, isn't it? To find out enter ```
ls
``` and it should list what's on your Desktop (or whatever directory you happen to be in at the time) if you see your file in the list, you're in the right place

---

### Post by kyle2595 on 2009-05-30
Cool, thanks!

---


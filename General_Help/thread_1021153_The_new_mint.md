---
title: "The new mint"
date: 2008-12-25
forum: General Help
---

### Post by vivek_123 on 2008-12-25
Hello guys and merry christmas to all of you
I am currently using ubuntu 8.10 .Yesterday i tried to install 
linux mint on my pc but ,though it was completely and properly installed ,It was not shown on my boot option menu i.e my boot screen still showed older O.S xp(sp2) and ubuntu 8.10 but,didn't showed linux mint!! please provide me with a remedy.

---

### Post by SPr on 2008-12-25
[How to restore Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---


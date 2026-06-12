---
title: "Install Inside Windows Missing -ubuntu 14.04"
date: 2014-05-09
forum: Desktop Environments
---

### Post by ramakanta on 2014-05-09
when I want to install Ubuntu 14.04 LTS inside windows, there is  *Install Inside Windows* Menu Missing. please help how to install Ubuntu inside the windows 7 . thank you

Ubuntu  9.10

 [[IMG]http://s28.postimg.org/6qhyctnvd/image.jpg[/IMG]]("http://postimg.org/image/6qhyctnvd/")

Ubuntu 14.04

[[IMG]http://s28.postimg.org/igvvu7gnt/image.jpg[/IMG]]("http://postimg.org/image/igvvu7gnt/")  Install Inside Windows menu Missing

---

### Post by kc1di on 2014-05-09
WUBI should be present if your windows version is compatible. WUBI (install inside windows) is not compatible with windows 8 or windowsME. 

It is included on the ISO however.

---

### Post by ramakanta on 2014-05-09
> **kc1di said:**
> WUBI should be present if your windows version is compatible. WUBI (install inside windows) is not compatible with windows 8 or windowsME. 

It is included on the ISO however.

my PC have  have windows 7

---

### Post by kc1di on 2014-05-09
in that case why not install virtualbox in windows (it's free) and run Ubuntu in the virtual machine. Or better yet install Ubuntu run window in virtual box , the advantage of using virtual box is that you do not have to reboot to access ubuntu or windows. 
[Here ]("http://www.wikihow.com/Install-and-Setup-Virtualbox,-With-an-Ubuntu-Linux-O/S-for-Windows-7")are a couple pages that can help, and [here.]("http://www.youtube.com/watch?v=rt8wrKBKrt0")

---

### Post by ajgreeny on 2014-05-09
If your computer uses UEFI and gpt partitions wubi will not work, so Win 7 will not have wubi if your computer is installed with UEFI or gpt either.

---


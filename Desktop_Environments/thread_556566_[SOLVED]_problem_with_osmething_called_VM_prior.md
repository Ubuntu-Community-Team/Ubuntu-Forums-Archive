---
title: "[SOLVED] problem with osmething called VM prior"
date: 2007-09-21
forum: Desktop Environments
---

### Post by tropcky on 2007-09-21
i just had a messenger called mercury  and i heard that its good 
so i installed it and evry thing it deb by the way  
and when i tryed 2 run   nothin happend its just didnt run i tryd 2 run by the terminal  2 see what goin on and when i did iu got thes :

tropcky@tropcky-linux:~$ mercury
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
tropcky@tropcky-linux:~$ 

so i did that : 

sudo apt-get install vm 

and when it finch installing the vm  i tryed to run it agen  and it gives the same msg :

tropcky@tropcky-linux:~$ mercury
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
tropcky@tropcky-linux:~$ 
 so any help ?

---

### Post by tropcky on 2007-09-21
any one

---

### Post by alephiej on 2007-09-22
You must install a package named:
sun-java5-bin

You can do it from command line by typing:
sudo apt-get install sun-java5-bin

Regards

---


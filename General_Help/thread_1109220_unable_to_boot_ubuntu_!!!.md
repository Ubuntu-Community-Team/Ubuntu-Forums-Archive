---
title: "unable to boot ubuntu !!!"
date: 2009-03-28
forum: General Help
---

### Post by rokroff on 2009-03-28
hi all 
i install ubuntu 8.10 on my box , and then install linux centos 5 after ubuntu , but i couldn't boot my old ubuntu from grun command line , when i type root(hd0,  and then press tab to show all available partitions , my ubuntu partition look like :
file system  unknown , type 82 (or something like this)
then i open centos 5 and convert ubuntu file system to ext2fs by 
[root@localhost~]#tune2fs -O ^has_journal /dev/hda6 
but this also couldn't solve my problem , could i go to install grub from ubuntu CD ? or there's best solution ? please help me this is first time that i use ubuntu :) 
thanks & regards

---

### Post by 3Miro on 2009-03-28
Are you sure Ubuntu is still alive? Can you see all the system files and everything else from within CentOS

---

### Post by rokroff on 2009-03-28
yes ubuntu is alive i mount it under centos and found all my files

---

### Post by rokroff on 2009-03-30
no solution ???? impossible 

if(no_solution ){
   leave_ubuntu() ;
   return to_my_old_linux ;
}

---


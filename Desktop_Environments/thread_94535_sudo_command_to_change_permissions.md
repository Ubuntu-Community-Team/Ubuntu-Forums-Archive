---
title: "sudo command to change permissions"
date: 2005-11-24
forum: Desktop Environments
---

### Post by AzraelShade on 2005-11-24
Okay i installed Ubuntu on a 4.3 GB ext3 partition and kept a 8GB FAT32 partition(on which i had the other OS stuff saved - documents, mp3s etc.. so didn't want to make this one ext3 too... ). Things is i want to save all my Linux kits and stuff while i will be using Ubuntu(hope that will be for a long time now... but if i can't work this out... ) So opened terminal typed sudo -i (also tried sudo -s and sudo su) and tried 
chmod 666 kits. tried chown *my_username* kits. tried chgrp *my_group* kits. Nothing seems to work.. I still have my permission set on rwxr-x-r-x. This makes it unable to download my kits into that specific partition... :???:  Anyone can help, please?

P.S. when trying to subscript to this forum, i tried like 6 times to type those letters... that till i realized i have to use lowercase? o_0 (in the image you can cleary see those are uppercase chars) . I am wrong? If yes maybe forums admins should give a hint on the fact that lowercase must be used. 
~~~AzraelShade~~~

---

### Post by frodon on 2005-11-24
Ok, FAT32 file system don't support unix rights and ownership, so chmod ans chown commands won't work.
If you want to access your partition as a simple user you have to put the good option to the corresponding line in your fstab file. So i purpose you to post your fstab file here and then we will give you back the modified line to cut and paste.
To open the file : ```
sudo gedit /etc/fstab
```Similar thread : [http://ubuntuforums.org/showthread.php?t=92178](http://ubuntuforums.org/showthread.php?t=92178)

---

### Post by AzraelShade on 2005-11-24
LOL :) thanx .. i tried before changing in fstab but only with default,rw and didn't worked. Saw the other thread and got it :) Thank You.

~~~AzraelShade~~~

---


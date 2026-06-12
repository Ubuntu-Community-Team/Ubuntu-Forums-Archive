---
title: "no more cifs automount"
date: 2009-05-28
forum: General Help
---

### Post by Olivier Lec on 2009-05-28
Hi everyone, 

since I have upgraded to jaunty for some reason my nas mount point are not coming automaticly at boot time. 

My /etc/fstab entries look like this
```

/192.168.1.1/notebook    /media/terastation/notebook        cifs    _netdev,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

If I do a ```
sudo mount -a
``` everything get mounted has it should. 
I tried to play with the netdev stuff has you can see without any success.

Last point which is kind of weird my dmesg is not showing anything wrong ... 

any hint/idea would be really appreciated!

---

### Post by Olivier Lec on 2009-05-28
Bump!

---


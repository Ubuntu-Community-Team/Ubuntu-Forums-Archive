---
title: "delet gdm config files reset gdm"
date: 2013-11-20
forum: Desktop Environments
---

### Post by mindbox on 2013-11-20
I installed ubuntu 12.04. And have since intalled gnome, cinnamon, kde, and several light weight window managers. I also install gdm and kdm. But now lightdm doesn't work. It says i'm running in low graphics mode. So I switched to gdm, which allows me to login. But it doesn't list all the session I've installed. I tried purging kdm, gdm, and lightdm. But when I reinstall I have the same settings as before. I mean the same background picture and session options. 

Can I delet the config files and have everything reset or would that reck my system? What config files would I delet? 

If possible I'd like to have all three working properly agian. I know I have to manually switch between them. 

Thanks for any help.

---

### Post by ibjsb4 on 2013-11-21
Try the reconfigure command.

```
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

Those commands will also work for lightdm.

---

### Post by mindbox on 2013-11-22
Thanks for the tip, gdm is working now. 

Do you know if it's safe to delet conf files? Will they automatically be recreated?

---


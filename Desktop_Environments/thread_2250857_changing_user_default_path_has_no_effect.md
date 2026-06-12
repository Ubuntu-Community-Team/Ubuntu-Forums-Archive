---
title: "changing user default path has no effect"
date: 2014-10-31
forum: Desktop Environments
---

### Post by krzysztofpater on 2014-10-31
kubuntu 14.04 LTS - fresh installed

How to check it:
go to System Configuration -> Account properties (icon in 1 row, 5 from left) -> Select Tab: Paths
I tried to change some folders, for example for Documents:
/home/krzysztof/Dokumenty -> /mnt/sdb8/krzysztof/Dokumenty 
where /mnt/sdb8 is /home partition from 12.04 LTS

the path changing has no effect on displayed data, folder Dokumenty opens still in /home/krzysztof/

The same happens for other changed entries. Reboot has no effect. In console mode the same.

---

### Post by deadflowr on 2014-10-31
It does not change the entries for dolphin. It changes where an application, such as kate, looks for the files by default.

---

### Post by Erik1984 on 2014-10-31
Not a direct answer but what you want can be achieved with symlinks. Suppose the folder /home/krzysztof/Dokumenty does not exist (you can delete it if it doesn't contain any documents), then you can make a symlink with that name :
```

ln -s /mnt/sdb8/krzysztof/Dokumenty /home/krzysztof/Dokumenty

```
Now the Dokumenty folder in your home directory is a symbolic link to the Dokumenty folder on the mounted partition.

---

### Post by speartip on 2014-11-01
Hi Krzysztofpater,

If I understand what you are trying to do, it is very simple.
Just open system settings, account details, & paths.
There you change all your default folder locations.
Hope this helps.

---

### Post by 33Nicolas on 2015-02-02
I am trying to do something similar. My documents are on a different partition that is mounted automatically. I don't know where to go to change the default Document path to the document folder I use on the other partition.

I'm using Ubuntu Studio and can't find Account Details on the Settings menu. Can you help?

Thanks,

---

### Post by speartip on 2015-02-02
Hi 33Nicolas,
Your problem is slightly different as the Op is using Kubuntu not Ubuntu.
The easiest way around your problem is to install ubuntu tweak from here:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
If you open up the program & go to Admins/User Folder, you can then change your folder paths.

---


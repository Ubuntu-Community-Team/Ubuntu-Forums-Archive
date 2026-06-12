---
title: "how to auto mount drives?"
date: 2009-03-03
forum: Desktop Environments
---

### Post by aurora_consurgens on 2009-03-03
Hello, Guys 

I use Ubuntu 8.10 It's be perfect. My laptop was installed 2 OS (windows,Linux) In windows I have Drive C,D (Both are NTFS) so I want to mount These NTFS drives automatically when I log in Ubuntu. 

How can I do it? 

Thank you.

---

### Post by taurus on 2009-03-03
Install ntfs-config and use it to configure your ntfs partitions.  

Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---


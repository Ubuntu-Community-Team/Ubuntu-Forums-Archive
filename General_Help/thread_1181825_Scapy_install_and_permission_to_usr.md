---
title: "Scapy install and permission to /usr"
date: 2009-06-08
forum: General Help
---

### Post by sky811 on 2009-06-08
hello,
 
I am new in Ubuntu. I just install Scapy into python. but after installation, don't know why Python still cannot run the Scapy lib. Do I need to copy the scapy.py to /usr/bin/python/ ? I have tried to do so, but while I was copying the scapy.py to the python folder, permission denied! What should I do?
 
Thanks!

---

### Post by michy99 on 2009-06-08
To copy files into a system folder, you need to use sudo to temporarily give yourself root permissions.```
sudo cp file newlocation
```

---


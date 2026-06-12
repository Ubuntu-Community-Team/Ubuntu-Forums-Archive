---
title: "System settings does not open in ubuntu 20.04"
date: 2020-09-09
forum: Desktop Environments
---

### Post by sandywandy on 2020-09-09
A very strange problem has occurred in my ubuntu 20. After clicking the settings icon, nothing happens. Even from terminal, if I type the command gnome-control-center, it gives an error as below:

error while loading shared libraries: libjpeg.so.8: cannot open shared object file. No such file or directory.

Please advise what to do. Thanks in advance.

---

### Post by CelticWarrior on 2020-09-09
Have you messed with phyton?

---

### Post by ActionParsnip on 2020-09-09
Try
```

sudo apt -y install libjpeg-turbo8

```

Should install the file you need
[https://packages.ubuntu.com/search?searchon=contents&keywords=libjpeg.so.8&mode=exactfilename&suite=focal&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=libjpeg.so.8&mode=exactfilename&suite=focal&arch=any)

---

### Post by sandywandy on 2020-09-11
executed the command. Got this reply:

libjpeg-turbo8 is already the newest version (2.0.3-0ubuntu1.20.04.1).

---

### Post by sandywandy on 2020-09-11
No never. My python versions are running fine and all of them are easily managable. I have 2.7, 3.8 in /usr/bin/ and 3.7.7 from anaconda. All of them are working fine.

---

### Post by sandywandy on 2020-09-11
No never. My python versions are running fine and all of them are easily managable. I have 2.7, 3.8 in /usr/bin/ and 3.7.7 from anaconda. All of them are working fine.

---

### Post by sandywandy on 2020-09-11
Thank you ActionParsnip. I had to reinstall it. Mere installation did not work. I tried:

sudo apt install --reinstall ligjpeg-turbo8

Thank you for the hint.

---


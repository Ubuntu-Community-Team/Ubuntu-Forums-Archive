---
title: "open a .rar file?"
date: 2009-04-21
forum: General Help
---

### Post by JakeHinojosa on 2009-04-21
does anybody know of any software i could download that can open a .rar file?

---

### Post by Nano_ext3 on 2009-04-21
In Ubuntu's Add Remove, install 7 zip, it can handle just about any format and can be used in the GUI or in Terminal.  You could alternatively install the "Rar Archiver" in the Add/Remove repo as well.  If you can't find either, be sure to enable all software sources.

_Nano

---

### Post by JakeHinojosa on 2009-04-21
> **Nano_ext3 said:**
> In Ubuntu's Add Remove, install 7 zip, it can handle just about any format and can be used in the GUI or in Terminal.  You could alternatively install the "Rar Archiver" in the Add/Remove repo as well.  If you can't find either, be sure to enable all software sources.

_Nano

it says i have 7zip, but how do i use it?

---

### Post by youknowwhat4q on 2009-04-21
> **JakeHinojosa said:**
> it says i have 7zip, but how do i use it?

Easiest was to solve this problem is to open the package manager and just search "rar"

It should come up with the package "unrar", download it and you should be in business.

---

### Post by Nano_ext3 on 2009-04-21
Make sure you have "unrar" installed, then use the archiver to extract. The association should automatically update with the install and clicking on a rar archive in Nautilus should do the trick

> Basically, to unrar a file in Linux, just navigate to the directory where your rar archive is and type unrar x [filename.rar], replacing [filename.rar] with the name of your rar archive

Otherwise:

```
sudo apt-get install rar unrar p7zip p7zip-full
```

Right click the .rar file in File Manager (GUI), and select unpack/extract


Command Line Guide:  [http://www.howtoadvice.com/7zipHelper/](http://www.howtoadvice.com/7zipHelper/)

---


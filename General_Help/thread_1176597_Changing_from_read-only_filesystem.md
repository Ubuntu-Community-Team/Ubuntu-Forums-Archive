---
title: "Changing from read-only filesystem"
date: 2009-06-02
forum: General Help
---

### Post by Kvothe on 2009-06-02
Just recently I have been unable to copy files to my thumb drive. I somehow changed it to a read-only file system, and would like to change it back to whatever normal is. If I need to use the terminal, please give full lines of code. Thank you for your time.

---

### Post by MichaelSammels on 2009-06-02
In Terminal:

```
sudo apt-get install pysdm
```
```
sudo apt-get pysdm
```

When running look through the options for your Flash Drive.

---

### Post by Kvothe on 2009-06-02
I opened it up, and I'm not seeing my drive there. It's a windows filesystem, does that help?

---

### Post by MichaelSammels on 2009-06-02
Storage Device Manager should recognise NTFS. Do you know what's letter name is? (For example sdc1)?

---


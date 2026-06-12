---
title: "How do I install?"
date: 2009-01-10
forum: General Help
---

### Post by cholmes on 2009-01-10
How do I install "other" programs thjat I download from sites. For instance Linux software versions for my printer. After I download it to my desktop what do I do to install the software? I have tried many different things but nothing seems to work.

---

### Post by jespdj on 2009-01-10
There's not a single way to install software. Are there no installation instructions with the software?

Sometimes you get .tar.gz files, which are archive files (just like zip files). Unpack them with a command like this:
```
tar xfz archive.tar.gz
```
Sometimes you get a script or an executable file. Make sure the file is executable:
```
chmod u+x somefile.bin
```
and run it like this:
```
./somefile.bin
```

---

### Post by cholmes on 2009-01-10
Not sure I understand, The file is a "run" file. How do I execute a type of file such as this?

---

### Post by taurus on 2009-01-10
You can try something like

```
cd ~/Desktop
chmod +x filename.run
sudo ./filename.run
```

---


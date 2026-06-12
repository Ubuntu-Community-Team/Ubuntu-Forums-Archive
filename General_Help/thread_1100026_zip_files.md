---
title: "zip files"
date: 2009-03-18
forum: General Help
---

### Post by mikeonthebeach on 2009-03-18
does any1 know a good program for using zip files for ubuntu 8.10

---

### Post by spcwingo on 2009-03-18
If by using you mean comprossing and uncompressing, I would say just use file roller.  It's installed by default.  To use it, just open Nautilus and double click the .zip file.  This will open file roller.  To extract, just select where you want to extract and press "extract".

---

### Post by mb_webguy on 2009-03-18
+1

The default Archive Manager (File Roller) is very versatile, and can use various command-line archive utilities as plugins.  Install the p7zip-full package to enable support for a number of other archive types, including 7z and rar.

If you need more features than Archive Manager provides, you can look at those command-line utilities it uses.  7z (provided by the p7zip-full package, which is installed when you install the p7zip-rar package) can handle zip, cab, rar, arj, gzip, bzip2, tar, rpm, iso, and deb archives.  You could also look at the commands zip, unzip, tar, rar, and unrar.

---

### Post by accooper on 2009-03-20
OK, I have installed 7zip through the add/remove menu.  But I can't find it to run it on my computer.  How do I find it?

Andrew

---

### Post by snova on 2009-03-20
> **accooper said:**
> OK, I have installed 7zip through the add/remove menu.  But I can't find it to run it on my computer.  How do I find it?

It is a command line program.

```
7z --help
```

---

### Post by mb_webguy on 2009-03-20
File Roller (which you can find under Applications->Accessories->Archive Manager) uses the command-line application 7z as a plugin.  You don't have to know how to run the 7z command-line application in order to use it.  Just use Archive Manager to open or create zip files and other archives.

---

### Post by accooper on 2009-03-21
Thanks, Another problem solved.

Andrew

---


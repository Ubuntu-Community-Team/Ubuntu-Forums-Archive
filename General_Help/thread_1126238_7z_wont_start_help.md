---
title: "7z wont start help"
date: 2009-04-15
forum: General Help
---

### Post by GosthShadow on 2009-04-15
my 7z wont start. I cant see him or run in terminal. cant extract rar files (already tried uninstall/install process) help

---

### Post by zvacet on 2009-04-15
In terminal type

```
sudo apt-get install p7zip p7zip-full p7zip-rar
```

When packages are installed then just rigt click on rar package and select **extract here**.

---

### Post by mb_webguy on 2009-04-15
The Linux version of 7z is not a full GUI application like the Windows version, but a command-line application that can be used as a plugin by various other GUI archive managers, like Ubuntu's default Archive Manager (File Roller).  You can also use it from the terminal.  Type "7z --help" or "man 7z" for more options.

---

### Post by GosthShadow on 2009-04-16
i tried to extract rar file/s with ubuntu default archive manger it says "Could not open "Headhunterz_vs__Wildstylez_-_Project_1.rar"

Archive type not supported."

help

---

### Post by mb_webguy on 2009-04-16
Have you installed either the unrar or p7zip-rar packages?

---

### Post by GosthShadow on 2009-04-17
yes i did install :(

---

### Post by Bachstelze on 2009-04-17
Does it work from the command-line?

```
unrar x filename.rar
```

---


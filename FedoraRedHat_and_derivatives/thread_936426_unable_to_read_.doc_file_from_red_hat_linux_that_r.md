---
title: "unable to read .doc file from red hat linux that retrieve through ftp service"
date: 2008-10-02
forum: Fedora/RedHat and derivatives
---

### Post by hirts_gal on 2008-10-02
i currently develop a web based ftp system and my problem is, if i create a .doc file in red hat linux 9.0 i can retrieve at windows using ftp service but when i open it, it will be empty although it is not. And if i create a .doc file in windows and put the file in linux then retrieve it again from linux using ftp service, the file will give me unreadable text when i try to open it. any one please help me

---

### Post by Antman on 2008-10-05
> **hirts_gal said:**
> i currently develop a web based ftp system and my problem is, if i create a .doc file in red hat linux 9.0 i can retrieve at windows using ftp service but when i open it, it will be empty although it is not. And if i create a .doc file in windows and put the file in linux then retrieve it again from linux using ftp service, the file will give me unreadable text when i try to open it. any one please help me
What application are you using on the linux box to open/create the .Doc files?

---

### Post by LaRoza on 2008-10-05
Can you save it in another format, like rtf?

---

### Post by hirts_gal on 2008-10-06
i use OpenOffice.org Writer 1.0 application to open and create the .doc file.Thanks LaRoza for your tips. i can retrieve .rtf file from linux but i have one question. How about .pdf file, .xls file and other image files? Do they have a specific format like .rtf because i also need to upload and retrieve those files in linux. i faced the problem for those files also.

---

### Post by Antman on 2008-10-06
> **hirts_gal said:**
> i use OpenOffice.org Writer 1.0 application to open and create the .doc file.Thanks LaRoza for your tips. i can retrieve .rtf file from linux but i have one question. How about .pdf file, .xls file and other image files? Do they have a specific format like .rtf because i also need to upload and retrieve those files in linux. i faced the problem for those files also.
If you need to open/create .doc and xls files and share with Windows machines running current versions of MS Office, you need to use a newer version of OpenOffice so that the file formats (.doc, .xls, etc) can be more compatible.

---


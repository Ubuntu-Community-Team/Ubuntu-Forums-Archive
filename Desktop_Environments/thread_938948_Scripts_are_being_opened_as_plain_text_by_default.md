---
title: "Scripts are being opened as plain text by default"
date: 2008-10-05
forum: Desktop Environments
---

### Post by Ryukenden on 2008-10-05
Scripts are being opened as plain text by default in Xubuntu 8.04. When i click on a script, it opens OpenOffice.org. When i view the properties of a script, it says it's a plain text document.
How do i fix this?

---

### Post by mali2297 on 2008-10-05
> **Ryukenden said:**
> Scripts are being opened as plain text by default in Xubuntu 8.04. When i click on a script, it opens OpenOffice.org. When i view the properties of a script, it says it's a plain text document.
How do i fix this?

Are they executable? 

Right-click on the file icon, go to Properties -> Permissions and check that *Allow this file to run as program* is enabled.

---

### Post by Ryukenden on 2008-10-05
The Permissions page does not show an option to allow the file to run as program, but i can run the script in a terminal.

---

### Post by mali2297 on 2008-10-05
> **Ryukenden said:**
> The Permissions page does not show an option to allow the file to run as program, but i can run the script in a terminal.
But are they executable? 

In the terminal, check
```

ls -l yourscript.sh

```
You should see something like -rwxr-xr-x. Otherwise make it executable with the command
```

chmod -v +x yourscript.sh

```

---

### Post by Ryukenden on 2008-10-05
gabriel@52X:/media/Gabriel/Os meus documentos/Ficheiros/Programas/wuala$ ls -la
total 204
drwxr-xr-x 4 gabriel gabriel   4096 2008-10-05 17:14 .
drwxr-xr-x 3 gabriel gabriel   4096 2008-10-05 19:57 ..
-rw-r--r-- 1 gabriel gabriel   1247 2008-10-05 19:44 HavelaarPrefs
-rw-r--r-- 1 gabriel gabriel 141123 2008-10-04 19:41 loader2.jar
drwxr-xr-x 4 gabriel gabriel   4096 2008-10-05 17:12 Local2
-rw-r--r-- 1 gabriel gabriel   1585 2008-10-05 17:13 Machine.dat
drwxr-xr-x 2 gabriel gabriel   4096 2008-10-05 20:23 Meta
-rw-r--r-- 1 gabriel gabriel  13788 2008-10-05 17:14 NodeTable.ctm
-rw-r--r-- 1 gabriel gabriel   4292 2008-10-04 19:45 Prefs0.db
-rw-r--r-- 1 gabriel gabriel    127 2008-10-04 19:45 Prefs.index
-rw-r--r-- 1 gabriel gabriel      0 2008-10-04 19:41 Prefs.lock
-rwxr-xr-x 1 gabriel gabriel    177 2008-10-04 19:41 wuala
-rwxr-xr-x 1 gabriel gabriel    183 2008-10-04 19:41 wualacmd

I can't run wuala from thunar. I opens OpenOffice.org

---

### Post by mali2297 on 2008-10-05
OK, seems strange. :-k

Looking at the path "/media/Gabriel/Os meus documentos/Ficheiros/Programas/wuala", is the directory on some other disk?

Perhaps you can try moving the wuala folder.

---

### Post by Ryukenden on 2008-10-05
It happens regardless of the location. It also affects wualacmd.

---


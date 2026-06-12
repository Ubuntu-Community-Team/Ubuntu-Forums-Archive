---
title: "mysterious launcher icon won't disappear"
date: 2015-02-16
forum: Desktop Environments
---

### Post by MissMonicaE on 2015-02-16
Hi y'all,

A while ago, my LibreOffice Writer launcher icon began malfunctioning--specifically, when I click on it, it launches GIMP. When I right-click it, it gives me three options: "New Document" (which does in fact open a new document in LibreOffice), "Spotify Linux Preview" (which opens GIMP), and "Lock to Launcher" (which does nothing). I've run
```
gsettings reset com.canonical.Unity.Launcher favorites
```
to no avail. Short of uninstalling all the programs involved or having my laptop exorcised, does anyone have any suggestions? I'm on Ubuntu 12.04, if that helps.

---

### Post by v3.xx on 2015-02-16
I do not run unity, but I know of some reset options.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity+12.04&sa=Search&cof=FORID:9)

[https://www.google.com/search?client=ubuntu&channel=fs&q=reset+unity+launcher+12.04&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=reset+unity+launcher+12.04&ie=utf-8&oe=utf-8)

---

### Post by deadflowr on 2015-02-16
Can you drag and drop that launcher into the trash can at the bottom?

---

### Post by coldraven on 2015-02-16
Your tags made me laugh, but if it was demonic Writer would open a doc titled "Last will and testament" :)

---

### Post by MissMonicaE on 2015-02-16
Dropping the icon into the trash can didn't work--it just jumped back to where it was. But
```
unity --reset-icons
```
did the trick. Thank you!

---


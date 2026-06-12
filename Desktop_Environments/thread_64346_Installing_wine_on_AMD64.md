---
title: "Installing wine on AMD64"
date: 2005-09-10
forum: Desktop Environments
---

### Post by apostlej on 2005-09-10
After mucking with installing wine (apt-get install wine had too many errors), I finally got wine to install.

Manually goto (using your fav browser): [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)

click the binary folder and d/l **wine_0.0.20050725-winehq-1_i386.deb** and **libwine_0.0.20050725-winehq-1_all.deb**

wherever you put these, navigate to that directory and type:
**sudo dpkg -i --force-all libwine_0.0.20050725-winehq-1_all.deb**
**sudo dpkg -i --force-all wine_0.0.20050725-winehq-1_i386.deb**

Now run your intended win32 app.

---

### Post by mlomker on 2005-09-10
Are you running the AMD64 bit version of Ubuntu or I386?  I wouldn't expect an I386 binary to run but, then again, I've never tried.

---


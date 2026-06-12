---
title: "msttcorefonts -- fail with apt"
date: 2005-12-07
forum: General Help
---

### Post by basketcase on 2005-12-07
Okay, I got easybreezy (automatrix NG) and selected the MS Fonts, I get a failed: connection timed out when trying to catch a mirror with sourceforge.  

Everytime I try and install an app with apt-get, it trys to grab thos packages again, always failing and never allowing any other packages to install.  

How can I stop it from trying to install msttcorefonts?  

I've already uninstalled easybreezy.  

Thanks!

---

### Post by Joe_CoT on 2005-12-07
the problem is that wget is set to use passive ftp by default
```
sudo gedit /etc/wgetrc
```

find the lines
```
#passive_ftp = off
passive_ftp = on
```

and change them to

```
passive_ftp = off
#passive_ftp = on
```

save and close. now do this

```
sudo apt-get install msttcorefonts
```

that *should* work

---

### Post by basketcase on 2005-12-07
[QUOTE=bobfnordman]the problem is that wget is set to use passive ftp by default
```
sudo gedit /etc/wgetrc
```

find the lines
```
#passive_ftp = off
passive_ftp = on
```

and change them to

```
passive_ftp = off
#passive_ftp = on
```

save and close. now do this

```
sudo apt-get install msttcorefonts
```

that *should* work[/QUOTE]
connection still times out

---

### Post by -DarkMind- on 2005-12-07
same problem here

the download and install of the .deb it's ok 

when start to downloads the fonts appear the time out

---

### Post by basketcase on 2005-12-08
Well after searching, I found the 5.04 Add-On CD from ubuntuguide and used that.  

It did change my repositories, but another search gave me a list, and I went back to 5.10 repositories.

---


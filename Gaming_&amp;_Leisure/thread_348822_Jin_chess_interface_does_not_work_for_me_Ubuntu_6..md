---
title: "Jin chess interface does not work for me Ubuntu 6.10"
date: 2007-01-29
forum: Gaming &amp; Leisure
---

### Post by timrichardson on 2007-01-29
I  installed Jin yesterday (so it is the latest version). Jin is a Java chess client for FICS. I have java version "1.5.0_08"
The jin screeen does not draw. I just get a blank screen. If I guess where the menus are and click, the menu I clicked is drawn. 
Is it perhaps not using the Sun jre? 

regards

Tim

---

### Post by SuperGnome on 2007-02-03
To find out type java -version in a terminal window. 
 
Anyway I had the same experience and resolved it by selecting a different look and feel in Jin -> Preferences -> User Interface ("Plastic" worked for me).

---

### Post by meng on 2007-02-03
Tim, you may be correct that the Sun java is installed but not the default. Look here for how to make it the default:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---


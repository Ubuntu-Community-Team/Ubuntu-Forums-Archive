---
title: "How to install Jabref 2.4.2 manually"
date: 2008-12-12
forum: General Help
---

### Post by wangjiajun on 2008-12-12
Dear all,

I am using Jabref 2.3 in my Hardy. 

However, latest verison 2.4.2 has the feature I need badly. Since ubuntu has not pack this version yet, I want to install manually. 

I can download source file from Jabref in SourceForge, but do not have instructions how to install the jars. If you happen to know, please let me know. 

Thanks!

---

### Post by Partyboi2 on 2008-12-13
If you have downloaded JabRef-2.4.2-src.tar.bz2 ([http://sourceforge.net/project/showfiles.php?group_id=92314&package_id=97632&release_id=637373](http://sourceforge.net/project/showfiles.php?group_id=92314&package_id=97632&release_id=637373)) say for example to your Desktop you would need to open a terminal (Applications>Accessories>Terminal) and change to the Desktop directory
```
cd ~/Desktop
``` then extract the tar.bz2 file
```
tar xvjf JabRef-2.4.2-src.tar.bz2 
```then change into the newly created directory
```
cd jabref-2.4.2/
```then  you can build and run jabref by typing
```
ant run
``` If you do not have ant installed you can install it by
```
sudo apt-get install ant
```If you want to compile the program then type
```
ant jars
```then to run the program
```
 java -jar /home/username/Desktop/jabref-2.4.2/build/lib/JabRef-2.4.2.jar
```**Change username to your actually username.

---


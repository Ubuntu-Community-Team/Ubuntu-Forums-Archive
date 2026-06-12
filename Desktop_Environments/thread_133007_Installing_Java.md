---
title: "Installing Java"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Enforcer on 2006-02-19
Srry for flame posting on this, but i really, really, really need to get this working.

i used this wiki page here : [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) 

and the flash worked but java didnt

i followed the tut changing the paths from this

```
sudo bash

chmod 777 ./jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

./jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/local/java32

cp -r -p ./jre1.5.0_06/* /usr/local/java32

cd /usr/local/firefox32/plugins/

ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

to this

```
sudo bash

chmod 777 ~/Desktop/jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

~/Desktop/jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/lib/java

cp -r -p ./jre1.5.0_06/* /usr/lib/java

cd /usr/lib/mozilla-firefox/plugins/

ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

now the last line cmd there the 'ln -s blah blah blah' says the file already exists. What I tried was cd-ing to the usr/lib/mozilla/ and using this ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./  to create or copy (not sure what this does if anyone wants to clerify) and i guess that worked but Java still inst working. So if anyone could help that b great!

---

### Post by Mr Frosti on 2006-02-19
If the last step says that the file already exists, the symbolic link will not be created. You can see what is going on in that directory by doing the following:

Change to the directory:
```
cd /usr/lib/mozilla-firefox/plugins/
```

View the path of the symbolic link:
```
ls -l
```

You should see something like "libjavaplugin_oji.so -> /path/to/java_plugin

If this link is broken, it will be red with a black background. If it is broken, try removing it, then doing the "ln -s" step again after the removal.

---

### Post by Enforcer on 2006-02-19
k, i got that fixed.

i RM the file and then ```
ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./ 
``` so now its Light blue which im assuming is good?

That cant b all tho cause its still not working

---

### Post by Perfect Storm on 2006-02-19
What does it say when you run **java -version** in the terminal?

---

### Post by Enforcer on 2006-02-19
```
root@ubuntu:~# java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
root@ubuntu:~#

```

---

### Post by Perfect Storm on 2006-02-19
Try with:

```
sudo update-alternatives --config java
```

---

### Post by Enforcer on 2006-02-19
they are both the same

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

```

I selected both and they are the same versions

---

### Post by Perfect Storm on 2006-02-19
Perhaps this howto can help you a bit: [http://ubuntuforums.org/showthread.php?t=90919&highlight=java](http://ubuntuforums.org/showthread.php?t=90919&highlight=java)

---

### Post by Enforcer on 2006-02-19
Yay it works, Thank you so much you saved so much time for me!

---

### Post by Perfect Storm on 2006-02-19
My pleasure ^^

---


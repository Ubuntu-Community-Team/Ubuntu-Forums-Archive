---
title: "ArtOfIllusion"
date: 2009-06-04
forum: General Help
---

### Post by gishaust on 2009-06-04
Does anyone know what this error means? 

Unable to access jarfile ArtOfIllusion.jar

The jar file is on the desktop in the instructions it says all I have to do is extract the zip file. Then move to the file through the terminal and then  sudo java -Xmx1000m -jar ArtOfIllusion.jar but all I get is the error above. 

The how to is here.

[http://www.housepixels.com/aoimanual/installation.html](http://www.housepixels.com/aoimanual/installation.html)

---

### Post by Chronon on 2009-06-05
Maybe try:
```
sudo java -Xmx1000m -jar ./ArtOfIllusion.jar
```from the directory that it's saved in.

---

### Post by Megrimn on 2009-06-05
ok, here's where it went wrong:

once you extract the folder from the .zip file, cd to that folder in terminal.

then, in terminal, execute the file "aoisetup.sh"

```
sh ./aoisetup.sh
```

terminal will then execute that pesky .jar file and start the installer.  

Happy Art-Of-Illusion-ing.  Now I get to figure out exactly what this program is for...:D

---

### Post by gishaust on 2009-06-05
It work great thanks.

A tip **don't** use install it using sudo sh ./aoisetup.sh it will not run
To get it to run you have to goto the folder that was installed through the terminal and type

sh ./aoi.sh

---


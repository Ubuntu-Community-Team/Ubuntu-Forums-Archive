---
title: "copying all files in one folder to another..."
date: 2006-06-25
forum: Desktop Environments
---

### Post by cwncool on 2006-06-25
I have a folder on my desktop called "essential". I need to copy all of it to "usr/lib/win32". Once in the "essential" folder of the desktop in the terminal I type this..
```

cwncool@cwncool-desktop:~/Desktop/essential$ cp /usr/lib/win32

```
It gives me the error
```

cp: missing destination file operand after `/usr/lib/win32'
Try `cp --help' for more information.

```
Why is it giving me that error and not copying the files...? How do I copy all files from the "essential" folder into the folder at "usr/lib/win32"? Thanx!

---

### Post by aysiu on 2006-06-25
Try this: ```
sudo cp -R ~/Desktop/essential /usr/lib/win32
```

---

### Post by cwncool on 2006-06-25
that copies the whole "essential" folder to "win32". I just want to copy the contents of "essential" into "win32"... How would I do that? and how do I now delete the "essential" folder from "win32" before I copy the contents to it? (srry 4 all the questions)

EDIT: N/M. I figured it out... I just added "/*" after the copy thanx for all your help aysiu! You're a linux pro! lol. thanx!

---

### Post by ardchoille on 2006-06-25
[QUOTE=cwncool]that copies the whole "essential" folder to "win32". I just want to copy the contents of "essential" into "win32"... How would I do that? and how do I now delete the "essential" folder from "win32" before I copy the contents to it? (srry 4 all the questions)[/QUOTE]
Try this
```

sudo cp -R ~/Desktop/essential/* /usr/lib/win32

```
To delete the "essential" folder from "win32", do:
```

sudo rm -rf /usr/lib/win32/essential

```

---

### Post by aysiu on 2006-06-25
```
sudo rm -rf /usr/lib/win32/essential
sudo cp -R ~/Desktop/essential/* /usr/lib/win32
```

---


---
title: "permission problem"
date: 2009-04-18
forum: General Help
---

### Post by fuhayer on 2009-04-18
i have just installed 9.04 jaunty and need to put a file into usr/local/bin but could not succeeded. whatever i tried did not work. cannot control this folder with chmod command. 

how can i put file in this folder ?

---

### Post by _Purple_ on 2009-04-18
You need admin privilege to write files in that folder. Did you use sudo?

---

### Post by fuhayer on 2009-04-18
> **_Purple_ said:**
> You need admin privilege to write files in that folder. Did you use sudo?

sudo did not work also. i am newbie but also checked commands and applied with failure. what is full sudo command to aloow put file in that folder ?

---

### Post by atomizer on 2009-04-18
if the file is in /home/yourusername

```
sudo cp /home/yourusername/file  /usr/local/bin
```



or to start nautilus with admin privileges (so you can copy/paste with a few mouseclicks)

```
gksudo nautilus
```

---

### Post by _Purple_ on 2009-04-18
It is not a good idea to change the permission of that folder. You can move any file to that folder using the following command:
```
sudo mv /*path_to_file*/*filename* /usr/local/bin/*filename*
```

Replace the **filename** with your filename and replace the **path_to_file** with the actual path of the file.

Similarly, you can do this using GUI using copy and paste but be careful as you will have the admin privilege while in the GUI. The command to enter the GUI is
```
gksu nautilus
```


edit:atomizer already posted the solution :)

---

### Post by fuhayer on 2009-04-18
> **_Purple_ said:**
> It is not a good idea to change the permission of that folder. You can move any file to that folder using the following command:
```
sudo mv /*path_to_file*/*filename* /usr/local/bin/*filename*
```

Replace the **filename** with your filename and replace the **path_to_file** with the actual path of the file.

Similarly, you can do this using GUI using copy and paste but be careful as you will have the admin privilege while in the GUI. The command to enter the GUI is
```
gksu nautilus
```


edit:atomizer already posted the solution :)

OMG. sudo cp and others worked :) many many thanks.

is there a FTP app for graphical use ? i found ftpcube but now ay to install it. any other alternatives ?

---

### Post by _Purple_ on 2009-04-18
Glad to hear that it worked for you. :)
I do not use any graphical ftp client but you might find [this thread](http://ubuntuforums.org/showthread.php?t=393867) useful.

---

### Post by fuhayer on 2009-04-18
> **_Purple_ said:**
> Glad to hear that it worked for you. :)
I do not use any graphical ftp client but you might find [this thread](http://ubuntuforums.org/showthread.php?t=393867) useful.

thank you :)

---


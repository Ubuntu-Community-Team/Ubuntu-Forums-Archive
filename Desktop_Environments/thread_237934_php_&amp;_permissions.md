---
title: "php &amp; permissions"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Illusionistx on 2006-08-16
when i want to create a new file, i usually don't like to have to open a terminal to do it, so i navigate to the folder, right click and create an empty document. or if i already ahve an editor open, just start a new one there and save it into my /var/www folder when i'm done. however when i open my browser and try to view it i get the
> ...failed to open stream: Permission denied...
warnings. i can fix this by doing
```

sudo chown -R www-data:www-data /var/www
```
but i hate having to dot hat everytime. 

is there a way that i can make it either not require those permissions or change them automatically or something?

---

### Post by murataht on 2006-08-17
if you start the editor (gedit), start it with the www-data user. then the documents should belong to this user and group. 
something like 
```
sudo su www-data
gedit
```
should bring up gedit with www-data user.

---

### Post by Illusionistx on 2006-08-17
thanks. not exactly what i was hoping for, but it works!

---

### Post by lupine_nickt on 2006-08-17
You can right-click on the file, go to Properties-*Permissions, and edit the owner and group it belongs to from there.

You could also create a shell script - for instance:-

```

#!/bin/bash
chown www-data:www-data $1

```

Once you've created your file, just drag it onto the shell script, which should execute with the file name as "$1". It shouldn't need root permissions, but if it does just use gksudo or kdesu at the beginning of the second line to get it tro prompt you for a password.

xF,

...Nick

---

### Post by Illusionistx on 2006-08-17
yeah i made a nautilus script similar to that and it seems to work well.

---


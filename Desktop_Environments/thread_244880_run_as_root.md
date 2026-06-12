---
title: "run as root"
date: 2006-08-27
forum: Desktop Environments
---

### Post by gary800 on 2006-08-27
I've got a couple of scripts that mount disk and alter the wireless connection.

The scripts can only be execute as root.

Is it possiable to give the normal user root rights when executing the script.

I read a little bit about the "s" tag in chmod but have not figured out how to make it work. Any examples would be great.

Thanks.

---

### Post by statue on 2006-08-27
sudo ./scriptname
be sure to be in the directory the script is or put the path before the filename

---

### Post by gary800 on 2006-08-27
Fair comment.

I like to have an icon on the desktop that can be clicked without having to run from terminal or entering the root password. If this is possible.

---

### Post by statue on 2006-08-27
could make a simple script to execute the above command and just put it on the desktop...not sure about the sudo though...does anyone know if you can put a sudo command into a shell script? i suppose the password would have to be in there somewhere

---

### Post by aysiu on 2006-08-27
You can put a *sudo* command in a shell script, but you'll be prompted for your password.

---

### Post by peabody on 2006-08-27
> **gary800 said:**
> Fair comment.

I like to have an icon on the desktop that can be clicked without having to run from terminal or entering the root password. If this is possible.

Create another script that runs the script via gksu:

```

#!/bin/sh

gksu ./script_file

```

---


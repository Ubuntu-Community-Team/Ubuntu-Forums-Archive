---
title: "log file help"
date: 2009-04-29
forum: General Help
---

### Post by brandon88tube on 2009-04-29
When I bring up the log file viewer I keeping getting an error at the top for /var/log/btmp saying "The file is not a regular file or is not a text file." This has never happened before when I would open up the log file viewer. Can someone help me out with this?

---

### Post by sisco311 on 2009-04-29
btmp is used to record bad logins. 

what's the output of:
```
ls -alh /var/log/btmp
```

are you using ssh?

---

### Post by brandon88tube on 2009-04-29
The output is
```
-rw-rw-r-- 1 root utmp 384 2009-04-29 15:05 /var/log/btmp
```
I don't think I'm using ssh, though it seems to be installed.

---

### Post by brandon88tube on 2009-05-01
Anyone?

---

### Post by brandon88tube on 2009-05-02
Still nothing?

---

### Post by gFallon on 2009-05-02
I had the same problem myself. What I ended up doing should work for you.
Open  a terminal session and move "btmp"  to btmp.bak like this
           sudo mv /var/log/btmp /var/log/btmp.bak
now copy a "dummy" file in its place 
           sudo cp -p /var/log/boot /var/log/btmp
now open the loge file viewer and select the btmp file on the left side of the application window. wthe it hilighted either select File -> Close or Ctrl + W. this will remove btmp from the list of logs bieng monitored by the log viewer. Now go back to the console and replace the origonal btmp file with
          sudo cp -p /var/log/btmp.bak /var/log/btmp
Cheers

---

### Post by brandon88tube on 2009-05-02
After I do that, when I try to add btmp back to the log file viewer I get the error "You don't have enough permissions to read the file."

---

### Post by hscku on 2009-05-11
> **gFallon said:**
> I had the same problem myself. What I ended up doing should work for you.
Open  a terminal session and move "btmp"  to btmp.bak like this
           sudo mv /var/log/btmp /var/log/btmp.bak
now copy a "dummy" file in its place 
           sudo cp -p /var/log/boot /var/log/btmp
now open the loge file viewer and select the btmp file on the left side of the application window. wthe it hilighted either select File -> Close or Ctrl + W. this will remove btmp from the list of logs bieng monitored by the log viewer. Now go back to the console and replace the origonal btmp file with
          sudo cp -p /var/log/btmp.bak /var/log/btmp
Cheers


Thanks, it worked for me

---

### Post by rudy.b on 2009-05-11
> **brandon88tube said:**
> After I do that, when I try to add btmp back to the log file viewer I get the error "You don't have enough permissions to read the file."

I don't think you can use the log file viewer to view the btmp log file since it's not a text file.  The only way I know of to view the contents of this file in plain text is to use the following terminal command:
```
$ sudo lastb
```

---

### Post by lelamal on 2009-11-07
> **gFallon said:**
> I had the same problem myself. What I ended up doing should work for you.
Open  a terminal session and move "btmp"  to btmp.bak like this
           sudo mv /var/log/btmp /var/log/btmp.bak
now copy a "dummy" file in its place 
           sudo cp -p /var/log/boot /var/log/btmp
now open the loge file viewer and select the btmp file on the left side of the application window. wthe it hilighted either select File -> Close or Ctrl + W. this will remove btmp from the list of logs bieng monitored by the log viewer. Now go back to the console and replace the origonal btmp file with
          sudo cp -p /var/log/btmp.bak /var/log/btmp
Cheers

Thanks, this worked for me too!

---

### Post by Squideshi on 2010-05-02
> **brandon88tube said:**
> After I do that, when I try to add btmp back to the log file viewer I get the error "You don't have enough permissions to read the file."

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---


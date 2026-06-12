---
title: "Problem creating symlinks in xubuntu"
date: 2012-09-25
forum: Desktop Environments
---

### Post by daKoolaid on 2012-09-25
I'm used to nautilus in Mint where you simply right click on a file or folder and do Make Link. It creates a link in that same folder which you can then put anywhere you like.

Xubuntu doesn't come with this and adding a custom action into Thunar for 
"ln -s %f Link to %n"
doesn't create anything.

If I try something like
"ln -s /file to copy /folder the file is in"
then terminal says the file already exists, which it does. I want a link to the file that already exists.

The ln man page didn't clear anything up, wasn't expecting this to be so difficult. Any tips for a noob?

---

### Post by jerrrys on 2012-09-25
Maybe this will make sense to you

[https://help.ubuntu.com/community/ThunarCustomActions#Create_Symlink](https://help.ubuntu.com/community/ThunarCustomActions#Create_Symlink)

Found that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=creating+symlinks+in+thunar&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=creating+symlinks+in+thunar&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by steeldriver on 2012-09-25
This seemed to work for me:

In Thunar --> Configure custom actions... (+)

```
Name: Create symlink here
Description: Create symlink of file (in local dir)
Command: /bin/ln -s %f "Link to %n"
``````
$ ls -l | grep myfile
lrwxrwxrwx  1 steeldriver steeldriver      20 Sep 25 18:26 Link to 'myfile' -> /home/steeldriver/myfile
-rw-r--r--  1 steeldriver steeldriver      80 Aug 19 14:41 myfile
```If you want it to overwrite an existing file you will need to add '-f' (force) to the ln command, I think

---

### Post by daKoolaid on 2012-09-25
> **steeldriver said:**
> This seemed to work for me:

In Thunar --> Configure custom actions... (+)

```
Name: Create symlink here
Description: Create symlink of file (in local dir)
Command: /bin/ln -s %f "Link to %n"
``````
$ ls -l | grep myfile
lrwxrwxrwx  1 steeldriver steeldriver      20 Sep 25 18:26 Link to 'myfile' -> /home/steeldriver/myfile
-rw-r--r--  1 steeldriver steeldriver      80 Aug 19 14:41 myfile
```If you want it to overwrite an existing file you will need to add '-f' (force) to the ln command, I think

THANK YOU!! That did exactly what I was looking for.

---

### Post by LewisTM on 2012-09-25
FYI Thunar DOES have a built-in way of creating symlinks. In fact, it has two:

1) Select your item(s) then go to Edit->Make Link
2) Select your item(s), then drag and drop while holding Ctrl-Shift

Cheers!

---


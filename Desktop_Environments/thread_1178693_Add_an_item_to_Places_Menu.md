---
title: "Add an item to Places Menu"
date: 2009-06-04
forum: Desktop Environments
---

### Post by conradin on 2009-06-04
Hi all,
I am using Ubuntu 8.10. I want to add a folder to the Places Menu and call it "DownLoads". (Like Fedora 10 has)
I know how to use the command prompt pretty well. When I make a Directory, such as ~# mkdir /home/user/DownLoads of course the folder is made, but it is not shown in the "Places Menu".

Any ideas how to place custom folders in the Places Menu?

---

### Post by _Purple_ on 2009-06-04
You can use the bookmark to add directories under places.

---

### Post by keplerspeed on 2009-06-04
Open nautilus, by going to places>home folder. Now navigate to the downloads folder, and go to bookmarks>add bookmark. The downloads directory should be added to the left pane. It will also be added to the places menu.

---

### Post by conradin on 2009-06-04
YAY!!! Much Thanks!!

---

### Post by savedr on 2009-08-04
I found this EXTREMELY useful, so thanks very much from me as well! :D

---

### Post by doris orange on 2010-03-09
awesome! so simple, yet so profound.

---

### Post by robfish on 2010-05-18
Thanks from me too.
I had tried editing .config/user-dirs.dirs but it did not work.

---

### Post by robfish on 2010-05-18
Next question --
How do I have the "Places" icons use the same icons as the folder?

When I change the default location for Pictures for example, the icon reverts to the standard folder icon. If I change it back to the Pictures folder in the home directory it shows a picture icon.

---

### Post by jringoot on 2010-09-27
Hi all

I would like do change these shortcuts system wide:
Let them point to resource dirs for users like:
```

/mnt/archive/$USER
/mnt/filer/$USER
/mnt/filer/`id -gn $USER`
/mnt/filer/public

```

Actually I would like to do it the most clean way possible, like by configuring everything in /etc/skel. Or in a general conf file.

I noticed, like many of you probably, that a lot more  than "/etc/skel" is created in ones homedir as soon as you log on in the GUI.
Anyone who has some guidance on how this is done, and how it can be influenced?

Thanks for your input,

Joost

---


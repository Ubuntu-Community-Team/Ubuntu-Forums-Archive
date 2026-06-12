---
title: "Application installation"
date: 2009-05-06
forum: General Help
---

### Post by polskimoose on 2009-05-06
say i'm trying to download an application and i get a .tar-2.bz2 file

what do i do with it?

---

### Post by taurus on 2009-05-06
You would open a terminal, change to the directory where you've saved that file, and unpackage it.

```
cd name_of_the_directory
tar xvjf filename.tar.bz2
```

What are you trying to install anyway?

---

### Post by polskimoose on 2009-05-06
and if i saved it to the desktop what would i type?

---

### Post by ikacer on 2009-05-06
cant you just right click and select "extract here"?

---

### Post by ikacer on 2009-05-06
if you want to do it in the terminal you would type:

```

cd ~/Desktop
tar xvjf filename.tar.bz2

```

the cd is the change directory command
the ~ goes to your /home/user_name directory

edit: you may want to try this really useful feature: [http://ubuntuforums.org/showthread.php?t=345153]("http://ubuntuforums.org/showthread.php?t=345153")

---

### Post by ikacer on 2009-05-06
sorry about 3 posts in a row, but it just occurred to be that if the application is a .tar.bz2 its probably the source code so you may need to compile the application. here is a link on how to do that: [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")
even if it looks complicated, its really usually pretty simple to compile applications.

best of luck!

---

### Post by polskimoose on 2009-05-06
nah i got it to work without that last post, thanks though!

---


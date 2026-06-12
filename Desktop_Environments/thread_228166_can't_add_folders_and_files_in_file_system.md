---
title: "can't add folders and files in file system?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by awong on 2006-08-02
I just had to reinstall 6.06 on my pc and now I cant seem to be able to copy and add files to the file system.  I checked on properties and it says I am not the owner of it so I cannot change it.  How would I fix this.  I only made one user name too.

---

### Post by ironfistchamp on 2006-08-02
Sounds like it is because you do not have the privledges. You can only write to directories other than your home folder as root. From the terminal you could type

```

sudo cp <file to copy> <place to copy too>

```

Or from the terminal type

```

gksu nautilus

```

To get root privledges in nautilus. Then you can copy your files. Best close the window after you have done the copying as you may edit/delete something you didn't mean to as root.

Hope this helps

Ironfistchamp

---

### Post by llamakc on 2006-08-02
If you're talking about files in your /home directory you can change the ownership of the files to your admin user you created at install.

Where are the files located you're talking about (in the filesystem)?

---

### Post by awong on 2006-08-02
thanks the gksu nautilus worked.  

I guess in my previous installation I may have gotten confused with home folder and the file system and where I was going to put a folder for my ndiswrapper drivers.

---

### Post by ironfistchamp on 2006-08-03
Glad its working for you now :D

---


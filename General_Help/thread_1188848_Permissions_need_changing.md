---
title: "Permissions need changing"
date: 2009-06-16
forum: General Help
---

### Post by 73ckn797 on 2009-06-16
I had to reload 9.04. Prior to doing that I backed up my /home to another drive. I no longer have permissions to those files. In particular the /home/myname/Documents. I could care less about all of the other /home files but my documents need access. I can go individually through them and change permissions using ```
sudo nautilus
``` That is a lot of work. I would like to change them all so I can have full access again.

Is this basically the correct command to use?
```
sudo chmod 777 /home/mydir
```

Reading the help pages leads me to this conclusion. I need to spend more time there but this week is hectic and I need my document access back.

Isn't there a command switch (-R = recursive) to change permissions of all files within the document folder?

What about getting permissions to other HDD's (2 others)?

---

### Post by nothingspecial on 2009-06-16
Yes you need the -R switch

If you use gksudo nautilus you can click right click choose properties. There is an option to change permissions to all files and folders.

something like that, anyway. 

Sorry not using gnome at the mo.

---

### Post by 73ckn797 on 2009-06-16
> **nothingspecial said:**
> Yes you need the -R switch

If you use gksudo nautilus you can click right click choose properties. There is an option to change permissions to all files and folders.

something like that, anyway. 

Sorry not using gnome at the mo.


That is what I have been doing but it is a slow process.

---

### Post by ActiveFrost on 2009-06-16
```
sudo chmod -R 777 /home/mydir
```

---

### Post by nothingspecial on 2009-06-16
No, if you right click on the directory there is an option to apply those permissions to everything in that directory.

---

### Post by nothingspecial on 2009-06-16
Thinking about it as he steps outside for a smoke........

The correct permissions for stuff in your home directory should be 755 unless you want anybody to be able to mess with them.

However this is linux so you do what you want.

---

### Post by ActiveFrost on 2009-06-16
In that case, why not to try chown ? :p

---


---
title: "Make the loader go away!"
date: 2008-03-28
forum: Desktop Environments
---

### Post by larrythecameraguy on 2008-03-28
I installed KUBUNTO to see if I could use it to work on my photos..

All is fine, BUT, when I boot up I get a "Loader" screen that lets me choose which operating system to load..

I would rather not have that loader, I would rather have the system boot from the drive selected in the CMOS setup, but it wont... no matter what drive I try to boot from, I always get the loader.

Larry

---

### Post by kellemes on 2008-03-28
You can [hide your bootmenu.]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

---

### Post by larrythecameraguy on 2008-03-28
Thanks for the attempt to help..

Right now that server is down or somehow the page isnt loading...

I'll try it tomorrow.

Thanks again

Larry

---

### Post by larrythecameraguy on 2008-03-30
HHHHHEEEEELLLLLPPPP!


I still cant get to the page that was posted and Im going NUTS trying to lose this LOADER PAGE...



Larry

---

### Post by YoG%*@ on 2008-03-30
hi, 

> **larrythecameraguy said:**
> HHHHHEEEEELLLLLPPPP!

I still cant get to the page that was posted and Im going NUTS trying to lose this LOADER PAGE...

Larry

hm, page seems to load fine, but there you go ;)

edit your /boot/grub/menu.lst file and activate hiddenmenu: 

```

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu
 
```


you might also want to set the timeout value to a small number: 

```

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout      3
 
```

hth, 
mux

---

### Post by jhdumer on 2008-03-30
This is good info, but how do get to edit the boot.lst?

---

### Post by kellemes on 2008-03-30
> **jhdumer said:**
> This is good info, but how do get to edit the boot.lst?

from terminal..
Create a backup first like so..
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
And edit the file..
```
gksudo gedit /boot/grub/menu.lst
```

---


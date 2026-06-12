---
title: "Xfce: accessing other LAN computers"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Granduke on 2005-12-11
I can't find how to access the other computers on my LAN, such as GNOME's Menu 'Places' - 'Network'.

landefor suggested creating a panel launcher: nautilus --no-desktop network

However this brings up an error window: "Couldn't find "/home/granduke/network".

---

### Post by soulestream on 2005-12-11
man smbmount
man mount 
man smbclient


im assuming you mean accessing shared files

soule

---

### Post by Iandefor on 2005-12-11
[quote=Granduke] landefor suggested creating a panel launcher: nautilus --no-desktop network

However this brings up an error window: "Couldn't find "/home/granduke/network".[/quote]
 Whoops. I had a brainfart of the worst kind- a seemingly minor omission. What I meant was:
```

nautilus --no-desktop network:
``` and just to make it absolutely clear, that colon *must* be at the end of "network"; otherwise, it just looks for a folder in your home directory called "network"

---

### Post by Granduke on 2005-12-11
Thanks landefor,
                         
That missing colon was the problem.

---

### Post by Iandefor on 2005-12-11
Yeah, I smacked my forehead when I realized I left it out.

---

### Post by karthik085 on 2005-12-19
Just to let you know, you can use xfsamba4, an samba front end .

---


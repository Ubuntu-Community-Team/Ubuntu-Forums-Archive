---
title: "[SOLVED] how to delete a program"
date: 2008-12-05
forum: General Help
---

### Post by banana jama on 2008-12-05
this is a little wierd to ask. i downloaded lime wire off of their website and i realized that i sucks. i want to delete it but when i go to add/remove under applications it doesn't show up. how do i delete limewire out side of the add/remove application.

---

### Post by unutbu on 2008-12-05
Was the package called LimeWireLinux.deb?
If so, open a terminal (Applications>Accessories>Terminal) and type
```

sudo dpkg -r LimeWireLinux
```

---

### Post by binbash on 2008-12-05
also if you cant find the exact name :

sudo dpkg -l | grep Similarnamehere

---

### Post by banana jama on 2008-12-05
i don't know the exact name so i should use this command
sudo dpkg -l | grep LimeWireLinux     

because i did and nothing happen it is still there.

---

### Post by ibutho on 2008-12-05
Try something like
```
sudo dpkg -l | grep -i limewire
```

---

### Post by banana jama on 2008-12-05
this is what terminal's output was 
> akeem@akeem-laptop:~$ sudo dpkg -l | grep -i limewire
ii  limewire-basic                            4.18.8-1                              LimeWire is a p2p filesharing program that o
akeem@akeem-laptop:~$ 
 
 is lime wire basic the name and if it is should i use that as a replacement unutbu's command. also thanks for the quick replys.

---

### Post by banana jama on 2008-12-05
YES!!! it worked for future refernce anyone who wants to delete limewire 4.18 use the following code:
       > sudo dpkg -r limewire-basic 

thanks everyone for the help.

---

### Post by Yellow Pasque on 2008-12-05
Are you using gtk-gnutella as an alternative?

---

### Post by banana jama on 2008-12-05
whats gtk-gnutella

---

### Post by Yellow Pasque on 2008-12-06
> **banana jama said:**
> whats gtk-gnutella
It's the Linux gnutella client (specifically, one with a GNOME interface.) Limewire is also a gnutella client.

---


---
title: "How do I find what model my graphics card is?"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Green9090 on 2009-01-15
I have an Nvidia card which works fine in Ubuntu, but I need to get the drivers to get it running on my new Windows XP partition. Is there any way to get Ubuntu to tell me what the exact model of my graphics card is?

---

### Post by aesis05401 on 2009-01-15
> **Green9090 said:**
> ... Is there any way to get Ubuntu to tell me what the exact model of my graphics card is?

```
 
sudo lshw > hardware.011509
nano hardware.011509

```

The first command sends the output of lshw (list hardware) to a file you are naming 'hardware.011509' (that is the date after the dot.. so you can keep it straight at a glance from other hardware snapshots).

The second command opens the nano text editor to view the newly created file.  Once inside of nano, hit CTRL W to pull up the find routine, and search for your network device name (usualy eth0 for wired, wlan0 for wireless).

You will see all sorts of info including product (model), vendor, etc...

---

### Post by Green9090 on 2009-01-15
Thank you so much!

---

### Post by capitales7 on 2009-01-22
What a useful command... cheers.

---

### Post by Geneorama on 2013-04-15
Some other commands that I use (substitute your card name for nvidia)

Find out which driver your card is using:
```
lsmod
lsmod | grep nvidia
```

Find out if you've installed drivers for nvidia
```
dpkg --get-selections | grep nvidia
```

I forget what this is supposed to do... for me it only shows errors
```
glxinfo | grep OpenGL
```

---

### Post by howefield on 2013-04-15
Old thread closed.

---

